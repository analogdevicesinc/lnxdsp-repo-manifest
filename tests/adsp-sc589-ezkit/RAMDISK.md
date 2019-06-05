# RAM Disk Testing
-----------------------------------

Build image
```
bitbake adsp-sc58x-ramdisk
```

Deploy image.  (Also copy over zImage and DTB, if not already present)
```
copy <Yocto directory>/tmp/deploy/images/adsp-sc589-ezkit/adsp-sc58x-ramdisk-adsp-sc589-ezkit.cpio.xz.u-boot to <TFTP directory>/ramdisk.cpio.xz.u-boot
```

Run the image from u-boot:
```
run ramboot
```

You should then see:
```
sc # run ramboot
Speed: 1000, full duplex
Using dwmac.3100c000 device
TFTP from server 192.168.1.15; our IP address is 192.168.1.33
Filename 'AnalogDevices/zImage'.
Load address: 0xc2000000
Loading: *#################################################################
	 #################################################################
	 #################################################################
	 ##############################################################
	 5.5 MiB/s
done
Bytes transferred = 3759064 (395bd8 hex)
Speed: 1000, full duplex
Using dwmac.3100c000 device
TFTP from server 192.168.1.15; our IP address is 192.168.1.33
Filename 'AnalogDevices/sc589-ezkit.dtb'.
Load address: 0xc4000000
Loading: *##
	 4.8 MiB/s
done
Bytes transferred = 20163 (4ec3 hex)
Speed: 1000, full duplex
Using dwmac.3100c000 device
TFTP from server 192.168.1.15; our IP address is 192.168.1.33
Filename 'AnalogDevices/adsp-sc58x-ramdisk-adsp-sc589-ezkit.cpio.xz.u-boot'.
Load address: 0xc5000000
Loading: *#################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 #################################################################
	 ################################################################
	 5.5 MiB/s
done
Bytes transferred = 10476436 (9fdb94 hex)
Kernel image @ 0xc2000000 [ 0x000000 - 0x395bd8 ]
## Loading init Ramdisk from Legacy Image at c5000000 ...
   Image Name:   Analog Devices Ram Disk Image
   Image Type:   ARM Linux RAMDisk Image (gzip compressed)
   Data Size:    10476372 Bytes = 10 MiB
   Load Address: 00000000
   Entry Point:  00000000
   Verifying Checksum ... OK
## Flattened Device Tree blob at c4000000
   Booting using the fdt blob at 0xc4000000
   Loading Ramdisk to cf460000, end cfe5db54 ... OK
   Loading Device Tree to cf458000, end cf45fec2 ... OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
Booting Linux on physical CPU 0x0
Linux version 4.16.0 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 Wed Jun 5 12:39:32 UTC 2019

...

Unpacking initramfs...
Freeing initrd memory: 10232K

...


     @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@     
     @@@@@@@@     @@@@@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@        @@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@            @@@@@@@@@@@@@@@@@@@
     @@@@@@@@               @@@@@@@@@@@@@@@@
     @@@@@@@@                   @@@@@@@@@@@@
     @@@@@@@@                     @@@@@@@@@@
     @@@@@@@@                        @@@@@@@
     @@@@@@@@                     @@@@@@@@@@
     @@@@@@@@                   @@@@@@@@@@@@
     @@@@@@@@               @@@@@@@@@@@@@@@@
     @@@@@@@@            @@@@@@@@@@@@@@@@@@@
     @@@@@@@@        @@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@     @@@@@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

        Analog Devices Yocto Distribution
                 www.analog.com
              www.yoctoproject.org

adsp-sc589-ezkit login: 
```