Testing Status
=================

✓ = Pass

✗ = Fail

\- = Untested


|Testing Component|SC589-EZKit|SC584-EZKit|SC573-EZKit|SC589-Mini|Notes
|-|-|-|-|-|-|
|[Boot Log](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/BOOTLOG.md)|✓|-|-|-|Pass|
|[AD1979 Audio In Driver](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/AD1979.md)|✗|-|-|-|No hardware to test with
|[AD1962 Audio Out Driver](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/AD1962.md)|✗|-|-|-|No audio output heard
|ADV7842 video decoder driver|-|-|-|-|Untested
|ADV7343 video sd encoder driver|-|-|-|-|Untested
|ADV7511 video hd encoder driver|-|-|-|-|Untested
|Can bus driver|-|-|-|-|Untested
|[MCAPI framework - Multi Core Communication](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/MCC.md)|✓|-|-|-|Pass
|Clock control ( PLL,CCLK,SCLK)|-|-|-|-|Untested
|[CPU Frequency Control](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/CPUFREQ.md)|✓|-|-|-|Pass
|[CRC Check Using Crypto Framework](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/HMAC-CRC.md)|✓|-|-|-|Pass
|[DMA Copy](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/DMA_COPY.md)|✗|-|-|-|Failed
|[10/100 Ethernet](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/ETHERNET.md)|✓|-|-|-|Pass
|[Generic GPIO driver](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/GENERIC_GPIO.md)|✓|-|-|-|Pass
|[GPTimer Module](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/GPTIMER.md)|✓|-|-|-|Pass
|I2C soft switch through gpio|-|-|-|-|Untested
|[IEEE 1588 PTP](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/PTP.md)|✓|-|-|-|Pass, but did not check master/slave with two boards
|L2 alloc|-|-|-|-|Untested
|link port|-|-|-|-|Untested
|pcie RC driver|-|-|-|-|Untested
|pcie EP driver|-|-|-|-|Untested
|pincontrol driver|-|-|-|-|Untested
|Pound(funcload)|-|-|-|-|Untested
|RAM fs test|-|-|-|-|Untested
|Real Time Clock|-|-|-|-|Untested
|Serial NOR Flash MTD driver(dma)|-|-|-|-|Untested
|SDIO MMC driver|-|-|-|-|Untested
|timer|-|-|-|-|Untested
|TFT LCD nl8048 driver|-|-|-|-|Untested
|touchscreen over SPI|-|-|-|-|Untested
|UART serial core driver|-|-|-|-|Untested
|USB Tests|-|-|-|-|Untested
|[Watchdog](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/WATCHDOG.md)|✓|-|-|-|Pass|
|wireless network driver USB dongle|-|-|-|-|Untested
|LTP tests(WT/WB), (p2), (slob/slab)|-|-|-|-|Untested
|[MPlayer](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/MPLAYER.md)|✗|-|-|-|No LCD hardware to test
|[NFS File System](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/NFS_FILESYSTEM.md)|✓|-|-|-|Pass
|[OProfile / Whetstone](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/OPROFILE.md)|✓|-|-|-|Pass
|[Busybox FTPD](https://src.timesys.com/services/analog-devices/analog-devices-yocto-bsp-porting/meta-adi/tree/manifest/tests/adsp-sc589-ezkit/BUSYBOX_FTPD.md)|✓|-|-|-|Pass