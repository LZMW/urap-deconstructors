# 协作模式示例

> 这些是参考示例，协调器可根据实际情况自由组合或创新

## 示例1：单专家模式

**适用场景**：特定阶段的独立任务

**调用示例**：
```
Task(subagent_type="deconstructors-profiler", prompt="扫描项目技术栈...")
Task(subagent_type="deconstructors-strategist", prompt="基于指纹报告制定分析策略...")
Task(subagent_type="deconstructors-hunter", prompt="分析 [功能模块] 的调用链...")
Task(subagent_type="deconstructors-scribe", prompt="创建/更新文档...")
```

## 示例2：完整 U.R.A.P 链式协作

**适用场景**：完整的代码库逆向分析与文档生成

**调用示例**：
```
Step 1: Task(subagent_type="deconstructors-profiler", prompt="执行技术栈指纹扫描...")
        ↓ 获取《技术栈指纹报告》

Step 2: Task(subagent_type="deconstructors-strategist", prompt="基于指纹报告制定分析策略...")
        ↓ 获取《分析策略声明》

Step 3: Task(subagent_type="deconstructors-scribe", prompt="初始化文档体系骨架...")
        ↓ 获取文档框架

Step 4: Task(subagent_type="deconstructors-hunter", prompt="按照策略深度分析代码...")
        ↓ 获取结构化知识

Step 5: Task(subagent_type="deconstructors-scribe", prompt="填充文档并执行质量验收...")
        ↓ 获取完整文档体系
```

## 示例3：并行协作

**适用场景**：多个独立模块同时分析

**调用示例**：
```
同时调用多个 Hunter：
- Task(subagent_type="deconstructors-hunter", prompt="分析用户模块...")
- Task(subagent_type="deconstructors-hunter", prompt="分析订单模块...")
- Task(subagent_type="deconstructors-hunter", prompt="分析支付模块...")
```

## 示例4：快速扫描模式

**适用场景**：用户只需要快速了解项目概况

**调用示例**：
```
Step 1: Task(subagent_type="deconstructors-profiler", prompt="快速扫描技术栈...")
Step 2: Task(subagent_type="deconstructors-strategist", prompt="基于扫描结果提供概要分析...")
```

## 示例5：动态调整

**场景**：执行中发现新问题

**应对**：
- 原计划单专家，发现需要设计 → 切换链式
- 原计划链式，某环节简单 → 跳过或合并
- 发现遗漏专家能力 → 临时调整策略
- 遇到复杂问题 → 使用 AskUserQuestion 与用户确认

---

**关键**：以上都是示例，协调器应保持灵活性，不被预设限制
