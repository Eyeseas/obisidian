---
title: 未命名
share: "true"
date: 2025-04-29 19:49
updated: 2025-04-29 19:49
tags: 
categories: 
---

## nftables 解决方案


```shell
nft add table inet my_nat_table

nft add chain inet my_nat_table prerouting { type nat hook prerouting priority filter \; policy accept \; }

nft add chain inet my_nat_table postrouting { type nat hook postrouting priority srcnat \; policy accept \; }

nft add rule inet my_nat_table prerouting iifname "eth0" udp dport xxxxx(替换成shadowTLS 的端口) dnat to :xxxxxx(替换成 $$-rust的端口)

nft add rule inet my_nat_table postrouting oifname "eth0" udp dport xxxxxx(替换成 $$-rust的端口) masquerade
```


## ss-rust 解决方案

```json
{
    "server": "::",
    "server_port": xxxxx(shadow TLS端口，让$$来接管这个端口的 udp 流量),
    "password": "xxxxxxxx",
    "method": "2022-blake3xxxxxxxx",
    "fast_open": true,
    "mode": "udp_only",
    "user": "nobody",
    "timeout": 300
}
```