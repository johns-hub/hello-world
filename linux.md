# Linux命令

## 1.查看整体机器性能

   top

- cpu 键盘数字键1
- mem
- id = idle
- load average: 0.00, 0.00, 0.00 平均值大于0.6繁忙

```shell
$ top
top - 23:35:45 up 890 days, 34 min,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  1.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.3%us,  1.0%sy,  0.3%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.3%us,  0.3%sy,  0.3%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.3%sy,  0.3%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3922688k total,  2580256k used,  1342432k free,   182144k buffers
Swap:  8392696k total,    11060k used,  8381636k free,   846536k cached
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                   
1682 work      39  19 5128m 1.2g  11m S  1.3 31.5   4:40.74 java                                                       
21782 root      39  19  535m  17m 3848 S  0.7  0.4   1091:49 leoAgent 

[root@192.168.1.1 ~]$ uptime
23:35:55 up 890 days, 34 min,  1 user,  load average: 0.00, 0.00, 0.00
```

## 2.内存

  ```shell
$ free
total       used       free     shared    buffers     cached
Mem:       3922688    2579944    1342744          0     182144     846576
-/+ buffers/cache:    1551224    2371464
Swap:      8392696      11060    8381636

[root@192.168.1.1 ~]$free -m
total       used       free     shared    buffers     cached
Mem:             3          2          1          0          0          0
-/+ buffers/cache:          1          2
Swap:            8          0          7

[root@192.168.1.1 ~]$ free -m
total       used       free     shared    buffers     cached
Mem:          3830       2519       1311          0        177        826
-/+ buffers/cache:       1514       2315
Swap:         8195         10       8185
  ```

## 3.硬盘

```shell
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/vda2             41284928   5719740  33468036  15% /
tmpfs                  1961344         0   1961344   0% /dev/shm
/dev/vda1               516040     59236    430592  13% /boot
/dev/vda5              1542096    639164    824596  44% /data

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/vda2              40G  5.5G   32G  15% /
tmpfs                 1.9G     0  1.9G   0% /dev/shm
/dev/vda1             504M   58M  421M  13% /boot
/dev/vda5             1.5G  625M  806M  44% /data
```

## 4.cpu (包含但不限于)

```shell
$ vmstat -n 2 3
procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu-----
r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
0  0  11060 1340648 182144 846688    0    0     0     9    0    0  0  0 99  0  0	
0  0  11060 1340236 182144 846688    0    0     0     8  726 1343  0  0 99  0  0	
0  0  11060 1340376 182144 846688    0    0     0     2  767 1393  0  0 99  0  0
```

## 5.磁盘IO

```shell
$ iostat -xdk 2 3
Linux 2.6.32-358.el6.x86_64 (LOK-MobileAPI-usercenter-05) 	11/22/2019 	_x86_64_	(4 CPU)

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
scd0              0.00     0.00    0.00    0.00     0.00     0.00     8.00     0.00    0.15   0.15   0.00
vda               0.01     5.30    0.02    4.17     0.27    36.27    17.44     0.01    3.13   1.46   0.61

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
scd0              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
vda               0.00     0.00    0.50    0.50     4.00     2.00    12.00     0.00    4.00   4.00   0.40

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
scd0              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
vda               0.00     8.50    0.00    3.00     0.00    46.00    30.67     0.00    1.17   0.83   0.25
```

# Linux网络

- **Host-Only**: The VM will be assigned one IP, but it's only accessible by the box VM is running on. No other computers can access it.
- **NAT**: Just like your home network with a wireless router, the VM will be assigned in a separate subnet, like `192.168.6.1` is your host computer, and VM is `192.168.6.3`, then your VM can access outside network like your host, but no outside access to your VM directly, it's protected.
- **Bridged**: Your VM will be in the same network as your host, if your host IP is `172.16.120.45` then your VM will be like `172.16.120.50`. It can be accessed by all computers in your host network.