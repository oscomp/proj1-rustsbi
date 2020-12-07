# proj1-rustsbi

## 介绍
用Rust语言实现的RISC-V Supervisor Binary Interface。该项目最初是 rCore 代码夏季 2020 活动的一部分，现在它能够在支持的 RISC-V 设备上运行 rCore 教程和其他操作系统内核。

当前实现：https://github.com/luojia65/rustsbi

### 所属赛道
“OS功能设计”

### 项目导师
蒋周奇 
- github https://github.com/luojia65
- email me@luojia.cc

### 特征
- 适应 RISC-V SBI 规范 v0.2
- 对 unix类型的操作系统有很好支持
- 用Rust实现
- 具有大部分功能的 OpenSBI 的替代方案
- 支持 QEMU 仿真器（RISC-V privileged spec v1.11）
- 向后兼容RISC-V privileged spec v1.9
- 支持Kendryte  K210 with MMU 和 S-Mode

### 文档
- [中文的开发blog](https://github.com/luojia65/rcore-os-blog/blob/master/source/_posts/os-report-final-luojia65.md)
- [中文介绍ppt](https://github.com/luojia65/DailySchedule/blob/master/Rust%E8%AF%AD%E8%A8%80%E4%B8%8ERISC-V%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.pdf)


### 关于平台实现注意事项
- RustSBI可以库的形式纯真。在正常情况下，RustSBI 通过embedded-hal 来实现。
- 在 QEMU 和 K210 平台上，支持CLINT和 PLIC 外围设备。

### License
- MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT)
- 木兰 PSL v2 (LICENSE-MULAN or https://opensource.org/licenses/MulanPSL-2.0)

## 项目目标
- 支持更多的RISC-V based的硬件或硬件模拟器，如SIFIVE，Terminus等
- 支持对S-Mode下的OS Kernel的在线调试功能，方便调试OS Kernel
- 支持加载OS Kernel到开发板的RAM中，实现快速运行

