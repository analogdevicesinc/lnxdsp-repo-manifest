# UART Testing
-----------------------------------

I am able to communicate through the FTDI USB/Serial transceiver in both U-boot and the Linux kernel


```
U-Boot 2015.01 ADI-1.3.0 (May 13 2019 - 14:52:08)

CPU:   ADSP ADSP-SC589-0.1 (Detected Rev: 1.1) (spi flash boot)
VCO: 450 MHz, Cclk0: 450 MHz, Sclk0: 112.500 MHz, Sclk1: 112.500 MHz, DCLK: 450 MHz
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
Hit any key to stop autoboot:  0 
sc # 
sc # version

U-Boot 2015.01 ADI-1.3.0 (May 13 2019 - 14:52:08)
arm-poky-linux-gnueabi-gcc (GCC) 8.2.0
GNU ld (GNU Binutils) 2.31.1.20181224
```

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
     
root@adsp-sc589-ezkit:~# dmesg | grep UART
adi-uart4.0: ttySC0 at MMIO 0x31003000 (irq = 21, base_baud = 7031250) is a ADI-UART4

root@adsp-sc589-ezkit:~# version
kernel:    Linux release 4.16.0, build #1 Wed Jun 5 13:07:36 UTC 2019
toolchain: arm-poky-linux-gnueabi-gcc -march=armv7-a -mthumb -mfpu=neon -mfloat-abi=hard -fstack-protector-strong -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=/mnt/NVME/Projects/AnalogDevices/yocto/tmp/work/armv7at2hf-neon-poky-linux-gnueabi/version/1.0-r0/recipe-sysroot release gcc version 8.2.0 (GCC) 
user-dist: release , build #1 Fri Jun 7 15:15:05 UTC 2019
```
