# I. Host preparation:
---------------
From a suitable Linux distribution, install Yocto prerequisites:
```
sudo apt-get update
sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm u-boot-tools openssl
```

Set up git user name and account and save password:
```
change to your own email:
$ git config --global user.email "test@analog.com"
  
Change to your own name:
$ git config --global user.name "test"
  
Save your password:
$ git config --global credential.helper store
```

# II. Build info
---------------
```           
Build Configuration:
BB_VERSION           = "1.40.0"
BUILD_SYS            = "x86_64-linux"
NATIVELSBSTRING      = "universal"
TARGET_SYS           = "arm-poky-linux-gnueabi"
MACHINE              = "adsp-sc589-ezkit"
DISTRO               = "poky"
DISTRO_VERSION       = "2.6.2"
TUNE_FEATURES        = "arm armv7a vfp thumb neon callconvention-hard"
TARGET_FPU           = "hard"
meta                 
meta-poky            
meta-yocto-bsp       = "HEAD:50f33d3bfebcbfb1538d932fb487cfd789872026"
meta-oe              = "HEAD:4cd3a39f22a2712bfa8fc657d09fe2c7765a4005"
meta-adi-adsp-sc5xx  
meta-adi-external-toolchain = "master:7ee07ffb82b93c93884e68063307ea6041a244b2"
```

# III. Initial Setup
-----------------

Download the "repo" utility
--------------------------------

Install the "repo" utility from Google. This is used to keep the various Yocto metalayers in sync.

```
mkdir ~/bin
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

Download the BSP
---------------------

Download various meta layers from the manifest: (Note: make sure your states are not root user now.)
```
PATH=${PATH}:~/bin
mkdir -p ~/analogdevices/yocto
cd ~/analogdevices/yocto
repo init -u https://bitbucket.analog.com/scm/dte/yocto-adi-manifest.git -b develop/yocto-1.0.0
repo sync
```

# IV. Configuring Layers
-----------------
```
source setup-environment -m adsp-sc589-ezkit
```

Here is usage of setup-environment:

```
- To create a new Yocto build directory, the order can't be changed, -m firstly -b secondly:
  $ source setup-environment -m adsp-sc589-ezkit -b build 
- To create a new Yocto build directory, the build dir is 'build' by default if there is no -b <build-dir> provided:
  $ source setup-environment -m adsp-sc589-ezkit
- To use an existing Yocto build directory:
  $ source setup-environment -b builddir
- Reuse existing 'build' folder.
  $ source setup-environment
- To get the help information
  $ source setup-environment -h
``` 

It will set conf/bblayers.conf to following. The meta-adi-external-toolchain line can be omitted if not using external toolchains:

```
# POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
# changes incompatibly
POKY_BBLAYERS_CONF_VERSION = "2"

BBPATH = "${TOPDIR}"
BBFILES ?= ""
BSPDIR := "${@os.path.abspath(os.path.dirname(d.getVar('FILE', True)) + '/../..')}"

BBLAYERS ?= " \
  ${BSPDIR}/sources/poky/meta \
  ${BSPDIR}/sources/poky/meta-poky \
  ${BSPDIR}/sources/poky/meta-yocto-bsp \
  ${BSPDIR}/sources/meta-openembedded/meta-oe \
  ${BSPDIR}/sources/meta-openembedded/meta-python \  
  ${BSPDIR}/sources/meta-openembedded/meta-networking \
  ${BSPDIR}/sources/meta-adi/meta-adi-adsp-sc5xx \
  ${BSPDIR}/sources/meta-adi/meta-adi-external-toolchain \
"
```

If you're going to use the precompiled 32-bit GCC4.8 external compilers from CCES, make conf/local.conf match this, being sure to modify the machine names and compiler paths as necessary.  You'll also need to be running on a 32 bit Linux host machine:
```
#Possible machine types: adsp-sc589-ezkit, adsp-sc589-mini, adsp-sc573-ezkit, adsp-sc584-ezkit
MACHINE ??= "adsp-sc589-ezkit"

DISTRO ?= "adi-distro"
PACKAGE_CLASSES ?= "package_ipk"

EXTRA_IMAGE_FEATURES ?= "debug-tweaks"

USER_CLASSES ?= "buildstats image-mklibs image-prelink"
PATCHRESOLVE = "noop"

BB_DISKMON_DIRS ??= "\
    STOPTASKS,${TMPDIR},1G,100K \
    STOPTASKS,${DL_DIR},1G,100K \
    STOPTASKS,${SSTATE_DIR},1G,100K \
    STOPTASKS,/tmp,100M,100K \
    ABORT,${TMPDIR},100M,1K \
    ABORT,${DL_DIR},100M,1K \
    ABORT,${SSTATE_DIR},100M,1K \
    ABORT,/tmp,10M,1K"

#Add this line below if using a version 2 board that requires the ethernet modification
ANALOG_DEVICES_VERSION2_ETHERNET="1"

#Add this line to enable ADI watchdog from U-boot
ANALOG_DEVICES_WATCHDOG="1"

#If running tests which use sram_alloc(), then include the following patch as well (this disables CONFIG_ICC and enables CONFIG_ARCH_SRAM_ALLOC)
ANALOG_DEVICES_SRAM_ALLOC="1"

#Add this to allow mpv (mplayer port), netperf to build
LICENSE_FLAGS_WHITELIST = "commercial non-commercial"

TCMODE = "external"

#Modify path as necessary
EXTERNAL_TOOLCHAIN = "/analogdevices/arm-linux-gnueabi"

#Modify path as necessary
EXTERNAL_TOOLCHAIN_BAREMETAL = "/analogdevices/arm-none-eabi/bin"

#Set to your machine, looks like possibilities in the precompiled chains are:
#  sc589_rev_any, sc573_rev_any, sc589_rev_none, sc573_rev_none
ANALOG_DEVICES_PLATFORM_LIBDIR = "sc589_rev_any"


GLIBC_GENERATE_LOCALES = "en_US.UTF-8"
SECURITY_STACK_PROTECTOR_remove = "-fstack-protector-strong"
OLDEST_KERNEL = "4.4.0"
```

If you're going to use mainline compilers (GCC ~8), make conf/local.conf match this, being sure to modify the machine names as necessary.  You can do this from both 32-bit and 64-bit Linux host machines:
```
#Possible machine types: adsp-sc589-ezkit, adsp-sc589-mini, adsp-sc573-ezkit, adsp-sc584-ezkit
MACHINE ??= "adsp-sc589-ezkit"
DISTRO ?= "adi-distro"
PACKAGE_CLASSES ?= "package_ipk"

EXTRA_IMAGE_FEATURES ?= "debug-tweaks"

USER_CLASSES ?= "buildstats image-mklibs image-prelink"
PATCHRESOLVE = "noop"

BB_DISKMON_DIRS ??= "\
    STOPTASKS,${TMPDIR},1G,100K \
    STOPTASKS,${DL_DIR},1G,100K \
    STOPTASKS,${SSTATE_DIR},1G,100K \
    STOPTASKS,/tmp,100M,100K \
    ABORT,${TMPDIR},100M,1K \
    ABORT,${DL_DIR},100M,1K \
    ABORT,${SSTATE_DIR},100M,1K \
    ABORT,/tmp,10M,1K"

#Add this line below if using a version 2 board that requires the ethernet modification
ANALOG_DEVICES_VERSION2_ETHERNET="1"

#Add this line to enable ADI watchdog from U-boot
ANALOG_DEVICES_WATCHDOG="1"

#If running tests which use sram_alloc(), then include the following patch as well (this disables CONFIG_ICC and enables CONFIG_ARCH_SRAM_ALLOC)
ANALOG_DEVICES_SRAM_ALLOC="1"

#Add this to allow mpv (mplayer port), netperf to build
LICENSE_FLAGS_WHITELIST = "commercial non-commercial"
```

# V. Building
-----------------

From the build directory, build an image.  Possible types are: adsp-sc58x-minimal, adsp-sc58x-full, adsp-sc57x-minimal, adsp-sc57x-full
```
bitbake adsp-sc58x-minimal
```

# VI. Configuring NFS and TFTP  
------------------
## Install TFTP server
```
$ sudo apt-get install tftpd-hpa -y
```
Change TFTP default directory to /tftpboot from /etc/default/tftpd-hpa.
```
sudo vi /etc/default/tftpd-hpa

#add following commands 
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"

$ sudo mkdir /tftpboot
$ sudo chmod 777 /tftpboot
$ sudo service tftpd-hpa restart
```
You should add the following commands into /etc/rc.local files so that tftp can auto-restart after you 
reboot your comport.
```
$ sudo vi /etc/rc.local

#add following commands
service tftpd-hpa restart

$ sudo chmod 755 tftpd-hpa
```
## Install NFS server
```
$ sudo apt-get install nfs-kernel-server
$ sudo vi /etc/exports

#Add following commands
/romfs *(rw,sync,no_root_squash,no_subtree_check)

$ sudo mkdir /romfs/
$ sudo chmod 777 /romfs/
$ sudo service nfs-kernel-server start
```

# VII. Deploying
-----------------

## Prepare the NFS and TFTP directories:
```
cd ~/analogdevices/yocto/build/tmp/deploy/images/adsp-sc589-ezkit

cp u-boot.ldr /tftpboot/u-boot.ldr
cp u-boot /tftpboot/u-boot
cp zImage /tftpboot/zImage
cp sc589-ezkit.dtb /tftpboot/sc589-ezkit.dtb

sudo rm -rf /romfs/*

#Minimal image
sudo tar -xvf adsp-sc58x-minimal-adsp-sc589-ezkit.tar.xz -C /romfs/

#Full image
sudo tar -xvf adsp-sc58x-full-adsp-sc589-ezkit.tar.xz -C /romfs/

#... etc images

```
## Flash U-Boot to the SPI Flash
The output from u-Boot is transmitted to the host PC using the micro USB cable connected from the Host PC to the USB-to-UART port of the EZ-Kit. The following instructions in this guide use the minicom application to interact with the serial port.

### Config minicom:
Open a new terminal and set up minicom to the ADSP-SC5xx serial console. Execute the following commands on the host PC:
```
$ sudo minicom -s

            +-----[configuration]------+
            | Filenames and paths      |
            | File transfer protocols  |
            | Serial port setup        |
            | Modem and dialing        |
            | Screen and keyboard      |
            | Save setup as dfl        |
            | Save setup as..          |
            | Exit                     |
            | Exit from Minicom        |
            +--------------------------+


# Select Serial port setup

     Set Serial Device to /dev/ttyUSB0

     Set Bps/Par/Bits to 57600 8N1

     Set Hardware Flow Control to No

     Close the Serial port setup option by press Esc

 Select Save setup as dfl

 Select Exit

$ sudo minicom
```
### Loading U-Boot With GDB
Launch openocd with ICE-1000 connected and run following commands in another new terminal:
```
cd /opt/analog/cces/2.8.3/ARM/openocd/share/openocd/scripts
sudo /opt/analog/cces/2.8.3/ARM/openocd/bin/openocd -f interface/ice1000.cfg -f target/adspsc58x.cfg
```
Launch gdb in another terminal:
```
$ cd ~/analogdevices/yocto/build/tmp/work/adsp_sc589_ezkit-poky-linux-gnueabi/u-boot-adi/1.0+gitAUTOINC+0a9b06673e-r0/build/  
$ arm-none-eabi-gdb u-boot

(gdb) target remote :3333

(gdb) load arch/arm/cpu/armv7/sc58x/init.elf
          Loading section .text, size 0x580 lma 0x20080000
          Start address 0x20080024, load size 1408
          Transfer rate: 25 KB/sec, 1408 bytes/write.
(gdb) c
          Continuing.
          ^C
          Program received signal SIGINT, Interrupt.
          0x0000546e in ?? ()
(gdb) load u-boot
          Loading section .text, size 0x315ac lma 0xc2200000
          Loading section .rodata, size 0xa605 lma 0xc22315ac
          Loading section .hash, size 0x18 lma 0xc223bbb4
          Loading section .data, size 0x2e78 lma 0xc223bbcc
          Loading section .got, size 0x158 lma 0xc223ea44
          Loading section .got.plt, size 0xc lma 0xc223eb9c
          Loading section .u_boot_list, size 0x894 lma 0xc223eba8
          Loading section .rel.dyn, size 0x2680 lma 0xc223f43c
          Loading section .dynsym, size 0x30 lma 0xc2241abc
          Loading section .dynstr, size 0x1 lma 0xc2241aec
          Loading section .dynamic, size 0x90 lma 0xc2241af0
          Loading section .interp, size 0x14 lma 0xc2241b80
          Loading section .gnu.hash, size 0x18 lma 0xc2241b94
          Start address 0xc2200000, load size 269222
          Transfer rate: 28 KB/sec, 3542 bytes/write.
(gdb) c
          Continuing.
```

You should see u-boot running in the minicom:
```
U-Boot 2015.01 ADI-1.3.1 (Oct 25 2019 - 03:07:33)

CPU:   ADSP ADSP-SC589-0.0 (Detected Rev: 1.1) (spi flash boot)
VCO: 450 MHz, Cclk0: 450 MHz, Sclk0: 112.500 MHz, Sclk1: 112.500 MHz, DCLK: 225 MHz
OCLK: 150 MHz
       Watchdog enabled
I2C:   ready
DRAM:  224 MiB
MMC:   SC5XX SDH: 0
SF: Detected W25Q128BV with page size 256 Bytes, erase size 4 KiB, total 16 MiB
In:    serial
Out:   serial
Err:   serial
other init
Net:   dwmac.3100c000
Hit any key to stop autoboot:  5	
```
Set your serverip and ipaddr to the same domain when you connect the board with your HOST PC directly:
```
sc # set ipaddr <BOARD_IP>
sc # set serverip <HOST_IP>


such as:
	sc # set ipaddr 10.100.4.50
	sc # set serverip 10.100.4.174


sc # saveenv

# Write the u-boot.ldr in /tftpboot to flash via command "run update"
sc # run update
	Speed: 1000, full duplex
	Using dwmac.3100c000 device
	TFTP from server 10.100.4.174; our IP address is 10.100.4.50
	Filename 'u-boot.ldr'.
	Load address: 0x82000000
	Loading: ########################
			1.5 MiB/s
	done
	Bytes transferred = 346020 (547a4 hex)
	SF: Detected W25Q128BV with page size 256 Bytes, erase size 4 KiB, total 16 MiB
	SF: 524288 bytes @ 0x0 Erased: OK
	SF: 346020 bytes @ 0x0 Written: OK

sc # run nfsboot
```
If your network cable and your computer are in the same local area network, running following commands:
```
sc # set serverip $(HOST IP ADDRESS) 
sc # dhcp
sc # saveenv

# Write the u-boot.ldr in /tftpboot to flash via command "run update"
sc # run update
	Speed: 1000, full duplex
	Using dwmac.3100c000 device
	TFTP from server 10.99.24.170; our IP address is 10.99.24.127
	Filename 'u-boot.ldr'.
	Load address: 0x82000000
	Loading: ########################
			1.5 MiB/s
	done
	Bytes transferred = 346020 (547a4 hex)
	SF: Detected W25Q128BV with page size 256 Bytes, erase size 4 KiB, total 16 MiB
	SF: 524288 bytes @ 0x0 Erased: OK
	SF: 346020 bytes @ 0x0 Written: OK

sc # run nfsboot
```

You should eventually see a log in prompt if the kernel boot was successful:
```
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
root@adsp-sc589-ezkit:~# uname -a
Linux adsp-sc589-ezkit 4.16.0 #1 Tue May 7 17:57:54 UTC 2019 armv7l GNU/Linux
root@adsp-sc589-ezkit:~# cat /proc/version
Linux version 4.16.0 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 Tue May 7 17:57:54 UTC 2019
```
# VIII. Licensing
-----------------------------
Please see the file LICENSE.md for more details regarding the licensing for this repository.
