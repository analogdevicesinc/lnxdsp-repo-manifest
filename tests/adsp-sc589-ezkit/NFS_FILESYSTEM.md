# NFS File System Test
-----------------------------------


From U-boot, set the the appropriate environment variables and perform an NFS boot with the appropriate NFS server running somewhere.  This is the same as documented in the main README.md:

```
sc # env default -a
sc # editenv ubootfile
sc # editenv serverip
sc # editenv dtbfile
sc # editenv nfsfile
sc # editenv rootpath
sc # printenv ubootfile serverip dtbfile nfsfile rootpath
		ubootfile=analog/u-boot.ldr
		serverip=192.168.1.7
		dtbfile=analog/sc589-ezkit.dtb
		nfsfile=analog/zImage
		rootpath=/mnt/HDD/rootfs/analog
sc # saveenv
sc # dhcp
		Speed: 1000, full duplex
		BOOTP broadcast 1
		BOOTP broadcast 2
		DHCP client bound to address 192.168.1.33 (562 ms)
sc # run nfsboot


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
     
adsp-sc589-ezkit login: root
Password: adi

```
