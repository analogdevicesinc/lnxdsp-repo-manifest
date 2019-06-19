# USB0: Gadget FS
-----------------------------------

Start usbtest module on host machine:
```
nathan@Debian-BuildMachine:$ sudo modprobe usbtest
nathan@Debian-BuildMachine:$ lsmod | grep usbtest
usbtest                36864  0
usbcore               253952  12 usbnet,ehci_hcd,cdc_ether,ohci_pci,ftdi_sio,usbserial,cdc_subset,xhci_pci,ohci_hcd,usbtest,xhci_hcd,ehci_pci
usb_common             16384  2 usbcore,usbtest
```

Start test from target machine:
```
root@adsp-sc589-ezkit:/# gadgetfs-test -r "1.3" -v
gadgetfs: bound to musb-hdrc driver
/dev/gadget/musb-hdrc ep0 configured
serial="1.3"
gadgetfs: connected

** Wed Jun 19 13:56:32 2019gadgetfs: disconnected

CONNECT high speed
DISCONNECT
gadgetfs: connected
CONNECT high speedgadgetfs: configuration #3

SETUP 80.06 v0300 i0000 255
SETUP 80.06 v0302 i0409 255
SETUP 80.06 v0301 i0409 255
SETUP 80.06 v0303 i0409 255
SETUP 00.09 v0003 i0000 0
CONFIG #3
simple_sink_thread start -1235360672 fd 4
SETUP 80.06 v0304 i0409 255
simple_source_thread start -1226967968 fd 5
SETUP 80.06 v0305 i0409 255
SETUP 01.0b v0000 i0000 0
```

See if device shows up on host machine:
```
nathan@Debian-BuildMachine:$ sudo cat /sys/kernel/debug/usb/devices | grep -5 Licensed
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0525 ProdID=a4a4 Rev= 1.07
S:  Manufacturer=Licensed to Code, LLC
S:  Product=My Source/Sink Product
S:  SerialNumber=1.3
C:* #Ifs= 1 Cfg#= 3 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=usbtest
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
```

See if device shows up on host machine:
```
nathan@Debian-BuildMachine:$ lsusb|grep -i "Netchip Technology"
Bus 003 Device 004: ID 0525:a4a4 Netchip Technology, Inc. Linux-USB user-mode bulk source/sink
```

Run testusb from host machine:
```
nathan@Debian-BuildMachine:$ sudo ./testusb -D /dev/bus/usb/003/004 -t9
./testusb: /dev/bus/usb/003/004 may see only control tests
/dev/bus/usb/003/004 test 9 --> 110 (Connection timed out)
```

Fails with this error:
```
root@adsp-sc589-ezkit:/#
musb_g_ep0_irq 687: SetupEnd came in a wrong ep0stage wait
```










