## Marvell Espressonbin v5 as NAT Router Performance

### Test setup

* wired end to end

* Arch Linux

* Enabled features: snmp, netflow using pmacct, telegraf, vrrp using keepalived 

* connectivity

```
client -- Linksys switch -- Mikrotik RB750Gr3 as L2 switch -- espressobin (router+nat) -- server
```


### Result 

* TCP

```
# iperf3 -c 10.77.1.1
Connecting to host 10.77.1.1, port 5201
[  4] local 192.168.1.17 port 56746 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  27.4 MBytes   230 Mbits/sec   37    420 KBytes
[  4]   1.00-2.00   sec  26.5 MBytes   222 Mbits/sec    0    465 KBytes
[  4]   2.00-3.00   sec  27.5 MBytes   231 Mbits/sec    0    509 KBytes
[  4]   3.00-4.00   sec  27.4 MBytes   230 Mbits/sec    0    547 KBytes
[  4]   4.00-5.00   sec  27.2 MBytes   228 Mbits/sec    0    585 KBytes
[  4]   5.00-6.00   sec  26.0 MBytes   218 Mbits/sec    0    618 KBytes
[  4]   6.00-7.00   sec  27.2 MBytes   228 Mbits/sec    0    650 KBytes
[  4]   7.00-8.00   sec  27.8 MBytes   233 Mbits/sec    0    683 KBytes
[  4]   8.00-9.00   sec  27.5 MBytes   230 Mbits/sec    0    713 KBytes
[  4]   9.00-10.00  sec  27.5 MBytes   230 Mbits/sec   12    544 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   272 MBytes   228 Mbits/sec   49             sender
[  4]   0.00-10.00  sec   268 MBytes   225 Mbits/sec                  receiver

```

* UDP

```
need re-test.
```



