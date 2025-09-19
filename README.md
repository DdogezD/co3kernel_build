# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

---
**大量性能调优**

合并了部分来自 **sultan, arter97, pzqqt, brokestar, ztc1997, hfdem** 等内核开发者的优化 *(排名不分先后)*

- 启用 o3 编译
- 启用 llvm armv9-a 优化
- 启用 llvm Polly 优化器
- 启用 LAZY RCU
- 禁用 KFENCE & UBSAN
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 debug
- 去除 psi 中的 debug
- arm64: clear_page 对齐 16b
- cpuidle: 去除 cpuidle: menu 的 iowait
- 重写的 mem* func
  - memcpy, memmove, memset, memutil
- mm: 不为 user/admin 登录而保留内存 (~136m)
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY
- fs: 缓存减半以发挥大内存的作用
- ttwu 流程中省略多余的获取内存屏障操作
- vmalloc: 能够分配大块虚拟内存
- selinux: 避免动态内存分配

- 以及一些上游补丁...

---
**使用最小作用域 hooks 的 KernelSU Next**

使用 [Coccinelle](https://github.com/coccinelle/coccinelle) 准确应用 hooks 补丁

最小化内核 hooks 的性能开销

---
**支持 tmpfs 扩展属性**

可使用 [Mountify](https://github.com/backslashxx/mountify) 完成模块挂载

---
**网络相关调优**
 
使用 westwood_plus+fq_codel

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
