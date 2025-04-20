---
title: 'Linux 系统性能测试'
date: 2025-03-29
---

## 磁盘

```
# 8k 随机写
fio -name=8krandw  -runtime=120  -filename=/tmp/rand.fio -ioengine=libaio -direct=1  -bs=8K  -size=5g  -iodepth=128  -numjobs=1  -rw=randwrite -group_reporting -time_based
  
# 8K  随机读
fio -name=8krandr  -runtime=120  -filename=/tmp/rand.fio -ioengine=libaio -direct=1  -bs=8K  -size=5g  -iodepth=128  -numjobs=1  -rw=randread -group_reporting -time_based
  
# 8k  混合读写
fio -name=8krandrw  -runtime=120  -filename=/tmp/rand.fio -ioengine=libaio -direct=1  -bs=8k  -size=5g  -iodepth=128  -numjobs=1  -rw=randrw -rwmixwrite=30  -group_reporting -time_based
   
# 1Mb  顺序写
fio -name=1mseqw  -runtime=120  -filename=/tmp/seq.fio -ioengine=libaio -direct=1  -bs=1024k  -size=5g  -iodepth=128  -numjobs=1  -rw=write -group_reporting -time_based
  
# 1Mb  顺序读
fio -name=1mseqr  -runtime=120  -filename=/tmp/seq.fio -ioengine=libaio -direct=1  -bs=1024k  -size=5g  -iodepth=128  -numjobs=1  -rw=read -group_reporting -time_based
  
# 1Mb  顺序读写
fio -name=1mseqrw  -runtime=120  -filename=/tmp/seq.fio -ioengine=libaio -direct=1  -bs=1024k  -size=5g  -iodepth=128  -numjobs=1  -rw=rw -rwmixwrite=30  -group_reporting -time_based
```