## Raspberry PI 4B  as NAT Router Performance

### Test setup

* wired end to end

* connectivity

```
client -- Linksys switch -- raspberry pi 4b (router+nat) -- server
```


### Result 

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

* UDP

```
# iperf3 -c 10.77.1.1 -u -b 1G
Connecting to host 10.77.1.1, port 5201
[  4] local 192.168.1.17 port 52116 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Total Datagrams
[  4]   0.00-1.00   sec  97.2 MBytes   816 Mbits/sec  12445
[  4]   1.00-2.00   sec   112 MBytes   941 Mbits/sec  14352
[  4]   2.00-3.00   sec   112 MBytes   943 Mbits/sec  14394
[  4]   3.00-4.00   sec   112 MBytes   943 Mbits/sec  14392
[  4]   4.00-5.00   sec   113 MBytes   949 Mbits/sec  14480
[  4]   5.00-6.00   sec   113 MBytes   949 Mbits/sec  14486
[  4]   6.00-7.00   sec   113 MBytes   947 Mbits/sec  14446
[  4]   7.00-8.00   sec   113 MBytes   950 Mbits/sec  14488
[  4]   8.00-9.00   sec   113 MBytes   947 Mbits/sec  14445
[  4]   9.00-10.00  sec   113 MBytes   948 Mbits/sec  14461
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Jitter    Lost/Total Datagrams
[  4]   0.00-10.00  sec  1.09 GBytes   933 Mbits/sec  0.265 ms  5605/7910 (71%)
[  4] Sent 7910 datagrams
```


