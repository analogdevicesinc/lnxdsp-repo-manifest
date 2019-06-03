# IEEE 1588 PTP Testing
-----------------------------------

####Did not test with master/slave scenario, as I do not have two boards running yet.

Make sure testptp works sucessfully:
```
root@adsp-sc589-ezkit:~# date
Fri Jan  1 13:52:45 UTC 2010
root@adsp-sc589-ezkit:~# testptp -g
clock time: 0.000000000 or Thu Jan  1 00:00:00 1970
root@adsp-sc589-ezkit:~# testptp -s
set time okay
root@adsp-sc589-ezkit:~# testptp -g
clock time: 1262353976.969243784 or Fri Jan  1 13:52:56 2010
```

Make sure the other requisite tools are on system:
```
root@adsp-sc589-ezkit:~# hwstamp_ctl -v
1.8
root@adsp-sc589-ezkit:~# phc2sys -v
1.8
root@adsp-sc589-ezkit:~# ptp4l -v
1.8
```
