# 解构重筑者团队 - 安装说明

## 系统要求

- Claude Code CLI 或兼容的 AI 编程助手
- 支持 YAML 前置元数据的 Markdown 解析能力
- 推荐模型：GLM5、Claude Opus/Sonnet 等中文友好模型

## 安装步骤

### 步骤 1：安装专家 Agent

```bash
# Windows (Git Bash / PowerShell)
mkdir -p ~/.claude/agents
cp agents/deconstructors-profiler.md ~/.claude/agents/
cp agents/deconstructors-strategist.md ~/.claude/agents/
cp agents/deconstructors-scribe.md ~/.claude/agents/
cp agents/deconstructors-hunter.md ~/.claude/agents/

# macOS / Linux
mkdir -p ~/.claude/agents
cp agents/deconstructors-*.md ~/.claude/agents/
```

### 步骤 2：安装协调器 Skill

```bash
# Windows (Git Bash / PowerShell)
mkdir -p ~/.claude/skills
cp -r skills/deconstructors-coordinator ~/.claude/skills/

# macOS / Linux
mkdir -p ~/.claude/skills
cp -r skills/deconstructors-coordinator ~/.claude/skills/
```

### 步骤 3：验证安装

```bash
# 检查 agents
ls ~/.claude/agents/deconstructors-*.md

# 应输出：
# deconstructors-profiler.md
# deconstructors-strategist.md
# deconstructors-scribe.md
# deconstructors-hunter.md

# 检查 skill
ls ~/.claude/skills/deconstructors-coordinator/

# 应输出：
# skill.md
# references/
```

## 生效方式

**重要**：修改或新增配置文件后，需要重启 Claude Code 会话才能加载新配置。

1. 关闭当前 Claude Code 会话
2. 重新启动 Claude Code
3. 新配置将自动加载

## 使用测试

启动新会话后，测试团队是否正常工作：

```
用户：/deconstructors-coordinator 帮我分析当前目录的技术栈

预期：协调器启动 Profiler 进行技术栈扫描
```

或直接调用专家：

```
用户：/deconstructors-profiler 扫描当前项目的技术栈

预期：Profiler 输出技术栈指纹报告
```

## 配置说明

### 专家工具权限

| 专家 | 工具 | 权限级别 |
|------|------|----------|
| Profiler | Read, Glob, Grep, Bash | 只读 + 执行 |
| Strategist | Read, Glob, Grep, Bash | 只读 + 执行 |
| Hunter | Read, Glob, Grep, Bash, LSP | 只读 + 执行 |
| Scribe | Read, Glob, Grep, Write, Edit, Bash | 写入 + 执行 |

### 模型配置

所有专家默认使用 `sonnet` 模型。可根据需要修改配置文件中的 `model` 字段：

```yaml
model: opus    # 更强推理能力
model: haiku   # 更快响应速度
model: inherit # 继承父会话模型
```

## 故障排除

### 问题1：专家未被识别

**症状**：调用 `/deconstructors-profiler` 无反应

**解决方案**：
1. 确认配置文件位于正确目录
2. 确认已重启会话
3. 检查配置文件格式是否正确
4. 确认 YAML 前置元数据格式无误

### 问题2：协调器无法调用专家

**症状**：协调器只输出文字，不调用其他专家

**解决方案**：
1. 确认所有专家配置文件都已复制
2. 确认专家配置文件名称包含 `deconstructors-` 前缀
3. 确认协调器 skill 中的 subagent_type 与专家名称匹配

### 问题3：中文输出乱码

**症状**：文档中出现乱码

**解决方案**：
确保所有配置文件使用 UTF-8 编码保存。

## 卸载

### 用户级卸载

```bash
# Windows (Git Bash)
rm ~/.claude/agents/deconstructors-*.md
rm -rf ~/.claude/skills/deconstructors-coordinator

# macOS / Linux
rm ~/.claude/agents/deconstructors-*.md
rm -rf ~/.claude/skills/deconstructors-coordinator
```

## 更新日志

### v2.0.0 (2025)
- 协调器从 Agent 改为 Skill 架构
- 专家名称添加团队前缀避免重名
- 新增 patterns-examples.md 参考文档
- 强调委托优先原则

### v1.0.0 (2024)
- 基于 U.R.A.P v4.0 协议构建
- 包含 4 位专家 + 1 位协调器
- 实现五阶段标准流水线
- 双维质量验收标准

---

如有问题，请参考 [README.md](README.md) 或查看配置文件中的详细说明。
