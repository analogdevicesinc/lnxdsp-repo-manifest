# USB1: Gadget Storage
-----------------------------------

Failed, lsusb is not showing a second usb port/hub:
```
root@adsp-sc589-ezkit:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
root@adsp-sc589-ezkit:~# dmesg | grep usb
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
usbcore: registered new interface driver usb-storage
musb-hdrc musb-hdrc.1.auto: MUSB HDRC host driver
musb-hdrc musb-hdrc.1.auto: new USB bus registered, assigned bus number 1
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
usbcore: registered new interface driver r8712u
```