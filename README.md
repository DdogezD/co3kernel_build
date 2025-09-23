# CO³Kernel 
**Custom Optimized OnePlus Open Kernel**

这是为 Hedwig (OnePlus Open) 编译的内核, 基于 OnePlusOSS 源码, 提升设备能效表现。

合并了来自 **Sultan, arter97, Pzqqt, brokestar233, ztc1997, hfdem, Cloud_Yun** 等内核开发者的提交, 排名不分先后。

## 特别感谢
**Pzqqt, brokestar233** 提供了开发指导

**Cloud_Yun** 提供了开发指导, 移植了 SCX 调速器

**🏁 特性**
-

⚙️ 伪装官方内核 uname (latest NA)

⚙️ SCX 调速器 - experimental

⚙️ KernelSU Scope Minimized Hooks: v1.5

⚙️ KernelSU Next: v1.1.0

⚠ 禁用软件模拟的 PAN 以提升性能

⚠ 禁用 Meltdown 缓解措施 (在 EL0 上作 unmap 处理) 以提升性能

⚠ 禁用 Spectre 缓解措施 (禁用基于历史的分支预测) 以提升性能

- 启用 o3 优化编译
- 为 armv9-a 优化编译
- 为 a510 优化编译
- 启用 llvm Polly 优化器
- 禁用 KFENCE & UBSAN
- tmpfs: 支持拓展属性
- tcp 拥塞算法: westwood+
- lz4: v1.10.0
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 debug
- 去除 psi 中的 debug
- selinux: 去除对 audit 的依赖以提升性能
- selinux: 避免动态内存分配
- arm64: clear_page 对齐 16b
- cpuidle: 去除 menu 的 iowait
- sched idle loop 中省略多余的获取内存屏障
- ttwu 流程中省略多余的获取内存屏障
- vmalloc: backport 上游更新
- 重写的 ashmem
- 优化的 mem*
  - memcpy
  - memmove
  - memset
- mm: 不为 user/admin 登录而保留内存 (~136m)
- fair: PELT 半衰期 32ms 减少到 16ms
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY
- fs: 减少缓存以发挥大内存的作用

🧩 CO³Kernel 附加模块
-

- 支持控制内建的 scx 调速器
  - Auxiliary_Standalone: 主动根据配置的应用列表来切换风驰游戏调度
  - Auxiliary_ScenePatcher: 修补 Scene 调度，对游戏使用风驰游戏调度
  - Disable: 不使用风驰游戏调度
- 配置 I/O 调速器为 none
- 禁用假电池容量预留显示
- 关闭 coresight
