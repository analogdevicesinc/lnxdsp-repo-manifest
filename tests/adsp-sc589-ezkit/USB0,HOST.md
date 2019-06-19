# USB0: Host
-----------------------------------

Plug in USB thumb drive using OTG cable, check to see if device shows up in dmesg:
```
root@adsp-sc589-ezkit:~# dmesg | tail
udevd[784]: starting version 3.2.7
udevd[784]: specified group 'kvm' unknown
udevd[785]: starting eudev-3.2.7
udevd[785]: inotify_init failed: Function not implemented
udevd[785]: error initializing inotify
random: crng init done
```

Not sure why we must start g_mass_storage for the thumb drive to show up:
```
root@adsp-sc589-ezkit:~# dd if=/dev/zero of=/fsg.block bs=1M count=16
root@adsp-sc589-ezkit:~# modprobe g_mass_storage file=/fsg.block stall=0
```

```
root@adsp-sc589-ezkit:~# dmesg | tail
usb-storage 1-1:1.0: USB Mass Storage device detected
scsi host0: usb-storage 1-1:1.0
scsi 0:0:0:0: Direct-Access     General  UDisk            5.00 PQ: 0 ANSI: 2
sd 0:0:0:0: [sda] 7864320 512-byte logical blocks: (4.03 GB/3.75 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 0b 00 00 08
sd 0:0:0:0: [sda] No Caching mode page found
sd 0:0:0:0: [sda] Assuming drive cache: write through
 sda: sda1
sd 0:0:0:0: [sda] Attached SCSI removable disk
```

```
root@adsp-sc589-ezkit:~# lsmod
Module                  Size  Used by
g_mass_storage         16384  0
usb_f_mass_storage     32768  2 g_mass_storage
libcomposite           40960  2 g_mass_storage,usb_f_mass_storage
configfs               32768  3 usb_f_mass_storage,libcomposite
```