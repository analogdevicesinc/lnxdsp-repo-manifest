# RTC Testing
-----------------------------------

```
root@adsp-sc589-ezkit:~# rtc_test 
====== RTC Test  ====
0. open and release
opened '/dev/rtc0': fd = 3
1. ioctl RTC_UIE_ON
2. RTC read 5 times
RTC read 1
RTC read 2
RTC read 3
RTC read 4
RTC read 5
3. ioctl RTC_UIE_OFF
4. Get RTC Time
Current RTC date/time is 5-6-119, 15:54:23
5. Set RTC Time
Set Current RTC date/time to 31-5-104, 02:30:00
Get RTC time
Current RTC date/time is 31-5-104, 02:30:00
6. Set alarm Time
7. Get alarm Time
Alarm time now set to 02:30:50
Waiting 50 seconds for alarm...
 Okay. Alarm rang.
Current RTC date/time is 31-5-104, 02:30:50
8. ioctl RTC_AIE_OFF
8.5 test sleep 10
Current RTC date/time is 31-5-104, 02:31:00
Current RTC date/time is 31-5-104, 02:31:00
RTC Tests done !!
```