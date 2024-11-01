# bypass-hotspot-detection
a command to bypass hotspot detection in linux using iptables

mangle table, postrouting, all packets leaving, time to live increment by 1

``` sudo iptables -t mangle -A POSTROUTING -j TTL --ttl-inc 1 ```
