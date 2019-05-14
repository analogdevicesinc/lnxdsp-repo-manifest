
# Netperf Client Test
-----------------------------------

Run a server from a host Linux machine
```
# sudo apt-get install netperf
# sudo service netperf restart
# ps -ef | grep netserver
root     23948  1045  0 12:05 ?        00:00:00 netserver
```

Perform a 100 second netperf test from the SC5xx processor:
```
root@adsp-sc589-ezkit:~# export SERVER_IP=x.x.x.x
root@adsp-sc589-ezkit:~# netperf -H ${SERVER_IP} -p 12865 -l 100
	MIGRATED TCP STREAM TEST from 0.0.0.0 () port 0 AF_INET to ${SERVER_IP} () port 0 AF_INET
	Recv   Send    Send                          
	Socket Socket  Message  Elapsed              
	Size   Size    Size     Time     Throughput  
	bytes  bytes   bytes    secs.    10^6bits/sec  

	 87380  16384  16384    100.04    314.45 
```

# Netperf Server Test
-----------------------------------

Run a server from the SC5xx processor:
```
root@adsp-sc589-ezkit:~# /etc/init.d/netperf restart
	stopped /usr/sbin/netserver (pid 905)
	Starting netserver with host 'IN(6)ADDR_ANY' port '12865' and family AF_UNSPEC
root@adsp-sc589-ezkit:~# ps | grep netserver
	963 root     /usr/sbin/netserver

```

Perform a 100 second netperf test from the host Linux machine:
```
# export SERVER_IP=x.x.x.x
# netperf -H ${SERVER_IP} -p 12865 -l 100
	MIGRATED TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to ${SERVER_IP} () port 0 AF_INET : demo
	Recv   Send    Send                          
	Socket Socket  Message  Elapsed              
	Size   Size    Size     Time     Throughput  
	bytes  bytes   bytes    secs.    10^6bits/sec  

	 87380  16384  16384    10.22      15.59 
```
