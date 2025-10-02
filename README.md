# CO³Kernel 
*Custom OnePlus Open Optimized Kernel*

这是为 Hedwig (OnePlus Open) 编译的内核, 基于 OnePlusOSS 源码, 提升设备综合表现。

#### 👾 内核级 root impl. 
- KernelSU Next: v1.1.0 (Manual Hooks)
- KernelSU Scope Minimized Hooks: v1.5
- Mountify 支持
  - tmpfs: 支持拓展属性

#### ⚡ CPU 优化
- BORE 调度器: v5.1.0
- cpuidle: 去除 menu 的 iowait
- fair: PELT 半衰期 32ms 减少到 16ms
- 优化 DynamIQ Shared Unit
  - fair: 减少任务迁移开销
  - sched: 禁用 CACHE_HOT_BUDDY

#### 📦 内存优化
- LZ4: v1.10.0
- 优化的 mem* (~25%+ faster)
  - memcpy
  - memmove
  - memset
- vmalloc: 支持大块虚拟内存
- mm: 不为 user/admin 登录而保留内存 (~136m)
- arm64: clear_page 对齐 16b

#### 📈 网络栈优化
- 采用 bbr 收敛方式的 westwood 算法变种
- 将 westwood 变种作为默认的 tcp 拥塞算法
- 将 fq_codel 作为默认的数据包队列调度器

#### 🎮️ 更多手柄适配
- 启用手柄反馈与指示灯特性
- 支持 Nintendo 手柄特性
  - 手柄反馈
  - 玩家灯
  - Joy-Con 二合一

#### 🖨️ 妥协调试效率换取的性能提升
- 禁用 KFENCE & UBSAN
- BLK/BLKdev 不收集 io stat
- 去除 drm 中的 dbg
- 去除 psi 中的 dbg
- selinux: 去除对 audit 的依赖以提升性能

#### 🧪 妥协安全性换取的性能提升
*在 Android 上，攻击者一般不会利用这些漏洞。
- 禁用软件模拟的 PAN 以提升性能
- 禁用 Meltdown 缓解措施 (在 EL0 上作 unmap 处理) 以提升性能
- 禁用 Spectre 缓解措施 (禁用基于历史的分支预测) 以提升性能

#### 🦄 编译器优化
  - 启用 o3 优化编译
  - 为 SM8550 优化编译
  - 启用 llvm Polly 优化器

#### 🔨 小幅调整
- 启用 LazyRCU
- 禁用 IKHEADERS
- selinux: 避免动态内存分配
- sched idle loop 中省略多余的获取内存屏障
- ttwu 流程中省略多余的获取内存屏障
- fs: 减少缓存以发挥大内存的作用
- fs: 对齐 8b

## 🧩 CO³Kernel 附加模块
- 配置 I/O 调速器为 none
- 禁用假电池容量预留显示
- 关闭 coresight

## 🍀 特别感谢
此内核合并了来自 **Sultan, arter97, Pzqqt, brokestar233, ztc1997, hfdem** 等内核开发者的提交。

感谢 **Pzqqt, brokestar233, Cloud_Yun** 提供了开发指导。

排名不分先后。
