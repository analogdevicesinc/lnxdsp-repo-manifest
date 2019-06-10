# USB0: Gadget Serial
-----------------------------------

Probe g_serial driver
```
root@adsp-sc589-ezkit:~# modprobe g_serial
g_serial gadget: Gadget Serial v2.4
g_serial gadget: g_serial ready
```

Plug in USB cable:
```
root@adsp-sc589-ezkit:
g_serial gadget: high-speed config #1: Generic Serial config
root@adsp-sc589-ezkit:~# ls /dev/ttyGS*
/dev/ttyGS0
```


Test sending data from host machine to target machine:

From target machine:
```
root@adsp-sc589-ezkit:~# cat /dev/ttyGS0
test

test

test
```

From host machine:
```
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
```

Test sending data from target machine to host machine:

From host machine:
```
nathan@Debian-BuildMachine:~$ cat /dev/ttyACM0
test

test

test
```

From target machine:
```
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
root@adsp-sc589-ezkit:~# echo "test" > /dev/ttyGS0
```
