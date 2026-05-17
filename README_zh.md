[English](README.md) | 中文

# AstroReason-Bench

AstroReason-Bench 正在演进为一个用于空间任务设计基准测试 (benchmark) 和第一方方法层的 monorepo。

基准核心保持算法无关 (algorithm-agnostic)：基准测试定义问题、数据集和验证器 (verifier)；方法消费基准测试，而非相反。

如需复现历史论文，请使用 `v1` 分支。

## 仓库结构

```text
astro-reason/
├── benchmarks/   # 标准问题、数据集、验证器、生成器
├── experiments/  # 可复现的方法评估运行
├── solvers/      # 传统求解器实现
├── runtimes/     # 可复用的智能体系统执行基板
├── scripts/      # 仓库自有的编排与验证入口
└── tests/        # 聚焦的基准测试与工具测试
```

## 设计原则

- **算法无关的基准核心 (algorithm-agnostic benchmark core)**：`benchmarks/` 不编码偏好的求解策略。
- **单向契约 (one-way contracts)**：方法可以依赖基准测试；基准测试不得依赖方法代码。
- **独立的基准测试 (standalone benchmarks)**：每个基准测试保持自包含。
- **可复现的方法层 (reproducible method layers)**：实验、求解器和运行时应该是可运行且可检查的。

## 目录角色

- `benchmarks/` 拥有公开的基准定义和基准侧工具。
- `experiments/` 拥有扁平的可运行实验族和共享的提示/配置片段。
- `solvers/` 拥有传统的非智能体求解器方法。
- `runtimes/` 拥有可复用的智能体运行时环境、构建逻辑和共享运行时资源。

## 环境

基准核心开发使用 `uv`。方法所属的目录可以在有正当理由时使用不同的工具，只要基准契约保持干净。

## 状态

当前工作聚焦于：

- 精炼基准定义和验证器契约
- 开发传统求解器作为基线
- 实现和运行智能体实验
