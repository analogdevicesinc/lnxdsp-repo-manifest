Testing Status
=================

[✓] = Pass

[✗] = Fail

\- = Untested


|Testing Component|SC589-EZKit|SC584-EZKit|SC573-EZKit|SC589-Mini|Notes
|-|-|-|-|-|-|
|Boot Log|[✓](./adsp-sc589-ezkit/BOOTLOG.md)|-|-|-|Pass|
|AD1979 Audio In Driver|[✗](./adsp-sc589-ezkit/AD1979.md)|-|-|Do not test|No hardware to test with
|AD1962 Audio Out Driver|[✗](./adsp-sc589-ezkit/AD1962.md)|-|-|Do not test|No audio output heard
|ADV7842 video decoder driver|-|Do not test|-|Do not test|Untested
|ADV7343 video sd encoder driver|-|Do not test|-|Do not test|Untested
|ADV7511 video hd encoder driver|-|Do not test|-|Do not test|Untested
|Can bus driver|-|-|-|Do not test|Untested
|MCAPI framework - Multi Core Communication|[✓](./adsp-sc589-ezkit/MCC.md)|-|-|-|Pass
|Clock control (PLL,CCLK,SCLK)|[✓](./adsp-sc589-ezkit/CLKCTL.md)|-|-|-|Pass
|CPU Frequency Control|[✓](./adsp-sc589-ezkit/CPUFREQ.md)|-|-|-|Pass
|CRC Check Using Crypto Framework|[✓](./adsp-sc589-ezkit/HMAC-CRC.md)|-|-|-|Pass
|DMA Copy|[✗](./adsp-sc589-ezkit/DMA_COPY.md)|-|-|-|Failed
|10/100 Ethernet|[✓](./adsp-sc589-ezkit/ETHERNET.md)|-|-|-|Pass
|Generic GPIO driver|[✓](./adsp-sc589-ezkit/GENERIC_GPIO.md)|-|-|-|Pass
|GPTimer Module|[✓](./adsp-sc589-ezkit/GPTIMER.md)|-|-|-|Pass
|I2C Soft Switch Expander|[✓](./adsp-sc589-ezkit/I2CEXPANDER.md)|-|-|Do not test|Pass
|IEEE 1588 PTP|[✓](./adsp-sc589-ezkit/PTP.md)|-|-|-|Pass, but did not check master/slave with two boards
|L2 alloc|[✗](./adsp-sc589-ezkit/L2ALLOC.md)|-|-|-|Unsure if outputs make sense
|Link Port|[✗](./adsp-sc589-ezkit/LINKPORT.md)|-|-|Do not test|Test failed, may not have correct cable to loopback
|PCIE RC Driver|[✗](./adsp-sc589-ezkit/PCIE_RC.md)|Do not test|Do not test|Do not test|Failed
|PCIE EP Driver|[✗](./adsp-sc589-ezkit/PCIE_EP.md)|Do not test|Do not test|Do not test|Failed
|PF Button Driver|Do not test|Do not test|Do not test|-|Untested
|Pin Control Driver|[✓](./adsp-sc589-ezkit/PINCTRL.md)|-|-|-|Pass
|Pound / Funk Load|[✓](./adsp-sc589-ezkit/POUND.md)|-|-|-|Pass
|RAM FS Test|[✓](./adsp-sc589-ezkit/RAMDISK.md)|-|-|-|Pass
|Real Time Clock|[✓](./adsp-sc589-ezkit/RTC.md)|-|-|Do not test|Pass
|Rotary Input Device Driver|Do not test|-|-|Do not test|Untested
|Serial NOR Flash MTD Driver|[✗](./adsp-sc589-ezkit/NOR.md)|-|-|-|Failed
|SDIO MMC Driver|[✓](./adsp-sc589-ezkit/SDIOMMC.md)|Do not test|-|-|Pass
|Timer|[✓](./adsp-sc589-ezkit/TIMER.md)|-|-|-|Pass
|TFT LCD nl8048 driver|-|-|Do not test|Do not test|Untested
|touchscreen over SPI|-|-|Do not test|Do not test|Untested
|UART serial core driver|-|-|-|-|Untested
|USB Tests|-|-|-|-|Untested
|Watchdog|[✓](./adsp-sc589-ezkit/WATCHDOG.md)|-|-|-|Pass|
|wireless network driver USB dongle|-|-|-|-|Untested
|LTP tests(WT/WB), (p2), (slob/slab)|-|-|-|-|Untested
|MPlayer|[✗](./adsp-sc589-ezkit/MPLAYER.md)|-|Do not test|Do not test|No LCD hardware to test
|NFS File System|[✓](./adsp-sc589-ezkit/NFS_FILESYSTEM.md)|-|-|-|Pass
|OProfile / Whetstone|[✓](./adsp-sc589-ezkit/OPROFILE.md)|-|-|-|Pass
|Busybox FTPD|[✓](./adsp-sc589-ezkit/BUSYBOX_FTPD.md)|-|-|-|Pass