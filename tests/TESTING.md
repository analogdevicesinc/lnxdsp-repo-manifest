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
|ADV7842 Video Decoder Driver|[✗](./adsp-sc589-ezkit/ADV7842.md)|Do not test|-|Do not test|No hardware to test with, "Unable to register sub device"
|ADV7343 Video SD Encoder Driver|[✗](./adsp-sc589-ezkit/ADV7343.md)|Do not test|-|Do not test|No hardware to test with, "Unable to register sub device"
|ADV7511 Video HD Encoder Driver|[✗](./adsp-sc589-ezkit/ADV7511.md)|Do not test|-|Do not test|No hardware to test with, "Unable to register sub device"
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
|TFT LCD NL8048 Driver|[✗](./adsp-sc589-ezkit/TFTLCD.md)|-|Do not test|Do not test|Failed
|SPI Touchscreen|[✗](./adsp-sc589-ezkit/TOUCH.md)|-|Do not test|Do not test|Failed
|UART/Serial Driver|[✓](./adsp-sc589-ezkit/UART.md)|-|-|-|Pass, but may need more exhaustive testing
|USB0: Host|[✗](./adsp-sc589-ezkit/USB0,HOST.md)|-|-|-|Works, but must first start as a device for some reason
|USB0: Device (Gadget Ethernet)|[✓](./adsp-sc589-ezkit/USB0,GADGETETH.md)|-|-|-|Untested
|USB0: Device (Gadget FS)|[✗](./adsp-sc589-ezkit/USB0,GADGETFS.md)|-|-|Do not test|Failed, "Connection timed out"
|USB0: Device (Gadget Audio)|[✓](./adsp-sc589-ezkit/USB0,GADGETAUDIO.md)|-|-|Do not test|Pass
|USB0: Device (Gadget Serial)|[✓](./adsp-sc589-ezkit/USB0,GADGETSERIAL.md)|-|-|-|Pass
|USB0: Device (Gadget Storage)|[✓](./adsp-sc589-ezkit/USB0,GADGETSTORAGE.md)|-|-|-|Pass
|USB0: Device (Gadget Zero)|[✓](./adsp-sc589-ezkit/USB0,GADGETZERO.md)|-|-|-|Pass
|USB1: Device (Gadget Storage)|[✗](./adsp-sc589-ezkit/USB1,GADGETSTORAGE.md)|Do not test|Do not test|Do not test|Failed, only USB0 is being instantiated
|USB1: Device (Gadget Zero)|[✗](./adsp-sc589-ezkit/USB1,GADGETZERO.md)|Do not test|Do not test|Do not test|Failed, only USB0 is being instantiated
|USB0: OTG Test|✓|-|-|-|Able to get port to work as host or device, see oddity under USB0: Host test though!
|USB Host Hotplug Test|✓|-|-|-|Pass, can plug/replug device
|USB Device Hotplug Test|✓|-|-|-|Pass can plug/replug cable from host
|USB2: OTG/host/device mode|✗|Do not test|Do not test|-|Do not see a third USB port on board, not sure how this is supposed to be tested
|Watchdog|[✓](./adsp-sc589-ezkit/WATCHDOG.md)|-|-|-|Pass|
|R8712U Wireless via USB|[✗](./adsp-sc589-ezkit/WIRELESS.md)|-|-|-|Fail, do not have R8712U USB dongle
|LTP tests(WT/WB), (p2), (slob/slab)|-|-|-|-|Untested
|MPlayer|[✗](./adsp-sc589-ezkit/MPLAYER.md)|-|Do not test|Do not test|No LCD hardware to test
|NFS File System|[✓](./adsp-sc589-ezkit/NFS_FILESYSTEM.md)|-|-|-|Pass
|OProfile / Whetstone|[✓](./adsp-sc589-ezkit/OPROFILE.md)|-|-|-|Pass
|Busybox FTPD|[✓](./adsp-sc589-ezkit/BUSYBOX_FTPD.md)|-|-|-|Pass