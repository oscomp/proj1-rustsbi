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
RustSBI已经被RISC-V SBI标准收录，作为官方推荐的实现之一，它的实现编号为4。

RustSBI的主要特点如下：

- 适配 RISC-V SBI 规范 v0.3
- 对类 Unix 操作系统有很好支持
- 完全使用 Rust 语言实现
- 是 OpenSBI 项目的有力竞争品
- 支持 QEMU 仿真器（RISC-V 特权级版本 v1.11）
- 向下兼容 RISC-V 特权级版本 v1.9
- 支持 Kendryte K210（含MMU和S模式）

当前项目实现源码等：https://github.com/rustsbi/rustsbi

### 所属赛道

2025年全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的学生
- 请遵循“2025年全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

蒋周奇（洛佳）
- github https://github.com/luojia65
- email me@luojia.cc

### 难度

中等

### 文档

所有与RustSBI相关的文档和报告汇总于[slides项目](https://github.com/rustsbi/slides)中。

### 平台实现的注意事项

- RustSBI 可以库的形式使用。通常情况下，RustSBI 的实现基于对 embedded-hal 的实现。
- 目前，在 QEMU 和 K210 平台上支持 CLINT 和 PLIC 外围设备。

### License

- MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT)
- 木兰 PSL v2 (LICENSE-MULAN or https://opensource.org/licenses/MulanPSL-2.0)

## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

建议选择的开发板（一项即可）：
* [VisionFive SBC](https://starfivetech.com/site/exploit), 2 * SiFive U74
* Allwinner D1/D1s boards, 有多个供应商, 1 * T-Head Xuantie C906
* HiFive Unmatched, 异构多核, 4 * SiFive U74, 1 * SiFive S7

### 第一题：RustSBI支持

- 挑选RISC-V硬件或模拟器，调查它具有哪些对RustSBI实现有帮助的外设。
- 选择可用的Rust语言运行时。您可以从开源实现（如riscv-rt）中选择，也可以自己编写简单的运行时；
- 使用RustSBI、HAL库和运行时，编写代码，使RustSBI支持挑选的RISC-V硬件或硬件模拟器。至少需要能运行rCore-Tutorial项目的操作系统内核。

### 第二题：引导程序环境

- 挑选RISC-V硬件或模拟器。对它包含的中断处理器（如CLINT、PLIC等），阅读文档或逆向分析，了解此中断处理器的使用方法；
- Oreboot是一个引导程序框架。阅读Oreboot的文档，了解它的功能；
- 分支Oreboot项目，为它增加一个平台实现，即您想要移植的开发板。

如果目标开发板具有闪存，建议将引导程序烧录到闪存中，然后由闪存启动系统。否则，可以使用SD卡分区的形式安装引导程序。

### 第三题：复杂的SBI实现

- 编写一个SBI固件，使之能下载操作系统内核并开机运行。可以选择从串口、USB等有线或无线方式下载，可以下载到RAM以实现快速运行（下载完毕后，请释放设备的所有权，以供操作系统使用）；
- 编写一个SBI固件，它能检测系统中是否插着可移除的存储设备（如SD卡），如果有，尝试运行存储设备上的操作系统内核；
- 编写一个SBI固件，它能连接到调试用的宿主机（PC机等），并可在S模式下调试正在运行的操作系统内核。要求从宿主机输入指令，从SBI固件返回调试结果。
