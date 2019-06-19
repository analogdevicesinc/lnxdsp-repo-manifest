# USB0: Gadget Ethernet
-----------------------------------

Probe the module
```
root@adsp-sc589-ezkit:~# modprobe g_ether
using random self ethernet address
using random host ethernet address
usb0: HOST MAC 76:8c:43:73:7e:7b
usb0: MAC 96:10:d1:f4:03:f2
using random self ethernet address
using random host ethernet address
g_ether gadget: Ethernet Gadget, version: Memorial Day 2008
g_ether gadget: g_ether ready
g_ether gadget: high-speed config #1: CDC Ethernet (ECM)
```

Set an IP
```
root@adsp-sc589-ezkit:~# ifconfig usb0 192.168.1.155
```

Ping IP from another machine
```
nathan@Debian-BuildMachine:~$ ping 192.168.1.155
PING 192.168.1.155 (192.168.1.155) 56(84) bytes of data.
64 bytes from 192.168.1.155: icmp_seq=1 ttl=64 time=1.49 ms
64 bytes from 192.168.1.155: icmp_seq=2 ttl=64 time=0.799 ms
^C
--- 192.168.1.155 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.799/1.146/1.493/0.347 ms
```