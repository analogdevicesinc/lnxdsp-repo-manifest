
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

Download various meta layers from the manifest:

```
PATH=${PATH}:~/bin
mkdir -p /analogdevices/yocto
cd /analogdevices/yocto
repo init -u https://bitbucket.analog.com/scm/dte/yocto-adi-manifest.git -b
develop/yocto-1.0.0
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


# VI. Deploying
-----------------

Prepare the NFS and TFTP directories:
```
cd <Yocto Directory>/build/tmp/deploy/images/adsp-sc589-ezkit

export tftp=<TFTP DIRECTORY>
export rootfs=<ROOTFS DIRECTORY>

cp u-boot.ldr ${tftp}/u-boot.ldr
cp u-boot ${tftp}/u-boot
cp zImage ${tftp}/zImage
cp sc589-ezkit.dtb ${tftp}/sc589-ezkit.dtb

sudo rm -rf ${rootfs}
sudo mkdir ${rootfs}
sudo chmod 777 ${rootfs}

#Minimal image
sudo tar -xvf adsp-sc58x-minimal-adsp-sc589-ezkit.tar.xz -C ${rootfs}

#Full image
sudo tar -xvf adsp-sc58x-full-adsp-sc589-ezkit.tar.xz -C ${rootfs}

#... etc images

```

Launch openocd with ICE-1000 connected:
```
sudo /opt/analog/cces/2.8.3/ARM/openocd/bin/openocd -f interface/ice1000.cfg -f target/adspsc58x.cfg
```

Launch gdb in another terminal:
```
cd /opt/analog/cces-linux-add-in/1.3.0/uboot-sc5xx-1.3.0/bin
arm-none-eabi-gdb u-boot-sc589-ezkit
```

Load u-boot through GDB
```
(gdb) target remote :3333

(gdb) load init-sc589-ezkit.elf
          Loading section .text, size 0x580 lma 0x20080000
          Start address 0x20080024, load size 1408
          Transfer rate: 25 KB/sec, 1408 bytes/write.
(gdb) c
          Continuing.
          ^C
          Program received signal SIGINT, Interrupt.
          0x0000546e in ?? ()
(gdb) load <TFTP DIRECTORY>/u-boot
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

Flash U-Boot to the SPI Flash
```
sc # env default -a
sc # editenv ubootfile
sc # editenv serverip
sc # dhcp
        Speed: 1000, full duplex
        BOOTP broadcast 1
        BOOTP broadcast 2
        DHCP client bound to address 192.168.1.33 (563 ms)


sc # run update
```

Unplug ICE-1000 from host's USB port, finalize and save boot arguments, and run nfsboot to boot from NFS:
```
sc # sleep 10 && reset
sc # env default -a
sc # editenv ubootfile
sc # editenv serverip
sc # editenv dtbfile
sc # editenv nfsfile
sc # editenv rootpath
sc # saveenv
sc # dhcp
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

# VII. Licensing
-----------------
Please see the file LICENSE.md for more details regarding the licensing for this repository.
