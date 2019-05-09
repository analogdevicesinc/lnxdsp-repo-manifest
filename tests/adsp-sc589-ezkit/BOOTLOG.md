```
U-Boot 2015.01 ADI-1.3.0 (May 07 2019 - 17:01:10)

CPU:   ADSP ADSP-SC589-0.1 (Detected Rev: 1.1) (spi flash boot)
VCO: 450 MHz, Cclk0: 450 MHz, Sclk0: 112.500 MHz, Sclk1: 112.500 MHz, DCLK: 450 MHz
OCLK: 150 MHz
I2C:   ready
DRAM:  224 MiB
MMC:   SC5XX SDH: 0
SF: Detected W25Q128BV with page size 256 Bytes, erase size 4 KiB, total 16 MiB
In:    serial
Out:   serial
Err:   serial
other init
Net:   dwmac.3100c000
Hit any key to stop autoboot:
sc # 
sc # run dhcp
Speed: 1000, full duplex
BOOTP broadcast 1
BOOTP broadcast 2
DHCP client bound to address 192.168.1.33 (561 ms)
sc # 
sc # run nfsboot
Speed: 1000, full duplex
Using dwmac.3100c000 device
TFTP from server 192.168.1.7; our IP address is 192.168.1.33
Filename 'analog/zImage'.
Load address: 0xc2000000
Loading: *#################################################################
	 #################################################################
	 #################################################################
	 ############################################################
	 3.9 MiB/s
done
Bytes transferred = 3743152 (391db0 hex)
Speed: 1000, full duplex
Using dwmac.3100c000 device
TFTP from server 192.168.1.7; our IP address is 192.168.1.33
Filename 'analog/sc589-ezkit.dtb'.
Load address: 0xc4000000
Loading: *##
	 3.6 MiB/s
done
Bytes transferred = 19115 (4aab hex)
Kernel image @ 0xc2000000 [ 0x000000 - 0x391db0 ]
## Flattened Device Tree blob at c4000000
   Booting using the fdt blob at 0xc4000000
   Loading Device Tree to cfe57000, end cfe5eaaa ... OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
Booting Linux on physical CPU 0x0
Linux version 4.16.0 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 Tue May 7 17:57:54 UTC 2019
CPU: ARMv7 Processor [410fc051] revision 1 (ARMv7), cr=10c53c7d
CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
OF: fdt: Machine model: ADI sc589-ezkit
bootconsole [earlycon0] enabled
Memory policy: Data cache writeback
Hit pending asynchronous external abort (FSR=0x00001c06) during first unmask, this is most likely caused by a firmware/bootloader bug.
CPU: All CPU(s) started in SVC mode.
dump init clock rate
CGU0_PLL 450 MHz
CGU0_SYSCLK 225 MHz
CGU0_CCLK 450 MHz
CGU0_SYS0 112 MHz
CGU0_DCLK 450 MHz
CGU0_OCLK 150 MHz
CGU0_SYS0 112 MHz
random: fast init done
Built 1 zonelists, mobility grouping on.  Total pages: 56896
Kernel command line: root=/dev/nfs rw nfsroot=192.168.1.7:/mnt/HDD/rootfs/analog,tcp,nfsvers=3 clkin_hz=(25000000) earlyprintk=serial,uart0,57600 console=ttySC0,57600 mem=224M ip=192.168.1.33:192.168.1.7:192.168.1.1:255.255.255.0:sc58x:eth0:off
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 217720K/229376K available (6144K kernel code, 191K rwdata, 1484K rodata, 1024K init, 108K bss, 11656K reserved, 0K cma-reserved)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0xce800000 - 0xff800000   ( 784 MB)
    lowmem  : 0xc0000000 - 0xce000000   ( 224 MB)
    modules : 0xbf000000 - 0xc0000000   (  16 MB)
      .text : 0x(ptrval) - 0x(ptrval)   (7136 kB)
      .init : 0x(ptrval) - 0x(ptrval)   (1024 kB)
      .data : 0x(ptrval) - 0x(ptrval)   ( 192 kB)
       .bss : 0x(ptrval) - 0x(ptrval)   ( 109 kB)
NR_IRQS: 16, nr_irqs: 16, preallocated irqs: 16
clocksource: cs_gptimer: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 16988981748 ns
sched_clock: 32 bits at 112MHz, resolution 8ns, wraps every 19088743419ns
Console: colour dummy device 80x30
Calibrating delay loop... 297.98 BogoMIPS (lpj=595968)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
CPU: Testing write buffer coherency: ok
Setting up static identity map for 0xc2100000 - 0xc210003c
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 2 part 30 variant 5 rev 1
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
futex hash table entries: 256 (order: -1, 3072 bytes)
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
L2C: device tree omits to specify unified cache
L2C-310 dynamic clock gating enabled, standby mode enabled
L2C-310 cache controller enabled, 8 ways, 256 kB
L2C-310: CACHE_ID 0x410000c9, AUX_CTRL 0x06040000
sc58x_init: registering device resources
sec init...
enabled
hw-breakpoint: Failed to enable monitor mode on CPU 0.
ADI DMA2 Controller
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
i2c-adi-twi 31001400.twi: ADI on-chip I2C TWI Controller, regs_base@c2cc3a9f
i2c-adi-twi 31001500.twi: ADI on-chip I2C TWI Controller, regs_base@269219d8
i2c-adi-twi 31001600.twi: ADI on-chip I2C TWI Controller, regs_base@7d565a14
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
Advanced Linux Sound Architecture Driver Initialized.
clocksource: Switched to clocksource cs_gptimer
NET: Registered protocol family 2
tcp_listen_portaddr_hash hash table entries: 512 (order: 0, 4096 bytes)
TCP established hash table entries: 2048 (order: 1, 8192 bytes)
TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
TCP: Hash tables configured (established 2048 bind 2048)
UDP hash table entries: 256 (order: 0, 4096 bytes)
UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
hw perfevents: no interrupt-affinity property for /pmu, guessing.
hw perfevents: enabled with armv7_cortex_a5 PMU driver, 3 counters available
workingset: timestamp_bits=30 max_order=16 bucket_order=0
NFS: Registering the id_resolver key type
Key type id_resolver registered
Key type id_legacy registered
nfs4filelayout_init: NFSv4 File Layout Driver Registering...
jffs2: version 2.2. (NAND) Â© 2001-2006 Red Hat, Inc.
io scheduler noop registered (default)
io scheduler mq-deadline registered
io scheduler kyber registered
ADI serial driver
adi-uart4.0: ttySC0 at MMIO 0x31003000 (irq = 21, base_baud = 7031250) is a ADI-UART4
console [ttySC0] enabled
console [ttySC0] enabled
bootconsole [earlycon0] disabled
bootconsole [earlycon0] disabled
loop: module loaded
adi-spi3 31042000.spi: registered ADI SPI controller spi0
m25p80 spi2.38: found w25q128, expected w25q32
m25p80 spi2.38: w25q128 (16384 Kbytes)
3 ofpart partitions found on MTD device spi2.38
Creating 3 MTD partitions on "spi2.38":
0x000000000000-0x000000080000 : "uboot (spi)"
0x000000080000-0x000000600000 : "kernel (spi)"
0x000000600000-0x000001000000 : "root file system (spi)"
adi-spi3 31044000.spi: registered ADI SPI controller spi2
libphy: Fixed MDIO Bus: probed
CAN device driver interface
stmmaceth 3100c000.ethernet: PTP uses main clock
stmmaceth 3100c000.ethernet: no reset control found
stmmac - user ID: 0x10, Synopsys ID: 0x37
stmmaceth 3100c000.ethernet: Ring mode enabled
stmmaceth 3100c000.ethernet: DMA HW capability register supported
stmmaceth 3100c000.ethernet: Enhanced/Alternate descriptors
stmmaceth 3100c000.ethernet: Enabled extended descriptors
stmmaceth 3100c000.ethernet: RX Checksum Offload Engine supported
stmmaceth 3100c000.ethernet: COE Type 2
stmmaceth 3100c000.ethernet: TX Checksum insertion supported
stmmaceth 3100c000.ethernet: Wake-Up On Lan supported
stmmaceth 3100c000.ethernet: Enable RX Mitigation via HW Watchdog Timer
libphy: stmmac: probed
force_sf_dma_mode is ignored if force_thresh_dma_mode is set.
stmmaceth 3100e000.ethernet: PTP uses main clock
stmmaceth 3100e000.ethernet: no reset control found
stmmac - user ID: 0x11, Synopsys ID: 0x37
stmmaceth 3100e000.ethernet: Ring mode enabled
stmmaceth 3100e000.ethernet: DMA HW capability register supported
stmmaceth 3100e000.ethernet: Enhanced/Alternate descriptors
stmmaceth 3100e000.ethernet: Enabled extended descriptors
stmmaceth 3100e000.ethernet: RX Checksum Offload Engine supported
stmmaceth 3100e000.ethernet: COE Type 2
stmmaceth 3100e000.ethernet: Wake-Up On Lan supported
stmmaceth 3100e000.ethernet: Enable RX Mitigation via HW Watchdog Timer
libphy: stmmac: probed
NS DP83848C 10/100 Mbps PHY stmmac-1:01: attached PHY driver [NS DP83848C 10/100 Mbps PHY] (mii_bus:phy_addr=stmmac-1:01, irq=POLL)
usbcore: registered new interface driver usb-storage
musb-hdrc musb-hdrc.1.auto: MUSB HDRC host driver
musb-hdrc musb-hdrc.1.auto: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
rtc rtc0: invalid alarm value: 1900-1-8 0:0:0
rtc-adi2 310c8000.rtc: registered as rtc0
i2c /dev entries driver
adi_wdt: initialized: timeout=20 sec (nowayout=0)
Synopsys Designware Multimedia Card Interface Driver
dwmmc_adi 31010000.mmc: IDMAC supports 32-bit address mode.
dwmmc_adi 31010000.mmc: Using internal DMA controller.
dwmmc_adi 31010000.mmc: Version ID is 270a
dwmmc_adi 31010000.mmc: DW MMC controller at irq 45,32 bit host data width,1024 deep fifo
mmc_host mmc0: Bus speed (slot 0) = 50000000Hz (slot req 400000Hz, actual 396825HZ div = 63)
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
icc 20080000.icc: initialized
NET: Registered protocol family 10
Segment Routing with IPv6
sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
NET: Registered protocol family 17
can: controller area network core (rev 20170425 abi 9)
NET: Registered protocol family 29
can: raw protocol (rev 20170425)
can: broadcast manager protocol (rev 20170425 t)
can: netlink gateway (rev 20170425) max_hops=1
Key type dns_resolver registered
ThumbEE CPU extension supported.
console [netcon0] enabled
netconsole: network logging started
rtc-adi2 310c8000.rtc: setting system clock to 2019-05-08 20:06:14 UTC (1557345974)
TI DP83867 stmmac-0:00: attached PHY driver [TI DP83867] (mii_bus:phy_addr=stmmac-0:00, irq=POLL)
stmmaceth 3100c000.ethernet eth0: IEEE 1588-2008 Advanced Timestamp supported
stmmaceth 3100c000.ethernet eth0: registered PTP clock
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
stmmaceth 3100c000.ethernet eth0: Link is Up - 1Gbps/Full - flow control rx/tx
IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
IP-Config: Complete:
     device=eth0, hwaddr=02:80:ad:20:31:e8, ipaddr=192.168.1.33, mask=255.255.255.0, gw=192.168.1.1
     host=sc58x, domain=, nis-domain=(none)
     bootserver=192.168.1.7, rootserver=192.168.1.7, rootpath=
ALSA device list:
  No soundcards found.
VFS: Mounted root (nfs filesystem) on device 0:11.
devtmpfs: mounted
Freeing unused kernel memory: 1024K
INIT: version 2.88 booting
Starting udev
udevd[682]: starting version 3.2.7
udevd[682]: specified group 'kvm' unknown
udevd[683]: starting eudev-3.2.7
udevd[683]: inotify_init failed: Function not implemented
udevd[683]: error initializing inotify
ALSA: Restoring mixer settings...
/usr/sbin/alsactl: load_state:1735: No soundcards found...
INIT: Entering runlevel: 5
Configuring network interfaces... ip: RTNETLINK answers: File exists
ifup skipped for nfsroot interface eth0
run-parts: /etc/network/if-pre-up.d/nfsroot: exit status 1
Starting system message bus: dbus.
Starting rpcbind daemon...done.
Starting syslogd/klogd: done
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon ...done.

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
root@adsp-sc589-ezkit:~# 
```