# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

---
**大量性能调优**

合并了部分来自 **sultan, arter97, pzqqt, brokestar, ztc1997, hfdem** 等内核开发者的优化 *(排名不分先后)*

- 启用 o3 优化编译
- 为 armv9-a 优化编译
- 为 a510 优化编译
- 启用 llvm Polly 优化器
- 启用 LAZY RCU
- 禁用 KFENCE & UBSAN
- ⚠ 禁用 Spectre 缓解措施以提升性能
  - CONFIG_MITIGATE_SPECTRE_BRANCH_HISTORY is not set
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 debug
- 去除 psi 中的 debug
- dma_buf: 去除 debug 以加速 ioctl
- arm64: clear_page 对齐 16b
- cpufreq: 在 scaling_min_freq 加入限制
- cpuidle: 去除 menu 的 iowait
- 重写的 ashmem
- 重写的 mem* func
  - memcpy, memmove, memset, memutil
- mm: 不为 user/admin 登录而保留内存 (~136m)
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY
- fs: 减少缓存以发挥大内存的作用
- ttwu 流程中省略多余的获取内存屏障操作
- vmalloc: 能够分配大块虚拟内存
- selinux: 避免动态内存分配

- **以及一些上游 backport...**

---
**使用最小作用域 hooks (v1.5) 的 KernelSU Next**

最小化内核 hooks 的性能开销

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
