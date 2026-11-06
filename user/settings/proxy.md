---
title: Proxy
description: Configure proxy servers for your network connections.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kcontrol6/proxy/index.docbook
source_authors: [Krishna Tateneni]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b21968 (kcms/proxy); read from code, not clicked through"
---

# Proxy

Proxies are programs on a computer acting as a server on your network. They receive requests, such as HTTP and FTP, retrieve the files from the Internet and pass them to the computer that asked for them.

When you've configured a proxy, requests are rerouted through it. You can also select specific hosts to contact directly. On a local network, for example, local hosts probably don't need to go through a proxy.

You should only need to configure a proxy if your network administrator or Internet service provider requires it. If everything seems fine with your Internet connection, you don't need to change anything. If you aren't sure, consult your provider's setup guide or your system administrator.

## Options

- **No proxy:** Connects to the Internet directly.
- **Detect proxy configuration automatically:** Finds and downloads the proxy setup script automatically, using the Web Proxy Auto-Discovery (WPAD) protocol. The module warns that this is almost never the correct configuration.
- **Use proxy auto configuration URL:** Use this if your proxy support comes from a script at a specific address. Enter the address, or use the folder button to browse to it.
- **Use system proxy configuration:** Some systems use variables such as `$HTTP_PROXY`, so that all applications can share the same proxy information. If this applies to you, select this option and click **Auto Detect** to fill in the names of the environment variables. In **Exceptions**, enter the variable, such as `$NO_PROXY`, that stores the sites that shouldn't use the proxy. **Show the value of the environment variables** shows their values instead of their names, but you can't edit them here.
- **Use manually specified proxy configuration:** Enter each proxy's address and port number. **Use this proxy server for all protocols** copies the HTTP proxy's address and port into the other fields, to save typing.

## Exceptions

Enter a comma-separated list of hostnames or IP addresses that shouldn't use the proxy settings.

- To exclude all hosts of a domain, enter the domain name preceded by a dot, such as `.example.org`.
- Wildcards such as `*` and `?` aren't supported.
- You can also enter IP addresses, such as `127.0.0.1`, and IP addresses with a subnet, such as `192.168.0.1/24`.

**Use proxy settings only for addresses in the exceptions list** reverses this, so proxies are only used for addresses in the list. This is useful if you only need a proxy for a few specific sites, such as an internal intranet. For more complex needs, you might want to use a configuration script.
