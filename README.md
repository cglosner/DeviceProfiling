# Memory and Storage Performance Profiling

Measuring Idle Latencies (ns)
|----|----|
| Numa Node | 0 |
| 0 | 37.3 |


Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using traffic with the following read-write ratios

Measuring Peak Injection Memory Bandwidths for the system (MB/sec)
|----|----|
| ALL Reads | 28547.3 |
|3:1 Reads-Writes | 25585.4 |
| 2:1 Reads-Writes | 25077.1 |
| 1:1 Reads-Writes | 25874.6 | 
| Stream-triad like | 25310.3 |

Using read-only traffic type

Measuring Memory Bandwidths between nodes within system (MB/sec)
|---|----|
| Numa Node | 0 |
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
|------|-------|
| Local Socket L2->L2 HIT Latency | 12.1 |
| Local Socket L2->L2 HITM Latency | 19.4 |
