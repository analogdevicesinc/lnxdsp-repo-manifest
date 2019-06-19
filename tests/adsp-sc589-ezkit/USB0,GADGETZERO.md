# USB0: Gadget Zero
-----------------------------------

Start usbtest module on host machine:
```
nathan@Debian-BuildMachine:$ sudo modprobe usbtest
nathan@Debian-BuildMachine:$ lsmod | grep usbtest
usbtest                36864  0
usbcore               253952  12 usbnet,ehci_hcd,cdc_ether,ohci_pci,ftdi_sio,usbserial,cdc_subset,xhci_pci,ohci_hcd,usbtest,xhci_hcd,ehci_pci
usb_common             16384  2 usbcore,usbtest
```

Probe the driver from target
```
root@adsp-sc589-ezkit:~# modprobe g_zero
zero gadget: Gadget Zero, version: Cinco de Mayo 2008
zero gadget: zero ready
root@adsp-sc589-ezkit:~# zero gadget: high-speed config #3: source/sink
```

Check if device enumerates on host:
```
nathan@Debian-BuildMachine:$ sudo cat /sys/kernel/debug/usb/devices | grep Zero
S:  Product=Gadget Zero

nathan@Debian-BuildMachine:$ lsusb | grep Gadget
Bus 003 Device 006: ID 0525:a4a0 Netchip Technology, Inc. Linux-USB "Gadget Zero"
```

Run the tests from host:
```
nathan@Debian-BuildMachine:$ sudo ./testusb -D /dev/bus/usb/003/006 -t 9unknown speed	/dev/bus/usb/003/006	0
/dev/bus/usb/003/006 test 9,    2.263172 secs
nathan@Debian-BuildMachine:$ sudo ./testusb -D /dev/bus/usb/003/006 -t 10unknown speed	/dev/bus/usb/003/006	0
/dev/bus/usb/003/006 test 10,    3.453821 secs
nathan@Debian-BuildMachine:$ sudo ./testusb -D /dev/bus/usb/003/006 -t 14 -c 15000 -s 256 -v 1
unknown speed	/dev/bus/usb/003/006	0
/dev/bus/usb/003/006 test 14,    4.450433 secs
```


