# CO³Kernel 
*Custom OnePlus Open Optimized Kernel*

这是为 Hedwig (OnePlus Open) 编译的内核, 基于 OnePlusOSS 源码, 提升设备能效表现。

合并来自 **Sultan, arter97, Pzqqt, brokestar233, ztc1997, hfdem** 等内核开发者的提交, 排名不分先后。

## 特别感谢
**Pzqqt, brokestar233, Cloud_Yun** 提供了开发指导

**特性**
-

#### 👾 内核级 root impl. 
- KernelSU Next: v1.1.0
- KernelSU Scope Minimized Hooks: v1.5

#### 🧩 Mountify 支持
- tmpfs: 支持拓展属性

#### 🔧 BORE CPU Sched: v5.3.0

#### 📦 LZ4: v1.10.0

#### 📈 包含精简 bbr 特性的 westwood & fq_codel

#### 🎮️ 更多手柄适配
- 启用手柄强制反馈与指示灯特性
- 同步上游手柄支持列表
- 支持 Nintendo 手柄特性 (Pro, Joy-Con)

#### 🖨️ 妥协调试效率换取的性能提升
- 禁用 KFENCE & UBSAN
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 debug
- 去除 psi 中的 debug
- selinux: 去除对 audit 的依赖以提升性能

#### 🪤 妥协安全性换取的性能提升
*在 Android 上，攻击者一般不会利用这些漏洞。
- 禁用软件模拟的 PAN 以提升性能
- 禁用 Meltdown 缓解措施 (在 EL0 上作 unmap 处理) 以提升性能
- 禁用 Spectre 缓解措施 (禁用基于历史的分支预测) 以提升性能

#### 🧑‍💻 编译器优化
  - 启用 o3 优化编译
  - 为 armv9-a 优化编译
  - 为 a510 优化编译
  - 启用 llvm Polly 优化器

#### ⚡ 大量性能优化
- selinux: 避免动态内存分配
- arm64: clear_page 对齐 16b
- cpuidle: 去除 menu 的 iowait
- sched idle loop 中省略多余的获取内存屏障
- ttwu 流程中省略多余的获取内存屏障
- 优化的 mem*
  - memcpy
  - memmove
  - memset
- vmalloc: 支持大块虚拟内存
- mm: 不为 user/admin 登录而保留内存 (~136m)
- fair: PELT 半衰期 32ms 减少到 16ms
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY
- fs: 减少缓存以发挥大内存的作用
- fs: 对齐 8b

CO³Kernel 附加模块
-

- 配置 I/O 调速器为 none
- 禁用假电池容量预留显示
- 关闭 coresight
