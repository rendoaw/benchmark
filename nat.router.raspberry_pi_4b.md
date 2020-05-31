## Raspberry PI 4B  as NAT Router Performance

### Test setup

* wired end to end

* native ethernet is facing to the server (uplink). USB 3.0 ethernet adapter is facing client. 


* connectivity

```
client -- Linksys switch -- raspberry pi 4b (router+nat) -- server
```


### Result 

#### Test #2: using TP-LINK dongle. Result is much better than tests #1

* TCP

```
# iperf3 -c 10.77.1.1
Connecting to host 10.77.1.1, port 5201
[  4] local 192.168.1.17 port 55668 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  91.9 MBytes   771 Mbits/sec  176    188 KBytes
[  4]   1.00-2.00   sec  87.7 MBytes   736 Mbits/sec  147    188 KBytes
[  4]   2.00-3.00   sec  91.3 MBytes   766 Mbits/sec  180    296 KBytes
[  4]   3.00-4.00   sec  93.7 MBytes   786 Mbits/sec    0    332 KBytes
[  4]   4.00-5.00   sec  91.3 MBytes   766 Mbits/sec   98    247 KBytes
[  4]   5.00-6.00   sec  92.2 MBytes   773 Mbits/sec   23    304 KBytes
[  4]   6.00-7.00   sec  91.8 MBytes   771 Mbits/sec    0    334 KBytes
[  4]   7.00-8.00   sec  91.7 MBytes   769 Mbits/sec  133    304 KBytes
[  4]   8.00-9.00   sec  94.0 MBytes   788 Mbits/sec    0    373 KBytes
[  4]   9.00-10.00  sec  93.3 MBytes   783 Mbits/sec   33    313 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   919 MBytes   771 Mbits/sec  790             sender
[  4]   0.00-10.00  sec   917 MBytes   769 Mbits/sec                  receiver
```

* UDP

```
```

#### Test #1: using anker usb 3.0 dongle

* TCP

```
# iperf3 -c 10.77.1.1
Connecting to host 10.77.1.1, port 5201
[  4] local 192.168.1.17 port 58596 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  33.7 MBytes   283 Mbits/sec  995   43.8 KBytes
[  4]   1.00-2.00   sec  33.4 MBytes   280 Mbits/sec  1185   48.1 KBytes
[  4]   2.00-3.00   sec  33.3 MBytes   279 Mbits/sec  1090   24.0 KBytes
[  4]   3.00-4.00   sec  33.9 MBytes   285 Mbits/sec  1153   32.5 KBytes
[  4]   4.00-5.00   sec  33.6 MBytes   282 Mbits/sec  1036   21.2 KBytes
[  4]   5.00-6.00   sec  33.9 MBytes   285 Mbits/sec  1124   43.8 KBytes
[  4]   6.00-7.00   sec  33.9 MBytes   284 Mbits/sec  1135   38.2 KBytes
[  4]   7.00-8.00   sec  33.6 MBytes   282 Mbits/sec  1021   36.8 KBytes
[  4]   8.00-9.00   sec  33.9 MBytes   285 Mbits/sec  1049   69.3 KBytes
[  4]   9.00-10.00  sec  33.8 MBytes   284 Mbits/sec  1168   38.2 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   337 MBytes   283 Mbits/sec  10956             sender
[  4]   0.00-10.00  sec   336 MBytes   282 Mbits/sec                  receiver
```

  * bottleneck is in usb3-ethernet dongle. Will re-test with new dongle. 


* UDP


```
need re-test. 
```


