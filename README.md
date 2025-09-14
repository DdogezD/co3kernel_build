# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

---
**大量性能调优**

合并了部分来自 **sultan, arter97, pzqqt, brokestar, ztc1997, hfdem** 等内核开发者的优化

*排名不分先后*

---
**使用最小作用域 hooks 的 KernelSU Next**

使用 [Coccinelle](https://github.com/coccinelle/coccinelle) 准确应用 hooks 补丁

最小化内核 hooks 的性能开销

---
**支持 tmpfs 扩展属性**

可使用 [Mountify](https://github.com/backslashxx/mountify) 完成模块挂载

---
**网络相关调优**
 
使用 bbr+fq_codel

---
**I/O 调速器优化**

io调速器可选 ssg

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
