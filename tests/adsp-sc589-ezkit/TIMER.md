# Timer Testing
-----------------------------------

Kernel is running with:
```
CONFIG_HZ_250=y
```

Run the test:
```
cat /proc/uptime
cat /proc/interrupts | grep GPTimer0
sleep 5
cat /proc/uptime
cat /proc/interrupts | grep GPTimer0
```

Outputs from test:
```
root@adsp-sc589-ezkit:~# 
root@adsp-sc589-ezkit:~# cat /proc/uptime
2522.40 2500.63
root@adsp-sc589-ezkit:~# cat /proc/interrupts | grep GPTimer0
me
cat /proc/interrupts | grep GPTimer0
 17:     630443     GIC-0  58 Edge      SC58x GPTimer0
root@adsp-sc589-ezkit:~# sleep 5
root@adsp-sc589-ezkit:~# cat /proc/uptime
2527.46 2505.63
root@adsp-sc589-ezkit:~# cat /proc/interrupts | grep GPTimer0
 17:     631707     GIC-0  58 Edge      SC58x GPTimer0
```

This is within CONFIG_HZ_250 +/- 25Hz (249.8 Hz):
```
2527.46 - 2522.40 = 5.06
631707-630443 = 1264
TIMER_TICK_AVERAGE = 1264/5.06 = 249.8
```
