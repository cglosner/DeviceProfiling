# Memory and Storage Performance Profiling

## Tested System

Lenovo X1 Laptop
- OS: Windows 10 Pro
- RAM: 16GB
- Processor: Intel i7-8650U @ 1.90GHz/2.11GHz
- Storage: 500GB SSD

## General Memeory Performance Profile 

The following profile was obtained by running the `mlc` commands.

Measuring Idle Latencies (ns)
| Numa Node | 0 |
|----|----|
| 0 | 37.3 |


Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using traffic with the following read-write ratios

Measuring Peak Injection Memory Bandwidths for the system (MB/sec)
|Read/Write Ratios | Bandwidth |
|-----|-----|
| ALL Reads | 28547.3 |
|3:1 Reads-Writes | 25585.4 |
| 2:1 Reads-Writes | 25077.1 |
| 1:1 Reads-Writes | 25874.6 | 
| Stream-triad like | 25310.3 |

Using read-only traffic type

Measuring Memory Bandwidths between nodes within system (MB/sec)
| Numa Node | 0 |
|----|----|
| 0 | 28451.5 |

Using Read-only traffic type

Measuring Loaded Latencies for the system
| Inject Delay | Latency (ns) | Bandwidth (MB/sec) |
|-----|------|------|
| 00000 | 79.98 | 27920.3 |
| 00002 | 104.69 | 25622.7 |
| 00008 | 94.29 | 25823.0 |
| 00015 | 91.77 | 26823.1 |
| 00050 | 81.13 | 24513.2 |
| 00100 | 61.98 | 17376.7 |
| 00200 | 43.77 | 12359.4 |
| 00300 | 42.47 | 9150.7 |
| 00400 | 41.91 | 7413.2 |
| 00500 | 41.27 | 6329.7 |
| 00700 | 41.43 | 5017.4 |
| 01000 | 40.73 | 4036.6 | 
| 01300 | 40.61 | 3488.7 |
| 01700 | 40.49 | 3053.7 |
| 02500 | 40.66 | 2579.9 |
| 03500 | 40.57 | 2294.5 |
| 05000 | 40.38 | 2091.5 |
| 09000 | 41.07 | 1838.4 |
| 20000 | 40.74 | 1698.9 |

Using small pages for allocating buffers

Measuring cache-to-cache transfer latency (in ns)

|Cache-to-Cache | Latency |
|------|------|
| Local Socket L2->L2 HIT Latency | 12.1 |
| Local Socket L2->L2 HITM Latency | 19.4 |

## Memory Performance Profiling With 62.5MB Buffers

`mlc --bandwidth_matrix -b64000`
Memory Bandwidth between Nodes in the system(MB/sec)
| Numa Node | 0 |
|----|----|
| 0 | 26992.5 |

`mlc --loaded_latency -b64000`
Measuring Loaded Latencies for the system
| Inject Delay | Latency (ns) | Bandwidth (MB/sec) |
|-----|------|------|
 |00000 | 112.40  |  24844.1|
 |00002 |  85.93  |  27544.1|
 |00008 |  90.74  |  26551.5|
 |00015 |  82.63  |  26735.9|
 |00050 |  80.50  |  24604.9|
 |00100 |  71.33  |  17476.8|
 |00200 |  57.06  |  11992.2|
 |00300 |  68.48  |   8018.8|
 |00400 |  46.48  |   7337.6|
 |00500 |  51.51  |   5759.2|
 |00700 |  50.48  |   4551.0|
 |01000 |  50.65  |   3594.2|
 |01300 |  45.99  |   3261.2|
 |01700 |  47.53  |   2783.8|
 |02500 |  47.85  |   2316.8|
 |03500 |  47.85  |   2035.8|
 |05000 |  48.38  |   1806.6|
 |09000 |  43.14  |   1761.1|
 |20000 |  49.49  |   1416.1|
 
 
 ![Throughput vs. Latency (64MB)](https://github.com/cglosner/DeviceProfiling/blob/main/64TvL.png)
 
## Memory Performance Profiling with 256MB Buffer

`mlc --bandwidth_matrix -b256000`
Memory Bandwidth between Nodes in the system(MB/sec)
| Numa Node | 0 |
|----|----|
| 0 | 28122.3 |

`mlc --loaded_latency -b256000`
Measuring Loaded Latencies for the system
| Inject Delay | Latency (ns) | Bandwidth (MB/sec) |
|-----|------|------|
 | 00000 |  83.26  |  27572.3|
 |00002 |  82.51  |  27626.1|
 |00008 |  80.48  |  27256.3|
 |00015 |  79.84  |  27030.1|
 |00050 |  72.42  |  25066.8|
 |00100 |  50.84  | 19915.2|
 |00200 |  45.62  |  12705.9|
 |00300 |  43.86  |   9336.1|
 |00400 |  43.05  |   7522.7|
 |00500 |  42.71  |   6368.5|
 |00700 |  42.27  |   5052.1|
 |01000 |  42.28  |   4010.0|
 |01300 |  43.76  |   3308.0|
 |01700 |  42.86  |   2884.0|
 |02500 | 43.42   |  2396.9|
 |03500 |  43.81  |   2122.2|
 |05000 |   43.15 |    1948.9|
 |09000 |  43.28  |   1738.9|
 |20000 |  53.61  |   1305.5|
 
 ![Throughput vs. Latency(64MB)](https://github.com/cglosner/DeviceProfiling/blob/main/256TvL.png)
 
 
## Memory Profile Analysis
 
Looking at the plots for both 64MB and 256MB buffers, the results were very similar in both cases but it is hard to have a proper comparison.

 ![Throughput vs. Latency](https://github.com/cglosner/DeviceProfiling/blob/main/ComparisonTvL.png)

The plot above includes both the 64MB and 256MB Throughput vs. Latency to give a more comprehensible comparison. As you can see, when the buffer size
is larger then the latency is lower on average, but in both cases they follow the same trend. The latency decreases as the bandwidth increases, which 
makes sense because when more data can pass through then the data in the IO queue can be processed faster with a lower latency.
## Storage Profiling 

Throughout this section it is broken up by commands used. Below the commands is the associated
relevant output. 

256MB for Read only
```
fio --name=latency-profile.fio --iodepth=16 --rw=randread --size=256M --direct=1
---------------------------------------
read: IOPS=74.2k, BW=290MiB/s (304MB/s)(256MiB/883msec)
lat (usec): min=7, max=327, avg=10.49, stdev= 5.64
bw (  KiB/s): min=293837, max=293837, per=98.98%, avg=293837.00, stdev= 0.00, samples=1
iops        : min=73459, max=73459, avg=73459.00, stdev= 0.00, samples=1
```

256MB for Read-Write
```
fio --name=latency-profile.fio --iodepth=4 --rw=randrw --size=256M --direct=1
------------------------------------------------------
 read: IOPS=37.2k, BW=145MiB/s (152MB/s)(128MiB/881msec)
 lat (usec): min=7, max=253, avg=10.63, stdev= 4.78
 bw (  KiB/s): min=148657, max=148657, per=100.00%, avg=148657.00, stdev= 0.00, samples=1
   iops        : min=37164, max=37164, avg=37164.00, stdev= 0.00, samples=1
   
  write: IOPS=37.2k, BW=145MiB/s (152MB/s)(128MiB/881msec)
lat (usec): min=7, max=256, avg=10.26, stdev= 4.61
 bw (  KiB/s): min=148767, max=148767, per=99.90%, avg=148767.00, stdev= 0.00, samples=1
   iops        : min=37191, max=37191, avg=37191.00, stdev= 0.00, samples=1
```

4KB for Read-Write (which only resulted in reading)
```
fio --name=latency-profile.fio --iodepth=4 --rw=randrw --size=4K --direct=1
----------------------------------------------
read: IOPS=1000, BW=4000KiB/s (4096kB/s)(4096B/1msec)
 lat (nsec): min=71100, max=71100, avg=71100.00, stdev= 0.00
```

64MB for Read-Write
```
fio --name=latency-profile.fio --iodepth=4 --rw=randrw --size=64M --direct=1
----------------------------------------------
 read: IOPS=37.8k, BW=148MiB/s (155MB/s)(31.9MiB/216msec)
lat (nsec): min=7300, max=63100, avg=10334.99, stdev=4020.87

write: IOPS=38.1k, BW=149MiB/s (156MB/s)(32.1MiB/216msec)
lat (usec): min=7, max=202, avg=10.01, stdev= 4.69
```

16MB for Read-Write
```
fio --name=latency-profile.fio --iodepth=4 --rw=randrw --size=16M --direct=1
-------------------------------------------
read: IOPS=37.6k, BW=147MiB/s (154MB/s)(7968KiB/53msec)
lat (nsec): min=7300, max=63600, avg=10051.26, stdev=3888.42

 write: IOPS=39.7k, BW=155MiB/s (163MB/s)(8416KiB/53msec)
lat (nsec): min=7200, max=62300, avg=9675.81, stdev=4105.43
```
