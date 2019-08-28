---
title: Windows 电源状态
toc: true
date: 2019-08-27 23:09:24
tags: [Windows,ACPI]
categories: [Windows]
---



<!--more-->

## Power states

| Global states | Name           | Sleep states | Description                                                  |
| ------------- | -------------- | ------------ | ------------------------------------------------------------ |
| G0            | Working        | S0           | The computer is running and the CPU executes instructions.   |
| G1            | Sleeping       | S0ix         | Modern Standby;  <br/>Some SoC systems support a low-power idle state known as [Modern Standby](http://go.microsoft.com/fwlink/p/?LinkID=624142). In this state, the system can very quickly switch from a low-power state to high-power state, so that it can respond quickly to hardware and network events. Systems that support Modern Standby do not use S1-S3. |
|               |                | S1           | Power on Suspend (POS): Processor caches are flushed, and the CPU(s) stops executing instructions. The power to the CPU(s) and RAM is maintained. Devices that do not indicate they must remain on may be powered off |
|               |                | S2           | CPU powered off. [Dirty cache](https://en.wikipedia.org/wiki/Dirty_cache) is flushed to RAM |
|               |                | S3           | Named Sleep on Windows; <br/>Suspend to RAM (STR): RAM remains powered. |
|               |                | S4           | Named Hibernation on Windows; <br/>Suspend to Disk: All content of the [main memory](https://en.wikipedia.org/wiki/RAM) is saved to [non-volatile memory](https://en.wikipedia.org/wiki/Non-volatile_memory) such as a [hard drive](https://en.wikipedia.org/wiki/Hard_drive), and the system is powered down |
| G2            | Soft off       | S5           | The Computer is powered down, but the power supply unit still supplies power. <br/>No previous content is retained. <br/>Some components may remain powered, then computer can be “wake” on input from the keyboard, mouse, clock, LAN, modem or USB devices. |
| G3            | Mechanical off |              | The computer's power has been totally removed via a mechanical switch (as on the rear of a PSU). <br/>The power cord can be removed and the system is safe for disassembly.<br/> Typically, only the [real-time clock](https://en.wikipedia.org/wiki/Real-time_clock)continues to run using its own small battery. |



## 参考资料

> - [Windows电源状态](https://wiki.zohead.com/技术/Windows/Windows电源状态.md)
> - [Advanced Configuration and Power Interface](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

