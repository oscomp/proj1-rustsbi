# proj1-rustsbi
用Rust语言实现的RISC-V Supervisor Binary Interface

当前实现：https://github.com/luojia65/rustsbi

## 特征
- 适应 RISC-V SBI 规范 v0.2
- 对 unix类型的操作系统有很好支持
- 用Rust实现
- 具有大部分功能的 OpenSBI 的替代方案
- 支持 QEMU 仿真器（RISC-V privileged spec v1.11）
- 向后兼容RISC-V privileged spec v1.9
- 支持Kendryte  K210 with MMU 和 S-Mode
