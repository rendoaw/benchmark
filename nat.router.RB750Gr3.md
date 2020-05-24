## RB750Gr3 as NAT Router Performance

### Test setup

* wired end to end

* Feature enabled: snmp, netflow v5, vrrp

* connectivity

```
client -- Linksys switch -- Mikrotik RB750Gr3 as switch+router+nat -- server
```


### Result 

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
# iperf3 -c 10.77.1.1 -u -b 1G
Connecting to host 10.77.1.1, port 5201
[  4] local 192.168.1.17 port 43254 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Total Datagrams
[  4]   0.00-1.00   sec   101 MBytes   850 Mbits/sec  12976
[  4]   1.00-2.00   sec   112 MBytes   936 Mbits/sec  14277
[  4]   2.00-3.00   sec   112 MBytes   938 Mbits/sec  14317
[  4]   3.00-4.00   sec   112 MBytes   942 Mbits/sec  14378
[  4]   4.00-5.00   sec   112 MBytes   939 Mbits/sec  14330
[  4]   5.00-6.00   sec   112 MBytes   941 Mbits/sec  14352
[  4]   6.00-7.00   sec   111 MBytes   932 Mbits/sec  14218
[  4]   7.00-8.00   sec   112 MBytes   941 Mbits/sec  14353
[  4]   8.00-9.00   sec   112 MBytes   942 Mbits/sec  14370
[  4]   9.00-10.00  sec   113 MBytes   945 Mbits/sec  14420
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Jitter    Lost/Total Datagrams
[  4]   0.00-10.00  sec  1.08 GBytes   931 Mbits/sec  0.124 ms  69338/141958 (49%)
[  4] Sent 141958 datagrams

```


