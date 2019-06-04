# L2 Alloc Testing
-----------------------------------

Must set following in conf/local.conf
```
ANALOG_DEVICES_SRAM_ALLOC="1"
```

Do these addresses make sense?
```
root@adsp-sc589-ezkit:~# modprobe hello_l2_alloc
hello_l2_alloc: loading out-of-tree module taints kernel.
=====alloc address is 0d807655 =======
=====alloc address is a88dd9c7 =======
=====alloc address is db5375f5 =======
=====alloc address is 8f2d54c2 =======
=====alloc address is 076adb80 =======
=====alloc address is b4ba41f6 =======
=====alloc address is fd047d87 =======
=====alloc address is d55e2236 =======
=====alloc address is 6bd34ae5 =======
=====alloc address is 148bce42 =======
======== hello_l2_alloc module finished. =======
```

Do these addresses make sense?
```
root@adsp-sc589-ezkit:~# modprobe hello
========Load module into L2 memory========
L2 Code test: code function addr = 0xf86e1445
L2 data A test: data variable addr = 0xf832e698, data value is 0
L2 BSS  bank A test: bss  variable addr = 0xd8aca450, bss value is 0
```
