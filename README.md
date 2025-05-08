# bypass-hotspot-detection
a command to bypass hotspot detection in linux using iptables

mangle table, postrouting, all packets leaving, time to live increment by 1

``` sudo iptables -t mangle -A POSTROUTING -j TTL --ttl-inc 1 ```

fw4, openwrt, set ttl to 65  
```echo "oifname \"eth1\" ip ttl set 65" > /usr/share/nftables.d/chain-pre/mangle_postrouting/01-set-ttl.nft```
then run ```fw4 reload``` and check with ```tcpdump -i eth1 -n -vv icmp``` to make sure your ttl is 65 on your outgoing packets  
note: replace eth1 with your wan interface, mine is eth1, 'wan' does not work  
