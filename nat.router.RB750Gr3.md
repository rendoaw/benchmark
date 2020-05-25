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
needd re-test
```


