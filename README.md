# yingshaoxo v2ray

Works in linux 32 bit version.

v2ray 4.38.2.


## Server

```
./v2ray
```

In server, it will only block torrent connection.

And listen 1314 port with vmess protocol, listen 1080 port for socks5 protocol.

Normally you use socks5 protocol, because it is simple to config.


## Client

```
./v2ray -c client_config.json
```

In client, it will:

1. convert 'googleapis.cn' to 'googleapis.com'
2. link 'local.pornhub.com' to '192.168.2.66', a LAN website for video stream
3. use dns '1.1.1.1' for non_cn domain, use dns '8.8.8.8' for cn domain
4. it listens 10807 socks5, so other device can connect, it can works as server and client at the same time. listens 10808 socks5, so kitsunebi v2ray android client can connect.
5. it connect to the server by using username/password 'admin'. that is the proxy route. 
6. for routing, all LAN(geoip:private) connection will go as direct normal network. all bittorrent will go as direct normal network without proxy. dns ip '8.8.8.8' will go direct network. dns ip '1.1.1.1' will go proxy channel. all us domain will go proxy channel. the server ip '14.202.109.163' will go direct channel because server ip need to get connected directly.
7. everything else will go to blackhole or block channel, we block everything except some domain or ip that goes direct channel. Here, the 'qq.com' and 'bing.com' works fine, but other connections will get blocked.


## Android client

As I tested out, v2rayNG will fail to start with client_config. Error is "this rule has no effective fields".

`Kitsunebi 1.8.0` works fine. (fun.kitsunebi.kitsunebi4android)

Old android ssl certification are broken, so do not use https.

> The real usage is to work with `vpnhotspot` to create a out network whitelist firewall, a real firewall that only allows some domain or ip visit. Root needed.

> Not like ubuntu ufw, they are fake firewall, if hacker can let your server visit their server, your server can still get remotely controlled.

> Since android become harder and harder to use, you should drop it.
