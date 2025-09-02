# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

---
**使用最小作用域 hooks 的 KernelSU Next**

使用 [Coccinelle](https://github.com/coccinelle/coccinelle) 准确应用 hooks 补丁

最小化内核 hooks 的性能开销

---
**支持 tmpfs 扩展属性**

可使用 [Mountify](https://github.com/backslashxx/mountify) 完成模块挂载

---
**网络相关配置优化**
 
可选 bbr & westwood 网络拥塞算法 (默认 westwood)

支持显式拥塞通知 (ECN)

---
**双层 zram 优化**

lz4 升级到 v1.10.0

zstd 升级到 v1.5.7

禁用 zstdn, 使 zram1 算法 fallback 为 zstd

---
**伪装最新 (NA) Linux 版本**

避免内核名特征检查

---
**使用官方 Build 脚本编译**

尽可能保留官方配置

---
## 致谢

- [OnePlusOSS](https://github.com/OnePlusOSS/kernel_manifest) / [oneplus_sm8550](https://github.com/OnePlusOSS/android_kernel_common_oneplus_sm8550)
- [KernelSU](https://github.com/tiann/KernelSU)
- [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next)
- [KernelSU Coccinelle](https://github.com/devnoname120/kernelsu-coccinelle)
- [Action_OnePlus_MKSU_SUSFS](https://github.com/ShirkNeko/Action_OnePlus_MKSU_SUSFS)
- [AnkoleNeon’s Patches](https://github.com/AnkoleNeon/GKI_KernelSU_SUSFS)
