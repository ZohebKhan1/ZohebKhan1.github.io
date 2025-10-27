---
date: 2024-10-22
publishDate: 2024-10-22
external_link: ""
image:
  caption: Stealth-VPN
  focal_point: Smart
slides: example
summary: A stunnel based virtual private network service for unrestricted internet access
tags:
- Opensource
title: Stealth-VPN for Unrestricted Network Access
links:
  - icon_pack: fab
    icon: github
    name: Source
    url: 'https://github.com/prasenjit52282/docker-stealth-openvpn'
---
The repository implements a scalable non-blockable VPN service to enable unrestricted internet within an organisation that restricts network via firewalls. The clients are oblivious to the interanl working process and only route traffic through the local socks5 proxy deployed within the organisation. The proxy host forward all packet via a stunnel to the open internet (VPN server). Moreover, the local openssh server allows outgoing ssh connections from the restricted network.

* VPN server must allows inbound connection to port: 443
* Local Proxy must allows outbound connection to port: 443, and inbound connection to ports: 2000 (socks5), 2002 (sshd)
* End user must use appropiate proxy clients to connect to the local proxy server. Some tested clients are shown later