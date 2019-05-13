# Busybox FTPD Testing
-----------------------------------

Start ftpd on target:

```
tcpsvd -vE 0.0.0.0 21 ftpd -A /tmp
```

Connect from host PC:
```
host:/> ftp $YOUR_BOARD_IP 
```
