# proj1-rustsbi

### 项目描述

RISC-V SBI（Supervisor Binary Interface）是RISC-V指令集的一种标注，它拥有多种实现。
SBI的实现是在M模式下运行的特定于平台的固件，以S或U模式执行的引导加载程序，管理程序或通用的操作系统。
除了引导启动之外，SBI还将常驻后台，为其上的操作系统提供功能支持。

RustSBI是Rust语言编写的RISC-V SBI实现。该项目最初是“rCore 代码之夏-2020”活动的一部分，
现在它能够在支持的 RISC-V 设备上运行 rCore 教程和其它操作系统内核。

RustSBI项目的目标是，制作一个最小的Rust语言SBI实现，为其它实现提供参考和支持。
RustSBI也可以作为一个库使用，使RISC-V处理器核和片上系统供应商可以轻松实现到自己的平台，以适应特定的硬件配置。

当前项目实现源码等：https://github.com/luojia65/rustsbi

### 所属赛道

“OS功能设计”

### 项目导师

蒋周奇 
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

- 对更多的硬件或模拟器，先编写对应的PAC库，进而编写支持 embedded-hal 的HAL库
- 支持更多基于的RISC-V的硬件或硬件模拟器，如SiFive，Terminus等
- 完善有关的工具链，支持对S-Mode下的OS Kernel的在线调试功能，方便调试OS Kernel
- 完善有关的工具链，支持加载OS Kernel到开发板的RAM中，实现快速运行
