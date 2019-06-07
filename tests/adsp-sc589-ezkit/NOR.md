# Serial NOR Flash MTD Driver
-----------------------------------

Fails on ubiattach

```
root@adsp-sc589-ezkit:~# cat /proc/mtd
dev:    size   erasesize  name
mtd0: 00080000 00001000 "uboot (spi)"
mtd1: 00580000 00001000 "kernel (spi)"
mtd2: 00a00000 00001000 "root file system (spi)"
```

```
root@adsp-sc589-ezkit:~# ubinfo
UBI version:                    1
Count of UBI devices:           0
UBI control device major/minor: 10:57
```

```
root@adsp-sc589-ezkit:~# ubiformat /dev/mtd2
ubiformat: mtd2 (nor), size 10485760 bytes (10.0 MiB), 2560 eraseblocks of 4096 bytes (4.0 KiB), min. I/O size 1 bytes
libscan: scanning eraseblock 2559 -- 100 % complete  
ubiformat: 1 eraseblocks have valid erase counter, mean value is 1
ubiformat: 2559 eraseblocks are supposedly empty
ubiformat: warning!: only 1 of 2560 eraseblocks have valid erase counter
ubiformat: erase counter 0 will be used for all eraseblocks
ubiformat: note, arbitrary erase counter value may be specified using -e option
ubiformat: continue? (y/N) y
ubiformat: use erase counter 0 for all eraseblocks
ubiformat: formatting eraseblock 2559 -- 100 % complete  
```

```
root@adsp-sc589-ezkit:~# ubiattach /dev/ubi_ctrl -m 2
ubi0: attaching mtd2
ubi0: scanning is finished
spi_master spi2: spi rx overrun
ubi0 warning: ubi_io_read: error -5 while reading 3956 bytes from PEB 0:128, read only 0 bytes, retry
```


...


```
mount -t ubifs ubi0:ubifs0 /mnt
ubimkvol /dev/ubi0 -s 20000000 -N ubifs0;
```