# Some websites not loading

Mostly shopify webshops, like https://www.analuisa.com/

https://stackoverflow.com/questions/12849986/connection-timeout-when-accessing-github

Solution: MTU needs to be lowered from 1500 to 1400 (https://askubuntu.com/a/655593/429828)

The problem with the command in the solution that the change is not permanent, after restart it resets.

Typing `ifconfig` shows something like this:

```
wlx9848278f1bf6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::XXXX:XXXX:XXXX:4692  prefixlen 64  scopeid 0x20<link>
        ether 98:XX:XX:XX:1b:f6  txqueuelen 1000  (Ethernet)
        RX packets 541775  bytes 512353709 (512.3 MB)
        RX errors 0  dropped 5  overruns 0  frame 0
        TX packets 157612  bytes 51903178 (51.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Note the end of the 1st line saying `mtu 1500`

_TODO: add info on how to change the MTU permanently_

Changing the MTU permanently: https://www.baeldung.com/linux/maximum-transmission-unit-change-size
