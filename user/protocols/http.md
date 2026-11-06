---
title: http and https
description: Connect to web servers.
source_url: https://invent.kde.org/frameworks/kio/-/blob/master/docs/kioworker6/http/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io e3f55ceb (src/kioworkers/http); read from code, not clicked through"
---

# http and https

HTTP is the *H*yper*T*ext *T*ransfer *P*rotocol.

SonicDE applications use the http KIO worker to handle connections to HTTP servers, that is, web servers.

You can use the https KIO worker by giving an application a URL such as `https://www.example.org`.

https is http encapsulated in an SSL/TLS stream.

SSL is the Secure Sockets Layer protocol, a security protocol that provides communications privacy over the Internet. It lets client and server applications communicate in a way designed to prevent eavesdropping, tampering and message forgery.

TLS stands for Transport Layer Security.
