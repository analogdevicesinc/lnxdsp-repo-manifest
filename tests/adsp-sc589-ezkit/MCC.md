# Multi-Core Communication Testing
-----------------------------------

From CCES, compile and launch mcapi_send_recv_Core1_sc589.dxe in suspended mode (no core 0 / core 2 applications)
```
root@adsp-sc589-ezkit:~# cat /proc/version
Linux version 4.16.0 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 Tue May 7 17:57:54 UTC 2019
```

```
root@adsp-sc589-ezkit:~# corecontrol --start 1
Test core 1 start
Test core 1 end: 0
```

Resume from within CCES, then start the Linux side:

```
root@adsp-sc589-ezkit:~# arm_sharc_msg_demo
semget
CHECK_STATUS---initialize:MCAPI_SUCCESS
 node=0, port=101
CHECK_STATUS---create_ep:MCAPI_SUCCESS
ep1 65   
CHECK_STATUS---get_ep_i:MCAPI_PENDING
 node=1, port=5
CHECK_STATUS---wait:MCAPI_SUCCESS
ep2 10005   
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 0]
Core0: mode(0) message send. The 0 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 1]
Core0: mode(0) message recv. The 0 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 1]
Core0: mode(0) message send. The 1 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 2]
Core0: mode(0) message recv. The 1 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 2]
Core0: mode(0) message send. The 2 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 3]
Core0: mode(0) message recv. The 2 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 3]
Core0: mode(0) message send. The 3 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 4]
Core0: mode(0) message recv. The 3 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 4]
Core0: mode(0) message send. The 4 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 5]
Core0: mode(0) message recv. The 4 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 5]
Core0: mode(0) message send. The 5 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 6]
Core0: mode(0) message recv. The 5 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 6]
Core0: mode(0) message send. The 6 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 7]
Core0: mode(0) message recv. The 6 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 7]
Core0: mode(0) message send. The 7 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 8]
Core0: mode(0) message recv. The 7 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 8]
Core0: mode(0) message send. The 8 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x13 has received: [hello mcapi core1 9]
Core0: mode(0) message recv. The 8 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 9]
Core0: mode(0) message send. The 9 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 10]
Core0: mode(0) message recv. The 9 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 10]
Core0: mode(0) message send. The 10 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 11]
Core0: mode(0) message recv. The 10 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 11]
Core0: mode(0) message send. The 11 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 12]
Core0: mode(0) message recv. The 11 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 12]
Core0: mode(0) message send. The 12 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 13]
Core0: mode(0) message recv. The 12 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 13]
Core0: mode(0) message send. The 13 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 14]
Core0: mode(0) message recv. The 13 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 14]
Core0: mode(0) message send. The 14 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 15]
Core0: mode(0) message recv. The 14 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 15]
Core0: mode(0) message send. The 15 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 16]
Core0: mode(0) message recv. The 15 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 16]
Core0: mode(0) message send. The 16 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 17]
Core0: mode(0) message recv. The 16 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 17]
Core0: mode(0) message send. The 17 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 18]
Core0: mode(0) message recv. The 17 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 18]
Core0: mode(0) message send. The 18 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 19]
Core0: mode(0) message recv. The 18 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 19]
Core0: mode(0) message send. The 19 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 20]
Core0: mode(0) message recv. The 19 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 20]
Core0: mode(0) message send. The 20 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 21]
Core0: mode(0) message recv. The 20 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 21]
Core0: mode(0) message send. The 21 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 22]
Core0: mode(0) message recv. The 21 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 22]
Core0: mode(0) message send. The 22 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 23]
Core0: mode(0) message recv. The 22 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 23]
Core0: mode(0) message send. The 23 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 24]
Core0: mode(0) message recv. The 23 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 24]
Core0: mode(0) message send. The 24 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 25]
Core0: mode(0) message recv. The 24 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 25]
Core0: mode(0) message send. The 25 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 26]
Core0: mode(0) message recv. The 25 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 26]
Core0: mode(0) message send. The 26 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 27]
Core0: mode(0) message recv. The 26 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 27]
Core0: mode(0) message send. The 27 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 28]
Core0: mode(0) message recv. The 27 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 28]
Core0: mode(0) message send. The 28 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 29]
Core0: mode(0) message recv. The 28 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 29]
Core0: mode(0) message send. The 29 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 30]
Core0: mode(0) message recv. The 29 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 30]
Core0: mode(0) message send. The 30 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 31]
Core0: mode(0) message recv. The 30 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 31]
Core0: mode(0) message send. The 31 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 32]
Core0: mode(0) message recv. The 31 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 32]
Core0: mode(0) message send. The 32 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 33]
Core0: mode(0) message recv. The 32 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 33]
Core0: mode(0) message send. The 33 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 34]
Core0: mode(0) message recv. The 33 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 34]
Core0: mode(0) message send. The 34 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 35]
Core0: mode(0) message recv. The 34 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 35]
Core0: mode(0) message send. The 35 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 36]
Core0: mode(0) message recv. The 35 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 36]
Core0: mode(0) message send. The 36 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 37]
Core0: mode(0) message recv. The 36 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 37]
Core0: mode(0) message send. The 37 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 38]
Core0: mode(0) message recv. The 37 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 38]
Core0: mode(0) message send. The 38 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 39]
Core0: mode(0) message recv. The 38 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 39]
Core0: mode(0) message send. The 39 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 40]
Core0: mode(0) message recv. The 39 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 40]
Core0: mode(0) message send. The 40 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 41]
Core0: mode(0) message recv. The 40 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 41]
Core0: mode(0) message send. The 41 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 42]
Core0: mode(0) message recv. The 41 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 42]
Core0: mode(0) message send. The 42 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 43]
Core0: mode(0) message recv. The 42 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 43]
Core0: mode(0) message send. The 43 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 44]
Core0: mode(0) message recv. The 43 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 44]
Core0: mode(0) message send. The 44 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 45]
Core0: mode(0) message recv. The 44 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 45]
Core0: mode(0) message send. The 45 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 46]
Core0: mode(0) message recv. The 45 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 46]
Core0: mode(0) message send. The 46 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 47]
Core0: mode(0) message recv. The 46 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 47]
Core0: mode(0) message send. The 47 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 48]
Core0: mode(0) message recv. The 47 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 48]
Core0: mode(0) message send. The 48 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 49]
Core0: mode(0) message recv. The 48 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 49]
Core0: mode(0) message send. The 49 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 50]
Core0: mode(0) message recv. The 49 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 50]
Core0: mode(0) message send. The 50 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 51]
Core0: mode(0) message recv. The 50 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 51]
Core0: mode(0) message send. The 51 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 52]
Core0: mode(0) message recv. The 51 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 52]
Core0: mode(0) message send. The 52 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 53]
Core0: mode(0) message recv. The 52 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 53]
Core0: mode(0) message send. The 53 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 54]
Core0: mode(0) message recv. The 53 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 54]
Core0: mode(0) message send. The 54 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 55]
Core0: mode(0) message recv. The 54 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 55]
Core0: mode(0) message send. The 55 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 56]
Core0: mode(0) message recv. The 55 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 56]
Core0: mode(0) message send. The 56 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 57]
Core0: mode(0) message recv. The 56 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 57]
Core0: mode(0) message send. The 57 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 58]
Core0: mode(0) message recv. The 57 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 58]
Core0: mode(0) message send. The 58 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 59]
Core0: mode(0) message recv. The 58 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 59]
Core0: mode(0) message send. The 59 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 60]
Core0: mode(0) message recv. The 59 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 60]
Core0: mode(0) message send. The 60 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 61]
Core0: mode(0) message recv. The 60 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 61]
Core0: mode(0) message send. The 61 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 62]
Core0: mode(0) message recv. The 61 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 62]
Core0: mode(0) message send. The 62 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 63]
Core0: mode(0) message recv. The 62 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 63]
Core0: mode(0) message send. The 63 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 64]
Core0: mode(0) message recv. The 63 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 64]
Core0: mode(0) message send. The 64 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 65]
Core0: mode(0) message recv. The 64 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 65]
Core0: mode(0) message send. The 65 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 66]
Core0: mode(0) message recv. The 65 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 66]
Core0: mode(0) message send. The 66 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 67]
Core0: mode(0) message recv. The 66 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 67]
Core0: mode(0) message send. The 67 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 68]
Core0: mode(0) message recv. The 67 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 68]
Core0: mode(0) message send. The 68 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 69]
Core0: mode(0) message recv. The 68 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 69]
Core0: mode(0) message send. The 69 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 70]
Core0: mode(0) message recv. The 69 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 70]
Core0: mode(0) message send. The 70 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 71]
Core0: mode(0) message recv. The 70 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 71]
Core0: mode(0) message send. The 71 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 72]
Core0: mode(0) message recv. The 71 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 72]
Core0: mode(0) message send. The 72 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 73]
Core0: mode(0) message recv. The 72 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 73]
Core0: mode(0) message send. The 73 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 74]
Core0: mode(0) message recv. The 73 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 74]
Core0: mode(0) message send. The 74 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 75]
Core0: mode(0) message recv. The 74 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 75]
Core0: mode(0) message send. The 75 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 76]
Core0: mode(0) message recv. The 75 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 76]
Core0: mode(0) message send. The 76 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 77]
Core0: mode(0) message recv. The 76 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 77]
Core0: mode(0) message send. The 77 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 78]
Core0: mode(0) message recv. The 77 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 78]
Core0: mode(0) message send. The 78 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 79]
Core0: mode(0) message recv. The 78 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 79]
Core0: mode(0) message send. The 79 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 80]
Core0: mode(0) message recv. The 79 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 80]
Core0: mode(0) message send. The 80 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 81]
Core0: mode(0) message recv. The 80 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 81]
Core0: mode(0) message send. The 81 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 82]
Core0: mode(0) message recv. The 81 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 82]
Core0: mode(0) message send. The 82 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 83]
Core0: mode(0) message recv. The 82 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 83]
Core0: mode(0) message send. The 83 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 84]
Core0: mode(0) message recv. The 83 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 84]
Core0: mode(0) message send. The 84 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 85]
Core0: mode(0) message recv. The 84 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 85]
Core0: mode(0) message send. The 85 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 86]
Core0: mode(0) message recv. The 85 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 86]
Core0: mode(0) message send. The 86 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 87]
Core0: mode(0) message recv. The 86 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 87]
Core0: mode(0) message send. The 87 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 88]
Core0: mode(0) message recv. The 87 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 88]
Core0: mode(0) message send. The 88 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 89]
Core0: mode(0) message recv. The 88 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 89]
Core0: mode(0) message send. The 89 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 90]
Core0: mode(0) message recv. The 89 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 90]
Core0: mode(0) message send. The 90 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 91]
Core0: mode(0) message recv. The 90 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 91]
Core0: mode(0) message send. The 91 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 92]
Core0: mode(0) message recv. The 91 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 92]
Core0: mode(0) message send. The 92 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 93]
Core0: mode(0) message recv. The 92 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 93]
Core0: mode(0) message send. The 93 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 94]
Core0: mode(0) message recv. The 93 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 94]
Core0: mode(0) message send. The 94 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 95]
Core0: mode(0) message recv. The 94 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 95]
Core0: mode(0) message send. The 95 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 96]
Core0: mode(0) message recv. The 95 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 96]
Core0: mode(0) message send. The 96 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 97]
Core0: mode(0) message recv. The 96 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 97]
Core0: mode(0) message send. The 97 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 98]
Core0: mode(0) message recv. The 97 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 98]
Core0: mode(0) message send. The 98 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x14 has received: [hello mcapi core1 99]
Core0: mode(0) message recv. The 98 time receiving
send() start......
CHECK_STATUS---send_i:MCAPI_PENDING
CHECK_STATUS---test:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of send() - endpoint=101 has sent: [hello mcapi core0 99]
Core0: mode(0) message send. The 99 time sending
recv() start......
CHECK_STATUS---available:MCAPI_SUCCESS
 node=1, port=5
CHECK_STATUS---recv_i:MCAPI_SUCCESS
CHECK_STATUS---wait:MCAPI_SUCCESS
end of recv() - endpoint=101 size 0x15 has received: [hello mcapi core1 100]
Core0: mode(0) message recv. The 99 time receiving
CHECK_STATUS---del_ep:MCAPI_SUCCESS
mcapi_finalize 322
CHECK_STATUS---finalize:MCAPI_SUCCESS
Core0 100 rounds mode(0) demo Test PASSED!!
```