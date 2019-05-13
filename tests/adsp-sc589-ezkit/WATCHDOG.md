# Watchdog Testing
-----------------------------------

Build and flash u-boot with the following line in build/conf/local.conf

```
ANALOG_DEVICES_WATCHDOG="1"
```

Boot up in to root file system and ensure watchdog daemon and application are running:
```
root@adsp-sc589-ezkit:~# ps | grep watchdog
  404 root     [watchdogd]
  813 root     /sbin/watchdog -t 1 /dev/watchdog
```

Kill the watchdog and watch the board reset after some time:
```
root@adsp-sc589-ezkit:~# /etc/init.d/watchdog.sh stop
Stopping watchdog...
watchdog: watchdog0: watchdog did not stop!

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

```

Read an illegal address from U-boot and ensure the board also resets after some time:
```
sc # md.w 0xff30ffff
ff30ffff:data abort
pc : [<cff8c6e4>]          lr : [<cff8c63c>]
sp : cfe5fcf8  ip : 00000001     fp : ff30ffff
r10: 00000008  r9 : cfe5ff08     r8 : ff30ffff
r7 : 00000000  r6 : 00000002     r5 : 00000008  r4 : 00000040
r3 : cfe5fd14  r2 : 00000000     r1 : 00000000  r0 : 00000009
Flags: nZCv  IRQs off  FIQs off  Mode SVC_32
Resetting CPU ...

### ERROR ### Please RESET the board ###


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
```