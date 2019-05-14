# CRC Check Using Crypto Framework
-----------------------------------

Check that CRC drivers were started properly:

```
root@adsp-sc589-ezkit:~# dmesg | grep crc
	bfin-hmac-crc 31001200.crc: initialized
	bfin-hmac-crc 31001300.crc: initialized
root@adsp-sc589-ezkit:~# dmesg | grep CRC
	Blackfin hardware CRC crypto driver
```

Run tcrypt:
```
root@adsp-sc589-ezkit:~# modprobe tcrypt mode=110
modprobe: ERROR: could not insert 'tcrypt': Resource temporarily unavailable
```

Make sure proc/crypto still shows passed:
```
root@adsp-sc589-ezkit:~# cat /proc/crypto | grep -C 10 hmac
name         : hmac(crc32)
driver       : bfin-hmac-crc
module       : kernel
priority     : 100
refcnt       : 1
selftest     : passed
internal     : no
type         : ahash
async        : yes
blocksize    : 1
digestsize   : 4
```


