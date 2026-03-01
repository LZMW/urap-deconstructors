# 解构重筑者 (Deconstructors) 团队

**版本**：3.0
**框架**：U.R.A.P (Understand-Recognize-Analyze-Present)
**团队类型**：流水线型（链式传递）
**最后更新**：2026-03-01

---

## 📋 团队简介

解构重筑者是专门的代码逆向分析与文档生成团队，遵循 **U.R.A.P v4.0 协议**，通过"环境指纹识别 → 智能策略生成 → 全景文档构建"的流水线流程，将任何陌生的代码库转化为可传承的知识资产。

**核心使命**：让后来者在完全脱离原作者的情况下，仅凭文档即可掌握系统全貌。

---

## 🎯 核心能力

| 能力领域 | 说明 | 专家 |
|----------|------|------|
| 技术栈识别 | 环境探测、依赖分析、项目结构理解 | Profiler |
| 策略制定 | 分析方法选择、文档架构设计、任务拆解 | Strategist |
| 代码分析 | 调用链追踪、算法挖掘、数据流分析 | Hunter |
| 文档生成 | 知识固化、质量验收、新人指南编写 | Scribe |

---

## 👥 团队成员

| 代号 | 角色 | 核心能力 | U.R.A.P阶段 |
|------|------|----------|-------------|
| **Profiler** | 指纹识别者 | 环境探测、技术栈识别、依赖分析 | Phase 1 |
| **Strategist** | 策略制定者 | 分析规划、文档架构、任务拆解 | Phase 2 |
| **Hunter** | 逻辑猎人 | 代码分析、调用追踪、逻辑挖掘 | Phase 4 |
| **Scribe** | 全景记录员 | 文档创建、知识固化、质量验收 | Phase 3 & 5 |

---

## 🔄 U.R.A.P 框架

```
Phase 1: Understand（理解）→ Profiler
  输出：技术栈指纹报告
       ↓

Phase 2: Recognize（识别）→ Strategist
  输出：分析策略声明
       ↓

Phase 3: Analyze - Skeleton（分析-骨架）→ Scribe
  输出：文档架构体系
       ↓

Phase 4: Analyze - Deep（分析-深度）→ Hunter
  输出：结构化知识
       ↓

Phase 5: Present（呈现）→ Scribe
  输出：完整文档体系 + 质量验收报告
```

---

## 📂 信息传递机制

**模式**：流水线型（链式传递）

**目录结构**：
```
{项目}/.deconstructors/
├── phases/                    # 阶段产出
│   ├── 01_profiler/          # Phase 1 指纹扫描
│   ├── 02_strategist/        # Phase 2 策略定调
│   ├── 03_scribe/            # Phase 3 骨架构建
│   ├── 04_hunter/            # Phase 4 深度狩猎
│   └── 05_scribe/            # Phase 5 知识固化
├── inbox.md                   # 统一消息收件箱
└── summary.md                 # 最终项目汇总
```

**链式传递要求**：
- 第一个成员（Profiler）：不需要读取前序，直接生成阶段产出
- 中间成员（Strategist, Hunter, Scribe Phase 3）：必须读取前序 INDEX.md，基于前序输出工作
- 最后成员（Scribe Phase 5）：读取前序并生成最终汇总报告

---

## 🔧 MCP 工具能力

| 代号 | 可授权的MCP工具 | 授权条件 |
|------|-----------------|----------|
| Profiler | mcp__context7__* | Phase 1指纹扫描需要查询技术栈文档时 |
| Strategist | mcp__sequential-thinking__*, mcp__context7__*, mcp__aurai-advisor__* | Phase 2策略制定需要深度推导或上级指导时 |
| Hunter | mcp__sequential-thinking__*, mcp__context7__*, mcp__aurai-advisor__* | Phase 4深度狩猎需要复杂分析或上级指导时 |
| Scribe | 无 | 不使用MCP |

**三级授权机制**：
- 🔴 **必要级**：任务核心依赖，"必须使用"
- 🟡 **推荐级**：显著提升质量，"建议主动使用"
- 🟢 **可选级**：锦上添花，"可使用"

---

## 📖 使用指南

### 快速开始

```bash
# 触发完整 U.R.A.P 流程
/deconstructors-coordinator
```

### 触发关键词

协调器会在以下场景被触发：

- **全流程分析**：逆向分析、文档生成、系统分析
- **技术栈识别**：技术栈识别、环境探测、依赖分析
- **分析策略**：策略制定、分析规划、任务拆解
- **代码理解**：代码分析、调用追踪、逻辑挖掘
- **文档编写**：文档编写、知识固化、质量验收

---

## 🎯 质量标准

### 新人测试标准

**核心问题**：如果一名刚入职的初级工程师，断网且无法联系原作者，他能否仅凭这套文档搭建起环境，跑通主要功能，并找到修改代码的地方？

#### 验收清单

```
全貌理解：
[?] 能否快速理解系统的定位和核心功能？
[?] 能否掌握技术栈和依赖关系？
[?] 能否理解目录结构和模块职责？

环境搭建：
[?] 能否按照文档成功搭建开发环境？
[?] 能否正确安装所有依赖？
[?] 能否解决常见的环境配置问题？

功能运行：
[?] 能否运行系统并看到预期效果？
[?] 能否执行主要功能流程？
[?] 能否理解和处理常见错误？

代码修改：
[?] 能否快速定位需要修改的代码位置？
[?] 能否理解核心业务逻辑？
[?] 能否安全地进行代码修改？
```

---

## 📦 配置包结构

```
deconstructors-team/
├── README.md                      # 本文件
├── INSTALL.md                     # 安装指南
├── agents/
│   ├── deconstructors-profiler.md  # Profiler 配置
│   ├── deconstructors-strategist.md # Strategist 配置
│   ├── deconstructors-hunter.md    # Hunter 配置
│   └── deconstructors-scribe.md    # Scribe 配置
└── skills/
    └── deconstructors-coordinator/
        └── skill.md               # 协调器 Skill
```

---

## 🚀 安装说明

详细安装步骤请参阅 [INSTALL.md](INSTALL.md)

**快速安装**：
1. 复制 `agents/` 中的4个 `.md` 文件到 `~/.claude/agents/`
2. 复制 `skills/deconstructors-coordinator/` 目录到 `~/.claude/skills/`
3. 重启 Claude Code 或刷新技能列表

---

## 📝 更新日志

### v3.0 (2026-03-01)
- ✨ 采用超级团队构建器 3.0 模板
- ✨ 新增标准化触发指令格式（📂📋🔓）
- ✨ 新增三级MCP授权机制
- ✨ 新增调度指令理解章节
- 🎨 优化信息传递机制说明
- 🎨 完善质量验收标准

### v2.0
- ✨ 引入 U.R.A.P v4.0 协议
- ✨ 新增双维质量验收标准
- 🎨 优化专家角色定位

### v1.0
- 🎉 初始版本发布

---

## 📄 许可证

本团队配置包遵循与 Claude Code 相同的许可证。

---

## 🤝 贡献

如发现问题或有改进建议，欢迎反馈。

**联系方式**：通过 Claude Code 反馈渠道提交

---

*"如果新人看不懂，这篇文档就是废纸。"* — Scribe
