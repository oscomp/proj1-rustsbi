# proj1-rustsbi

### 题目
**rustsbi**

### 项目描述

RISC-V指令集的SBI标准规定了类Unix平台下，操作系统运行环境的规范。这个规范拥有多种实现，RustSBI是它的一种实现。

RISC-V架构中，存在着定义于操作系统之下的运行环境。这个运行环境不仅将引导启动RISC-V下的操作系统，
还将常驻后台，为操作系统提供一系列二进制接口，以便其获取和操作硬件信息。
RISC-V给出了此类环境和二进制接口的规范，称为“操作系统二进制接口”，即“SBI”。

SBI的实现是在M模式下运行的特定于平台的固件，它将管理S、U等特权上的程序或通用的操作系统。

RustSBI项目发起于鹏城实验室的“rCore代码之夏-2020”活动，它是完全由Rust语言开发的SBI实现。
现在它能够在支持的RISC-V设备上运行rCore教程和其它操作系统内核。

RustSBI项目的目标是，制作一个从固件启动的最小Rust语言SBI实现，为可能的复杂实现提供参考和支持。
RustSBI也可以作为一个库使用，帮助更多的SBI开发者适配自己的平台，以支持更多处理器核和片上系统。

当前项目实现源码等：https://github.com/luojia65/rustsbi

### 所属赛道

2021全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2021年春季学期或之后本科毕业的大一~大四的学生）
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2021全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

蒋周奇（洛佳）
- github https://github.com/luojia65
- email me@luojia.cc

### 难度

中等

### 特征

- 适配 RISC-V SBI 规范 v0.2
- 对类 Unix 操作系统有很好支持
- 完全使用 Rust 语言实现
- 具备 OpenSBI 的大部分功能
- 支持 QEMU 仿真器（RISC-V 特权级版本 v1.11）
- 向下兼容 RISC-V 特权级版本 v1.9
- 支持 Kendryte K210（含MMU和S模式）

### 文档

- [中文开发博客](https://github.com/luojia65/rcore-os-blog/blob/master/source/_posts/os-report-final-luojia65.md)
- [中文介绍ppt](https://github.com/luojia65/DailySchedule/blob/master/Rust%E8%AF%AD%E8%A8%80%E4%B8%8ERISC-V%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.pdf)

### 平台实现的注意事项

- RustSBI 可以库的形式使用。通常情况下，RustSBI 的实现基于对 embedded-hal 的实现。
- 目前，在 QEMU 和 K210 平台上支持 CLINT 和 PLIC 外围设备。

### License

- MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT)
- 木兰 PSL v2 (LICENSE-MULAN or https://opensource.org/licenses/MulanPSL-2.0)

## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

### 第一题：RustSBI支持

- 挑选RISC-V硬件或模拟器，编写支持embedded-hal的HAL库。您可能需要先获得它的SVD文件，进而使用svd2rust生成对应的PAC库，基于PAC编写HAL库；
- 选择可用的Rust语言运行时。您可以从开源实现（如riscv-rt）中选择，也可以自己编写简单的运行时；
- 基于RustSBI、HAL库和运行时，编写代码，使RustSBI支持挑选的RISC-V硬件或硬件模拟器。至少需要能运行rCore-Tutorial项目的操作系统内核。

### 第二题：RTIC运行时

- 挑选RISC-V硬件或模拟器。对它包含的中断处理器（如CLINT、PLIC等），阅读文档或逆向分析，了解此中断处理器的使用方法；
- 对这款中断处理器，设计通用的库，支持优先级中断功能，以作为riscv库的补充。您可能需要参考cortex-m库的NVIC结构体（[这里](https://docs.rs/cortex-m/0.7.0/cortex_m/peripheral/struct.NVIC.html)）；
- RTIC是一个中断驱动的并发运行时。阅读RTIC的文档（[这里](http://rtic.rs/)），了解RTIC的设计和功能；
- RTIC目前支持Cortex-M架构；使用您的中断处理器库，尝试编写代码，使RTIC支持RISC-V架构和所挑选芯片包含的中断处理器。

### 第三题：复杂的SBI实现

- 编写一个SBI固件，使之能下载操作系统内核并开机运行。可以选择从串口、USB等有线或无线方式下载，可以下载到RAM以实现快速运行（下载完毕后，请释放设备的所有权，以供操作系统使用）；
- 编写一个SBI固件，它能检测系统中是否插着可移除的存储设备（如SD卡），如果有，尝试运行存储设备上的操作系统内核；
- 编写一个SBI固件，它能连接到调试用的宿主机（PC机等），并可在S模式下调试正在运行的操作系统内核。要求从宿主机输入指令，从SBI固件返回调试结果。
