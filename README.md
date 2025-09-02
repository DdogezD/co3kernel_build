# CO³ — Custom OnePlus Open OKI

这是为 **Hedwig (OnePlus Open)** 编译的内核，包含以下特性：

- **使用手动最小作用域 hooks 的 KernelSU Next:** 最小化 KernelSU 性能开销。
- **支持 tmpfs 扩展属性:** 可使用 [Mountify](https://github.com/backslashxx/mountify) 完成模块挂载。
- **支持 bbr & westwood 网络拥塞算法**
- **LZ4 1.10.0**
- **ZSTD 1.5.7**
- **默认伪装为最新 OnePlus Open (NA) 内核 Linux 版本**
- **使用官方 Build 脚本编译, 力求与官方产物接近**

## 致谢

- [OnePlusOSS](https://github.com/OnePlusOSS/kernel_manifest) / [oneplus_sm8550](https://github.com/OnePlusOSS/android_kernel_common_oneplus_sm8550)
- [KernelSU](https://github.com/tiann/KernelSU)
- [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next)
- [KernelSU Coccinelle](https://github.com/devnoname120/kernelsu-coccinelle)
- [Action_OnePlus_MKSU_SUSFS](https://github.com/ShirkNeko/Action_OnePlus_MKSU_SUSFS)
- [AnkoleNeon’s Patches](https://github.com/AnkoleNeon/GKI_KernelSU_SUSFS)
