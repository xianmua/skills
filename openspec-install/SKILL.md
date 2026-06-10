---
name: openspec
description: OpenSpec 项目初始化和管理工具。当用户首次使用 openspec、需要安装 openspec、或者需要了解 openspec 基本使用时触发。帮助你检查安装状态、安装或初始化 openspec、以当前编辑器配置重命名，并提供基本使用指导。
license: MIT
compatibility: 需要 Node.js 18+ 和 npm/pnpm。
metadata:
  author: custom
  version: "1.0"
---

OpenSpec 安装、初始化和基础使用指南。

我将帮助你：
1. 检查 openspec 是否已安装
2. 如未安装，安装 openspec 到项目中
3. 初始化 openspec 配置
4. 提供基本使用方法和最佳实践

---

## 步骤

### 第1步：检查 openspec 是否已安装

首先检查 openspec CLI 是否可用：

```bash
which openspec-cn || npm list -g @studyzy/openspec-cn
```

如果不可用，检查项目中是否已初始化（查看 openspec 目录是否存在）：

```bash
ls -la openspec/ 2>/dev/null || echo "openspec directory not found"
```

### 第2步：处理未安装的情况

**如果 openspec 未安装，安装步骤如下：**

1. **优先使用 Volta 安装**（如果可用）：
```bash
volta install @studyzy/openspec-cn@latest
```

2. **如果没有 Volta，使用 npm 全局安装**：
```bash
npm install -g @studyzy/openspec-cn@latest
```

3. **验证安装**：
```bash
openspec-cn --version
```

### 第3步：初始化 openspec 项目

**如果 openspec 目录不存在，执行初始化：**

```bash
openspec-cn init  --tools claude
```

这将创建默认的 openspec 目录结构：
```
openspec/
├── changes/      # 变更目录
├── specs/        # 规格说明目录
├── config.yaml   # 主配置文件
```

### 第4步：编辑器配置重命名

**根据你使用的编辑器进行配置（当前检测到的编辑器：comate）：**

将 `.claude` 重命名为 `.comate`, 如果 `.claude` 或当前检测到的编辑器原本就存在，就不要重命名，而是将 `.claude` 中 `openspec` 的 `commands` 和 `skills` 剪切到当前检测到的编辑器（comate）中， 

---

## OpenSpec 基本使用

### 常用命令

| 命令 | 说明 |
|------|------|
| `openspec-cn list` | 列出所有变更 |
| `openspec-cn new change <name>` | 创建新变更 |
| `openspec-cn status` | 查看变更状态 |
| `openspec-cn instructions <artifact>` | 获取产出物指令 |

### 工作流程

```
1. 探索阶段（/opsx:explore）
   └── 自由思考、澄清需求

2. 提案阶段（/opsx:new）
   └── 创建 proposal.md, design.md, tasks.md

3. 实现阶段（/opsx:apply）
   └── 执行任务，实现功能

4. 归档阶段（/opsx:archive）
   └── 完成变更，归档产出物
```

### 变更产出物

每个变更包含以下产出物：

| 产出物 | 说明 |
|--------|------|
| `proposal.md` | 变更提案（什么和为什么）|
| `design.md` | 设计文档（如何）|
| `tasks.md` | 任务列表（实现步骤）|
| `spec.md` | 规格说明 |

---

## 典型场景

### 场景1：开始新功能

```
1. 用户：我想添加用户认证功能
2. 你：/opsx:new add-user-auth
3. 按照指引创建 proposal → design → tasks
4. 用户：准备好了
5. 你：/opsx:apply add-user-auth
6. 执行任务，完成实现
7. 你：/opsx:archive add-user-auth
```

### 场景2：中途遇到问题

```
用户：我卡在 OAuth 集成上，太复杂了
你：/opsx:explore add-user-auth
   → 探索问题，澄清方案
   → 建议更新 design 或添加探针任务
```

### 场景3：需求变更

```
用户：范围要改变，不仅是高级用户
你：阅读当前 design.md
   → 讨论新范围的影响
   → 建议更新 proposal 和 design
```

---

## 最佳实践

1. **先探索，再提案**
   - 不要急于创建变更，先用 /opsx:explore 澄清需求
   - 探索模式是免费的思考时间

2. **保持产出物 small**
   - proposal 控制在 500 字以内
   - 每个任务 2 小时内完成

3. **频繁归档**
   - 完成的变更及时归档
   - 保持变更目录整洁

4. **使用配置**
   - 根据编辑器配置使用对应的 config 文件
   - 利用 project.md 记录项目上下文

---

## 护栏

- 如果 openspec 已安装并初始化，直接告知用户现有状态
- 如果用户只想了解基本使用，不需要执行安装步骤
- 尊重用户的选择，不强制安装