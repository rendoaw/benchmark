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
[  5] local 192.168.1.17 port 33504 connected to 10.77.1.1 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  88.6 MBytes   744 Mbits/sec    0    619 KBytes
[  5]   1.00-2.00   sec  91.1 MBytes   764 Mbits/sec    0    648 KBytes
[  5]   2.00-3.00   sec  90.0 MBytes   755 Mbits/sec    0    710 KBytes
[  5]   3.00-4.00   sec  90.0 MBytes   755 Mbits/sec    0    710 KBytes
[  5]   4.00-5.00   sec  88.8 MBytes   744 Mbits/sec    0    710 KBytes
[  5]   5.00-6.00   sec  90.0 MBytes   755 Mbits/sec    0    742 KBytes
[  5]   6.00-7.00   sec  88.8 MBytes   744 Mbits/sec    0    779 KBytes
[  5]   7.00-8.00   sec  90.0 MBytes   755 Mbits/sec    0    779 KBytes
[  5]   8.00-9.00   sec  88.8 MBytes   744 Mbits/sec    0    817 KBytes
[  5]   9.00-10.00  sec  90.0 MBytes   755 Mbits/sec    0    868 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec   896 MBytes   752 Mbits/sec    0             sender
[  5]   0.00-10.00  sec   892 MBytes   748 Mbits/sec                  receiver
```

* UDP

result still strange. 

```
### after NAT --> measured on server after NAT

Accepted connection from 10.77.1.30, port 38230
[  5] local 10.77.1.1 port 5202 connected to 10.77.1.30 port 57845
[ ID] Interval           Transfer     Bitrate         Jitter    Lost/Total Datagrams
[  5]   0.00-1.00   sec  19.2 MBytes   161 Mbits/sec  0.119 ms  60272/74142 (81%)
[  5]   1.00-2.00   sec  20.0 MBytes   168 Mbits/sec  0.123 ms  67458/81936 (82%)
[  5]   2.00-3.00   sec  20.0 MBytes   168 Mbits/sec  0.059 ms  67386/81887 (82%)
[  5]   3.00-4.00   sec  20.0 MBytes   168 Mbits/sec  0.052 ms  67502/81964 (82%)
[  5]   4.00-5.00   sec  20.0 MBytes   167 Mbits/sec  0.049 ms  67471/81919 (82%)
[  5]   5.00-6.00   sec  20.0 MBytes   168 Mbits/sec  0.175 ms  67534/81997 (82%)
[  5]   6.00-7.00   sec  20.0 MBytes   168 Mbits/sec  0.088 ms  67439/81900 (82%)
[  5]   7.00-8.00   sec  20.2 MBytes   169 Mbits/sec  0.068 ms  66700/81329 (82%)
[  5]   8.00-9.00   sec  20.2 MBytes   169 Mbits/sec  0.241 ms  67408/82032 (82%)
[  5]   9.00-10.00  sec  20.2 MBytes   169 Mbits/sec  0.168 ms  67017/81645 (82%)
[  5]  10.00-10.21  sec  1.70 MBytes  68.6 Mbits/sec  0.031 ms  5540/6769 (82%)
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Jitter    Lost/Total Datagrams
[  5]   0.00-10.21  sec   201 MBytes   165 Mbits/sec  0.031 ms  671727/817520 (82%)  receiver


### before NAT --> measured on raspi @ LAN/client facing interface

-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 192.168.1.17, port 44732
[  5] local 192.168.1.109 port 5201 connected to 192.168.1.17 port 50832
[ ID] Interval           Transfer     Bitrate         Jitter    Lost/Total Datagrams
[  5]   0.00-1.00   sec   107 MBytes   898 Mbits/sec  0.010 ms  3229/80727 (4%)
[  5]   1.00-2.00   sec   113 MBytes   949 Mbits/sec  0.009 ms  0/81934 (0%)
[  5]   2.00-3.00   sec   113 MBytes   948 Mbits/sec  0.012 ms  118/81934 (0.14%)
[  5]   3.00-4.00   sec   113 MBytes   949 Mbits/sec  0.013 ms  0/81935 (0%)
[  5]   4.00-5.00   sec   113 MBytes   949 Mbits/sec  0.009 ms  0/81933 (0%)
[  5]   5.00-6.00   sec   113 MBytes   947 Mbits/sec  0.014 ms  171/81935 (0.21%)
[  5]   6.00-7.00   sec   113 MBytes   949 Mbits/sec  0.012 ms  0/81885 (0%)
[  5]   7.00-8.00   sec   113 MBytes   949 Mbits/sec  0.009 ms  0/81929 (0%)
[  5]   8.00-9.00   sec   113 MBytes   949 Mbits/sec  0.015 ms  0/81931 (0%)
[  5]   9.00-10.00  sec   111 MBytes   935 Mbits/sec  0.014 ms  1176/81880 (1.4%)
[  5]  10.00-10.00  sec   157 KBytes   944 Mbits/sec  0.007 ms  0/111 (0%)
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Jitter    Lost/Total Datagrams
[  5]   0.00-10.00  sec  1.10 GBytes   942 Mbits/sec  0.007 ms  4694/818134 (0.57%)  receiver

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


