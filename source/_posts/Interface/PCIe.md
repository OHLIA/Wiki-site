---
title: PCIe
toc: true
date: 2019-08-28 20:01:58
tags: [PCIe]
categories: [PCIe]
---



<!--more-->

| Revision | Coding    | Date Rate | x1         | x4         | x16         |
| -------- | --------- | --------- | ---------- | ---------- | ----------- |
| 1.0      | 8b/10b    | 2.5 GT/s  | 250 MB/s   | 1 GB/s     | 4 GB/s      |
| 2.0      | 8b/10b    | 5 GT/s    | 500 MB/s   | 2 GB/s     | 8 GB/s      |
| 3.0      | 128b/130b | 8 GT/s    | 984.6 MB/s | 3.94 GB/s  | 15.75 GB/s  |
| 4.0      | 128b/130b | 16 GT/s   | 1696 MB/s  | 7.88  GB/s | 31.51 GB/s  |
| 5.0      | 128b/130b | 32 GT/s   | 3938 MB/s  | 15.75 GB/s | 126.03 GB/s |

### Bandwidth

PCIe 2.0 support 5 GT/s, every lane support transmit 5G bit, but don’t means the transmission rate is 5Gbps for every lane.   
Because the encode scheme is 8b/10b, means transmit 8 bit data need send 10 bit.  
So PCIe 2.0 every lane actual rate  is 5 x 8 / 10 = 4 Gbps = 500 MB/s .  
PCIe 3.0 1 lane, 8 x 128 /130 = 7.88 Gbps = 984.6 MB/s.



## 参考资料

> - [PCI-E总线带宽](https://wiki.zohead.com/技术/硬件/PCI-E/PCI-E总线带宽.md)
> - [PCI Express](https://en.wikipedia.org/wiki/PCI_Express)
