# 解构重筑者团队安装指南

**版本**：3.0
**平台**：Claude Code
**最后更新**：2026-03-01

---

## 📋 前置要求

- 已安装 Claude Code
- 了解 Claude Code 技能和代理配置位置
- **重要**：本机安装，不留老版本备份

---

## 🚀 快速安装

### 步骤 1：备份现有配置（可选）

如果之前已安装旧版本解构重筑者团队，建议先备份：

```bash
# Windows PowerShell
Copy-Item -Path "$env:USERPROFILE\.claude\agents\deconstructors-*.md" -Destination "$env:USERPROFILE\.claude\agents\backup\" -Recurse
Copy-Item -Path "$env:USERPROFILE\.claude\skills\deconstructors-coordinator" -Destination "$env:USERPROFILE\.claude\skills\backup\" -Recurse

# Linux/macOS
mkdir -p ~/.claude/agents/backup ~/.claude/skills/backup
mv ~/.claude/agents/deconstructors-*.md ~/.claude/agents/backup/
mv ~/.claude/skills/deconstructors-coordinator ~/.claude/skills/backup/
```

### 步骤 2：复制专家 Agent 配置

```bash
# Windows PowerShell
Copy-Item -Path "N:\编程备份\3.0团队\deconstructors-team\agents\*.md" -Destination "$env:USERPROFILE\.claude\agents\"

# Linux/macOS
cp "N:/编程备份/3.0团队/deconstructors-team/agents/"*.md ~/.claude/agents/
```

**确认文件已复制**：
- `deconstructors-profiler.md`
```

**确认目录结构**：
```
~/.claude/skills/deconstructors-coordinator/
└── skill.md
```

### 步骤 4：验证安装

1. **重启 Claude Code** 或刷新技能列表
2. **检查技能列表**：输入 `/` 查看 `deconstructors-coordinator` 是否在列表中
3. **测试触发**：
   ```
   帮我分析这个项目的技术栈
   ```
   应该能看到解构重筑者协调器被触发

---

## 📂 配置文件详解

### Agent 配置文件结构

每个 `.md` 文件包含：

```yaml
---
name: deconstructors-[expert-name]
description: "使用场景描述..."
tools: [工具列表]
model: sonnet
color: [颜色]
---

# [专家角色]

## 核心职责
...

## 调度指令理解
...
```

### Skill 配置文件结构

```yaml
---
name: deconstructors-coordinator
description: 协调器描述...
---

# 协调器说明

## 核心原则
...

## 执行流程
...
```

---

## 🔧 配置验证

### 验证清单

安装完成后，请确认：

- [ ] 4个 Agent 配置文件已复制到 `~/.claude/agents/`
- [ ] 协调器 Skill 目录已复制到 `~/.claude/skills/`
- [ ] 重启 Claude Code 后可以看到 `deconstructors-coordinator` 技能
- [ ] 触发测试正常工作

### 测试命令

**测试1：技术栈识别**
```
帮我识别这个项目的技术栈
```

**测试2：完整流程**
```
帮我分析这个项目并生成文档
```

---

## 🗑️ 卸载说明

如需卸载解构重筑者团队：

```bash
# Windows PowerShell
Remove-Item -Path "$env:USERPROFILE\.claude\agents\deconstructors-*.md"
Remove-Item -Path "$env:USERPROFILE\.claude\skills\deconstructors-coordinator" -Recurse

# Linux/macOS
rm ~/.claude/agents/deconstructors-*.md
rm -rf ~/.claude/skills/deconstructors-coordinator
```

---

## ⚙️ 高级配置

### 自定义 MCP 工具授权

如需自定义各成员的 MCP 工具权限，编辑对应的 `.md` 文件：

1. 打开 `~/.claude/agents/deconstructors-[expert-name].md`
2. 修改 `tools:` 字段，添加/删除 MCP 工具
3. 保存文件

### 自定义协调器行为

如需自定义协调器的执行流程，编辑 `~/.claude/skills/deconstructors-coordinator/skill.md`：

1. 打开文件
2. 修改执行流程章节
3. 保存文件
4. 重启 Claude Code

---

## 🐛 故障排查

### 问题1：技能不显示

**症状**：输入 `/` 后看不到 `deconstructors-coordinator`

**可能原因**：
1. Skill 文件未正确复制
2. Skill 目录结构不正确
3. Claude Code 未刷新

**解决方法**：
1. 确认 `~/.claude/skills/deconstructors-coordinator/skill.md` 文件存在
2. 重启 Claude Code
3. 如果还不行，检查 `skill.md` 文件格式是否正确

### 问题2：Agent 触发失败

**症状**：协调器尝试触发 Agent 时失败

**可能原因**：
1. Agent 配置文件未正确复制
2. Agent 配置文件格式错误

**解决方法**：
1. 确认 `~/.claude/agents/` 目录下有4个 `deconstructors-*.md` 文件
2. 检查文件格式是否正确（YAML frontmatter + Markdown 内容）
3. 重启 Claude Code

### 问题3：MCP 工具无法使用

**症状**：Agent 提示无权限使用 MCP 工具

**可能原因**：
1. 协调器未授权 MCP 工具
2. Agent 的 tools 字段未声明 MCP 工具

**解决方法**：
1. 协调器触发 Agent 时需包含 `🔓 MCP 授权` 声明
2. 检查 Agent 配置文件的 `tools:` 字段是否包含对应 MCP 工具

---

## 📞 获取帮助

如遇到安装问题：

1. 查看 [README.md](README.md) 了解团队详情
2. 查看 Claude Code 官方文档
3. 通过 Claude Code 反馈渠道提交问题

---

## ✅ 安装完成

安装完成后，解构重筑者团队将：

- ✅ 自动识别项目技术栈
- ✅ 智能制定分析策略
- ✅ 深度分析代码逻辑
- ✅ 生成高质量文档
- ✅ 执行双维质量验收

**开始使用**：
```
/deconstructors-coordinator
```

---

*"好的开始是成功的一半。"* — 化名
