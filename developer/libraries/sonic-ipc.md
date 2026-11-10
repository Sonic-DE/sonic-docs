---
title: Sonic IPC
description: Let SonicDE components talk to each other over Unix domain sockets with framed, versioned messages, without a message bus.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-ipc (README.md, src/server.h, src/client.h, src/connection.h, src/frame.h), sonic-desktop-interface (applets/keyboardlayout/ipc/IpcProtocol.h), sonicde-builder (AGENTS.md); written from the code, not run"
---

# Sonic IPC

[Sonic IPC](/docs/api/sonicipc/sonicipc-index), in `sonic-frameworks-ipc` (`find_package(SonicIpc)`,
`Sonic::Ipc`), lets SonicDE components talk to each other directly, peer to peer, over Unix domain
sockets (`QLocalServer` and `QLocalSocket`). There's no message bus in between. It needs Qt Core and
Network and [Sonic Logging](sonic-logging.md).

## When to use it

SonicDE uses Sonic IPC for communication where both ends ship in SonicDE and nothing outside SonicDE
calls the interface. Examples already converted are the keyboard layout widget and the keyboard
service, the login manager's greeter, settings page and helper, and the screen locker and its unlock
screen.

[D-Bus](../dbus/introduction.md) stays where software outside SonicDE takes part, as client or server:
logind, NetworkManager, UPower, polkit, freedesktop.org interfaces such as notifications, MPRIS and
portals, and `org.kde.*` interfaces that upstream KDE applications call. When you're unsure whether
something outside SonicDE calls a D-Bus server, keep the server and move SonicDE's own clients to
Sonic IPC.

## Messages

Every message is one frame: a magic marker, a frame format version, your protocol version, a message
type (`quint32`), the payload length and a CRC-32 of the payload. The payload is whatever bytes you send;
SonicDE components write it with `QDataStream`.

- Damaged, oversized or foreign data is rejected, and the connection is closed. The payload size is
  checked from the header alone, before any payload is buffered. The limit is 16 MiB unless you pass
  another `maxPayload`.
- A peer that speaks a different protocol version gets a "version rejected" frame before the connection
  closes. Both sides report it with `versionRejected()`, and a client stops reconnecting.
- Frame type `0xFFFFFFFF` is reserved for the library.

Put the message types and the protocol version in one header shared by both ends, and raise the version
on any incompatible change. The keyboard layout widget's `IpcProtocol.h` in sonic-desktop-interface is a
complete example.

## A server

```cpp
#include <Sonic/Ipc/Connection>
#include <Sonic/Ipc/Server>

constexpr quint16 protocolVersion = 1;

auto *server = new Sonic::Ipc::Server(this);
if (!server->listen(Sonic::Ipc::Server::userSocketPath(QStringLiteral("my-service.sock")),
                    Sonic::Ipc::Server::Access::User, protocolVersion)) {
    sonicWarning() << "can't listen:" << server->errorString();
}
connect(server, &Sonic::Ipc::Server::newConnection, this, [](Sonic::Ipc::Connection *connection) {
    QObject::connect(connection, &Sonic::Ipc::Connection::frameReceived, connection,
                     [connection](quint32 type, const QByteArray &payload) {
                         connection->send(type, payload); // echo
                     });
});
```

- `Server::userSocketPath(fileName)` gives `<runtime directory>/<fileName>`, or a checked
  `/tmp/sonic-<uid>/` fallback when there's no runtime directory.
- `Access::User`, `Access::Group` or `Access::World` sets who may connect to the socket. Per-user
  services use `Access::User`.
- A live server's socket is never replaced: `listen()` fails while another server answers on the name,
  and only a stale socket file is removed.
- `broadcast(type, payload)` sends a frame to every connected client, for change notifications.
- A privileged server checks who is calling: `Connection::peerCredentials()` returns the uid, gid and pid
  of the connected process.

## A client

```cpp
#include <Sonic/Ipc/Client>

auto *client = new Sonic::Ipc::Client(protocolVersion, Sonic::Ipc::defaultMaxPayload, this);
client->setReconnectInterval(2000); // follow the server across restarts
connect(client, &Sonic::Ipc::Client::connected, this, [](Sonic::Ipc::Connection *connection) {
    connection->send(/*type*/ 1, {});
});
client->connectToServer(Sonic::Ipc::Server::userSocketPath(QStringLiteral("my-service.sock")));
```

`connectionFailed(reason)` and `versionRejected(serverVersion)` report problems, and `connection()`
returns the current connection.

Everything works through Qt's event loop: `frameReceived()` and `disconnected()`. In a thread without
an event loop, use `Connection::waitForFrame()` and `sendBlocking()`, or the blocking one-shot request:

```cpp
// On a worker thread: one request, one reply, within 5 s.
QString error;
const std::optional<Sonic::Ipc::Frame> reply =
    Sonic::Ipc::Client::request(path, /*type*/ 1, payload, protocolVersion, 5000, &error);
```

## Converting a D-Bus interface

When you move an internal-only D-Bus interface to Sonic IPC:

- Change both ends in the same change, and remove the D-Bus XML, adaptors and interface classes that
  only served it.
- Put the message types and a protocol version in one shared header, and send each message as one frame.
- Listen on `Server::userSocketPath("<name>.sock")` with `Access::User`. A privileged server checks the
  peer credentials of each connection.
- Add `sonicde/sonic-frameworks-ipc` to the package manifest's `depends` in sonicde-builder, link
  `Sonic::Ipc`, and test both ends.
- Raise the protocol version on any incompatible change. Say in the packager release notes if a restart
  is needed after upgrading, and in the package's `RELEASE-NOTES.md` if users will notice.
