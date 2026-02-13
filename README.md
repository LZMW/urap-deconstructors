<div align="center">

# 解构重筑者
### The Deconstructors

**U.R.A.P v4.0 通用逆向分析与智能文档构建专家团队**

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-blue)](https://code.claude.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-2.0-orange.svg)]()
[![U.R.A.P](https://img.shields.io/badge/Protocol-U.R.A.P%20v4.0-purple.svg)]()

</div>

---

## 免责声明

本工具仅供合法用途（自己拥有的代码库、开源项目学习、授权审计、教育研究）。严禁用于逆向商业软件破解、侵犯知识产权等非法活动。使用本工具进行非法活动，后果自负。

---

## 简介

**解构重筑者** 是一个遵循 **U.R.A.P v4.0 协议** 的智能专家团队系统，通过「环境指纹识别 → 智能策略生成 → 全景文档构建」的动态流程，将任何陌生的代码库转化为可传承的知识资产。

> **核心使命**：让后来者在完全脱离原作者的情况下，仅凭文档即可掌握系统全貌。

---

## 架构说明

### 协调器 Skill 与专家 Agent 的关系

```
┌─────────────────────────────────────────────────────────────────────┐
│                        Claude Code 主代理                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ┌─────────────────────────────────────────────────────────────┐  │
│   │           协调器 Skill (deconstructors-coordinator)          │  │
│   │                                                             │  │
│   │   • 运行在主代理层面，拥有完整的工具权限                        │  │
│   │   • 接收用户任务，分析需求，制定执行计划                        │  │
│   │   • 通过自然语言触发专家 Agent 执行具体工作                    │  │
│   │   • 不自己干活，只负责协调和分配                               │  │
│   │                                                             │  │
│   └───────────────────────┬─────────────────────────────────────┘  │
│                           │ 自然语言触发                            │
│           ┌───────────────┼───────────────┐                        │
│           ▼               ▼               ▼                        │
│   ┌───────────┐   ┌───────────┐   ┌───────────┐                   │
│   │  Agent    │   │  Agent    │   │  Agent    │   ...             │
│   │ Profiler  │   │Strategist │   │  Hunter   │                   │
│   │           │   │           │   │           │                   │
│   │ • 子代理   │   │ • 子代理   │   │ • 子代理   │                   │
│   │ • 执行任务 │   │ • 执行任务 │   │ • 执行任务 │                   │
│   │ • 返回结果 │   │ • 返回结果 │   │ • 返回结果 │                   │
│   └───────────┘   └───────────┘   └───────────┘                   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 关键机制

| 组件 | 类型 | 作用 | 能否触发其他Agent |
|------|------|------|------------------|
| **协调器 Skill** | Skill | 任务入口，分析需求，协调专家 | 可以（运行在主代理层面） |
| **专家 Agent** | Agent | 执行具体任务 | 不可以（子代理无法调用其他子代理） |

### 为什么协调器必须是 Skill？

Claude Code 有一个关键限制：**子代理（Agent）无法调用其他子代理**。

因此我们将协调器设计为 **Skill**（运行在主代理层面），这样它就可以自由触发专家 Agent，实现多专家协作。

---

## 专家团队

| 专家 | 代号 | 职责 | 阶段 |
|:----:|:----:|:-----|:----:|
| Profiler | 扫描仪 | 环境指纹识别、技术栈分析 | Phase 1 |
| Strategist | 军师 | 智能策略生成、任务规划 | Phase 2 |
| Scribe | 史官 | 文档架构 + 知识固化 | Phase 3/5 |
| Hunter | 猎手 | 代码分析、逻辑挖掘 | Phase 4 |

---

## 快速开始

### 安装

```bash
# 1. 复制专家 agent 配置到 ~/.claude/agents/
cp agents/*.md ~/.claude/agents/

# 2. 复制协调器 skill 到 ~/.claude/skills/
cp -r skills/deconstructors-coordinator ~/.claude/skills/
```

### 重启会话

安装后需要重启 Claude Code 会话才能加载新配置。

---

## 如何使用

### 方式一：通过协调器（推荐）

直接向 Claude Code 描述你的需求，协调器会自动分析并分配给合适的专家：

```
用户: 帮我分析这个项目的技术栈和架构
用户: 为这个代码库生成完整的开发文档
用户: 我需要理解这个模块的调用关系
```

协调器会：
1. 分析你的需求
2. 制定执行计划
3. 依次触发专家 Agent 完成任务
4. 汇总结果交付

### 方式二：直接调用专家

如果你想跳过协调器，直接调用特定专家：

```
用户: 使用 deconstructors-profiler 扫描项目技术栈
用户: 让 deconstructors-hunter 分析这个模块的代码逻辑
用户: 请 deconstructors-scribe 为我创建 API 文档
```

### 方式三：触发协调器 Skill

```
用户: /deconstructors-coordinator 分析当前项目并生成文档
```

---

## 协作示例

### 示例1：完整项目分析

```
用户: 分析这个 Python 项目，生成开发文档

协调器的工作流程:
┌────────────────────────────────────────────────────────────┐
│ Step 1: 触发 Profiler 扫描技术栈                            │
│         → 输出: 技术栈指纹报告（Python 3.10, FastAPI, ...）  │
│                                                            │
│ Step 2: 触发 Strategist 制定分析策略                        │
│         → 输出: 分析策略声明（按模块分析，重点关注API层）     │
│                                                            │
│ Step 3: 触发 Scribe 初始化文档骨架                          │
│         → 输出: 文档目录结构                                │
│                                                            │
│ Step 4: 触发 Hunter 深度分析代码                            │
│         → 输出: 结构化知识（模块职责、调用关系、核心逻辑）     │
│                                                            │
│ Step 5: 触发 Scribe 填充文档                                │
│         → 输出: 完整的开发文档                              │
└────────────────────────────────────────────────────────────┘
```

### 示例2：单任务调用

```
用户: 使用 profiler 扫描这个项目用了什么技术

协调器:
  分析需求 → 识别为技术栈扫描任务 → 触发 deconstructors-profiler

Profiler Agent:
  扫描 package.json, requirements.txt, go.mod 等
  分析目录结构和配置文件
  输出技术栈指纹报告
```

---

## 文件结构

```
deconstructors-team/
├── README.md                          # 本文档
├── INSTALL.md                         # 安装说明
├── agents/                            # 专家 Agent 配置
│   ├── deconstructors-profiler.md     # 技术栈扫描专家
│   ├── deconstructors-strategist.md   # 策略制定专家
│   ├── deconstructors-scribe.md       # 文档编写专家
│   └── deconstructors-hunter.md       # 代码分析专家
└── skills/                            # 协调器 Skill 配置
    └── deconstructors-coordinator/
        ├── skill.md                   # 协调器主文件
        └── references/
            └── patterns-examples.md   # 协作模式参考
```

---

## 注意事项

1. **重启生效**：修改配置后需重启 Claude Code 会话
2. **委托优先**：协调器只协调，不自己执行任务
3. **合法使用**：仅用于合法的代码分析和文档生成

---

## 许可证

本项目采用 [MIT](LICENSE) 许可证。

---

<div align="center">

**解构重筑者 - 让知识得以传承**

</div>
