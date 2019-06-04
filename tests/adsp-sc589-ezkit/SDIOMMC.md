# SDIO MMC Testing
-----------------------------------

Plug in an SD card and you should see device instantiate like so:
```
root@adsp-sc589-ezkit:~#
mmc_host mmc0: Bus speed (slot 0) = 50000000Hz (slot req 25000000Hz, actual 25000000HZ div = 1)
mmc0: new SD card at address b368
mmcblk0: mmc0:b368 SMI   1.86 GiB 
 mmcblk0: p1
```


Fdisk should also show the device:
```
root@adsp-sc589-ezkit:~# fdisk -l
Disk /dev/mmcblk0: 1902 MB, 1994391552 bytes, 3895296 sectors
92745 cylinders, 7 heads, 6 sectors/track
Units: sectors of 1 * 512 = 512 bytes

Device       Boot StartCHS    EndCHS        StartLBA     EndLBA    Sectors  Size Id Type
/dev/mmcblk0p1    0,2,6       966,6,6            131    3895295    3895165 1901M  6 FAT16
```