# USB0: Gadget Storage
-----------------------------------

Create backing file
```
root@adsp-sc589-ezkit:~# dd if=/dev/zero of=/fsg.block bs=1M count=16
```

Probe driver
```
root@adsp-sc589-ezkit:~# modprobe g_mass_storage file=/fsg.block stall=0
Mass Storage Function, version: 2009/09/11
LUN: removable file: (no medium)
LUN: file: /fsg.block
Number of LUNs=1
g_mass_storage gadget: Mass Storage Gadget, version: 2009/09/11
g_mass_storage gadget: userspace failed to provide iSerialNumber
g_mass_storage gadget: g_mass_storage ready
```

Plug in USB cable:
```
root@adsp-sc589-ezkit:
g_mass_storage gadget: high-speed config #1: Linux File-Backed Storage
```

From host machine, should see:
```
[19110.193008] usb 3-2: new high-speed USB device number 7 using ehci-pci
[19110.341978] usb 3-2: New USB device found, idVendor=0525, idProduct=a4a5
[19110.341983] usb 3-2: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[19110.341986] usb 3-2: Product: Mass Storage Gadget
[19110.341988] usb 3-2: Manufacturer: Linux 4.16.0 with musb-hdrc
[19110.378402] usb-storage 3-2:1.0: USB Mass Storage device detected
[19110.378589] usb-storage 3-2:1.0: Quirks match for vid 0525 pid a4a5: 10000
[19110.378661] scsi host8: usb-storage 3-2:1.0
[19110.378822] usbcore: registered new interface driver usb-storage
[19110.393754] usbcore: registered new interface driver uas
[19111.381977] scsi 8:0:0:0: Direct-Access     Linux    File-Stor Gadget 0416 PQ: 0 ANSI: 2
[19111.382680] sd 8:0:0:0: Attached scsi generic sg2 type 0
[19111.384326] sd 8:0:0:0: [sdc] 32768 512-byte logical blocks: (16.8 MB/16.0 MiB)
[19111.384971] sd 8:0:0:0: [sdc] Write Protect is off
[19111.384977] sd 8:0:0:0: [sdc] Mode Sense: 0f 00 00 00
[19111.385691] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[19111.393687] sd 8:0:0:0: [sdc] Attached SCSI disk
```

From host machine, format the file:
```

nathan@Debian-BuildMachine:~$ sudo fdisk /dev/sdc

Welcome to fdisk (util-linux 2.29.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x6a7fa03b.

Command (m for help): o
Created a new DOS disklabel with disk identifier 0x29a5879f.

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): 

Using default response p.
Partition number (1-4, default 1): 
First sector (2048-32767, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-32767, default 32767): 

Created a new partition 1 of type 'Linux' and of size 15 MiB.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

```


From host machine, create ext3 partition:
```
nathan@Debian-BuildMachine:~$ sudo mkfs.ext3 /dev/sdc1
mke2fs 1.43.4 (31-Jan-2017)
Creating filesystem with 15360 1k blocks and 3840 inodes
Filesystem UUID: cf17644b-2e24-4853-bf79-ead01ed12e7e
Superblock backups stored on blocks: 
	8193

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done
```

From host machine, mount ext3 partition and write a file to it:
```
nathan@Debian-BuildMachine:~$ sudo mkdir -p /mnt/test
nathan@Debian-BuildMachine:~$ sudo mount /dev/sdc1 /mnt/test
nathan@Debian-BuildMachine:~$ sudo touch /mnt/test/test.txt
nathan@Debian-BuildMachine:~$ sudo chmod 777 /mnt/test/test.txt
nathan@Debian-BuildMachine:~$ echo "test" > /mnt/test/test.txt
nathan@Debian-BuildMachine:~$ sudo umount /mnt/test
```

From target machine:
```
root@adsp-sc589-ezkit:~# rmmod g_mass_storage
root@adsp-sc589-ezkit:~# mkdir -p /mnt/test
root@adsp-sc589-ezkit:~# losetup -o 1048576 /dev/loop0 /mnt/test
root@adsp-sc589-ezkit:~# mount -text3 /dev/loop0 /mnt/test
EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
```

Make sure the file was properly created:
```
root@adsp-sc589-ezkit:~# cat /mnt/test/test.txt 
test
```
