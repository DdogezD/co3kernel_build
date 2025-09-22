# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

---
**大量性能调优**

合并了来自 **Sultan, arter97, Pzqqt, brokestar233, ztc1997, hfdem, Cloud_Yun** 等内核开发者的提交，排名不分先后。

⚠ 禁用 Spectre 缓解措施 (禁用基于历史的分支预测) 以提升性能

⚠ 禁用 Meltdown 缓解措施 (在 EL0 上作 unmap 处理) 以提升性能

⚠ 禁用软件模拟的 PAN 以提升性能

- 启用 o3 优化编译
- 为 armv9-a 优化编译
- 为 a510 优化编译
- 启用 llvm Polly 优化器
- 启用 LAZY RCU
- 禁用 KFENCE & UBSAN
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 debug
- 去除 psi 中的 debug
- dma_buf: 去除 debug 以加速 ioctl
- selinux: 去除对 audit 的依赖以提升性能
- selinux: 避免动态内存分配
- arm64: clear_page 对齐 16b
- cpuidle: 去除 menu 的 iowait
- vmalloc: 能够分配大块虚拟内存
- 重写的 ashmem
- 重写的 mem*
  - memcpy
  - memmove
  - memset
  - memutil
- mm: 不为 user/admin 登录而保留内存 (~136m)
- fair: 针对不对称的 cpu 拓扑优化
- fair: 去除 numa 相关的参数
- fair: PELT 半衰期(32ms) 减少到 16ms
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY
- fs: 减少缓存以发挥大内存的作用
- ttwu 流程中省略多余的获取内存屏障操作

- **以及一些上游 backport...**

---
**使用最小作用域 hooks (v1.5) 的 KernelSU Next (v1.1.0)**

最小化内核 hooks 的性能开销

---
**(todo) 风驰游戏调度** *- Experimental*

支持启用风驰游戏调度 (scx)

可使用修补后的 Scene 调度控制 (暂未实现)

---
**支持 tmpfs 扩展属性**

可使用 [Mountify](https://github.com/backslashxx/mountify) 完成模块挂载

---
**网络相关调优**
 
使用 westwood+

---
**zram 性能优化**

lz4 升级到 v1.10.0

---
**伪装最新 (NA) Linux 版本**

避免内核名特征检查

---
**使用官方 Build 脚本编译**

同步最新上游
尽可能保留官方配置

---
## 致谢

- [OnePlusOSS](https://github.com/OnePlusOSS/kernel_manifest) / [oneplus_sm8550](https://github.com/OnePlusOSS/android_kernel_common_oneplus_sm8550)
- [KernelSU](https://github.com/tiann/KernelSU)
- [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next)
- [KernelSU Coccinelle](https://github.com/devnoname120/kernelsu-coccinelle)
- [Action_OnePlus_MKSU_SUSFS](https://github.com/ShirkNeko/Action_OnePlus_MKSU_SUSFS)
