# README

## cc_net profile

环境：单节点16Core124GB设备

### cc_net 10个segment测试过程中cpu绝大部分时间（95%以上）是跑满的

submitit WARNING (2024-04-16 10:07:22,277) - Bypassing signal SIGTERM
2024-04-16 10:07 WARNING 47510:submitit - Bypassing signal SIGTERM

- 10个segment，每个segment（125MB左右）作为一个shared，1个shared内比较去重。峰值内存：42.3GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时5min20s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止,保留文件多，因此耗时多）
- 10个segment，每个segment（125MB左右）作为一个shared，2个shared内比较去重。峰值内存：43.4GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时5min40s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止）
- 10个segment，每个segment（125MB左右）作为一个shared，5个shared内比较去重。峰值内存：43.9GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时4min40s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止）
- 10个segment，每个segment（125MB左右）作为一个shared，10个shared内比较去重。峰值内存：44.2GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时4min40s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止）

### cc_net 40个segment测试过程中cpu大部分时间（95%以上）是跑满的

- 40个segment，每个segment（125MB左右）作为一个shared，1个shared内比较去重。峰值内存：61.5GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时29min44s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止,保留文件多，因此耗时多）
- 40个segment，每个segment（125MB左右）作为一个shared，10个shared内比较去重。峰值内存：68.4GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时37min24s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止,保留文件多，因此耗时多）
- 40个segment，每个segment（125MB左右）作为一个shared，40个shared内比较去重。峰值内存：74.7GB（系统总的内存消耗，启动前系统已有开销9.3GB左右），耗时1小时37min24s (任务调度有问题，最后一步（写结果到磁盘）有些job不终止,保留文件多，因此耗时多）===>耗时2h10min
