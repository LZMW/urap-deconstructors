# 安装指南

## 前置要求

- Claude Code CLI 已安装
- 有写入 `~/.claude/` 目录的权限

---

## 安装步骤

### 方法一：命令行安装（推荐）

```bash
# 进入配置包目录
cd N:/编程备份/4.0团队/deconstructors-team

# 1. 复制专家 Agent 配置
cp agents/*.md ~/.claude/agents/

# 2. 复制协调器 Skill 配置
cp -r skills/deconstructors-coordinator ~/.claude/skills/
```

### 方法二：手动复制

1. **复制 Agent 配置**
   - 将 `agents/` 目录下的所有 `.md` 文件
   - 复制到 `~/.claude/agents/` 目录

2. **复制 Skill 配置**
   - 将 `skills/deconstructors-coordinator/` 整个目录
   - 复制到 `~/.claude/skills/` 目录

---

## 验证安装

### 1. 检查文件是否正确安装

```bash
# 检查 Agent 配置
ls ~/.claude/agents/deconstructors-*.md

# 预期输出：
# deconstructors-profiler.md
# deconstructors-strategist.md
# deconstructors-scribe.md
# deconstructors-hunter.md

# 检查 Skill 配置
ls ~/.claude/skills/deconstructors-coordinator/

# 预期输出：
# skill.md
```

### 2. 重启 Claude Code 会话

安装后**必须**重启 Claude Code 会话才能加载新配置：

1. 退出当前 Claude Code 会话
2. 重新启动 Claude Code
3. 新配置将自动加载

### 3. 验证配置加载

启动新会话后，可以尝试以下命令验证：

```
用户: /deconstructors-coordinator 分析当前项目
```

如果协调器正常响应，说明配置已成功加载。

---

## 卸载

```bash
# 删除 Agent 配置
rm ~/.claude/agents/deconstructors-*.md

# 删除 Skill 配置
rm -rf ~/.claude/skills/deconstructors-coordinator
```

卸载后需要重启 Claude Code 会话。

---

## 故障排查

### 问题1：专家无法触发

**可能原因**：配置文件未正确复制

**解决方案**：
```bash
# 检查文件是否存在
ls -la ~/.claude/agents/deconstructors-*.md

# 如果文件不存在，重新复制
cp agents/*.md ~/.claude/agents/
```

### 问题2：协调器无响应

**可能原因**：Skill 目录结构不正确

**解决方案**：
```bash
# 确保 skill.md 在正确的目录结构中
ls ~/.claude/skills/deconstructors-coordinator/skill.md

# 如果目录结构不对，重新复制
cp -r skills/deconstructors-coordinator ~/.claude/skills/
```

### 问题3：修改配置后不生效

**解决方案**：重启 Claude Code 会话

---

## 文件位置说明

| 文件类型 | 安装位置 | 说明 |
|----------|----------|------|
| Agent 配置 | `~/.claude/agents/` | 专家成员的配置文件 |
| Skill 配置 | `~/.claude/skills/` | 协调器的配置目录 |

---

## 版本信息

- **团队版本**：4.0
- **协议版本**：U.R.A.P v4.0
- **更新日期**：2026-03-02
