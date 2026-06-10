---
name: fmt
description: 代码格式化工具 - 自动格式化代码，支持多种语言和工具
---

# 代码格式化 Skill

## 触发条件
当用户提到以下场景时触发：
- "格式化代码"、"format code"、"fmt"
- "整理代码格式"、"美化代码"
- "缩进"、"indent"
- 需要对代码应用 lint/format 规则时

## 支持的语言和格式化工具

### Python
- **工具**: black, autopep8, yapf
- **命令示例**: `black src/`, `autopep8 --in-place file.py`

### JavaScript/TypeScript
- **工具**: prettier, eslint (--fix)
- **命令示例**: `npx prettier --write src/**/*.js`, `eslint --fix .`

### Go
- **工具**: gofmt, goimports
- **命令示例**: `gofmt -w file.go`, `goimports -w file.go`

### Rust
- **工具**: rustfmt
- **命令示例**: `cargo fmt`

### Java
- **工具**: google-java-format
- **命令示例**: `google-java-format -i file.java`

### C/C++
- **工具**: clang-format
- **命令示例**: `clang-format -i file.c`

### CSS/SCSS
- **工具**: prettier, stylelint
- **命令示例**: `npx prettier --write "**/*.css"`

### 通用
- **工具**: prettier (多语言支持)
- **命令示例**: `npx prettier --write .`

## 使用方法

### 1. 检测项目配置
首先检查项目中是否已有格式化配置：
- `.prettierrc` / `prettier.config.js`
- `.editorconfig`
- `pyproject.toml` (black 配置)
- `.rustfmt.toml`
- `Makefile` 中的 fmt 目标

### 2. 优先使用项目配置
如果项目已有格式化配置，优先使用项目自带的工具和配置。

### 3. 应用格式化
根据文件类型选择合适的工具进行格式化。

## 工作流程

1. **识别语言**: 根据文件扩展名判断语言类型
2. **检查配置**: 查找项目中的格式化配置文件
3. **选择工具**: 根据语言和配置选择合适的格式化工具
4. **执行格式化**: 运行格式化命令
5. **验证结果**: 确认格式化成功，无错误

## 常见场景处理

### 场景1: 格式化单个文件
```bash
# 使用项目配置的格式化工具
npx prettier --write src/index.js
```

### 场景2: 格式化整个目录
```bash
# Python
black src/

# JavaScript
npx prettier --write src/

# Go
gofmt -w .
```

### 场景3: 批量格式化多种语言
```bash
# 使用 prettier 处理多种语言
npx prettier --write "src/**/*.{js,ts,jsx,tsx,css,md}"
```

### 场景4: 只检查格式（不修改）
```bash
npx prettier --check src/
black --check src/
```

## 注意事项

- **不修改语义**: 格式化只改变代码风格，不改变逻辑
- **保留 git 历史**: 格式化后建议单独提交，避免与功能修改混在一起
- **CI 集成**: 建议在 CI 中配置格式化检查，确保团队代码风格一致
- **配置一致性**: 团队应统一使用相同的格式化配置

## 错误处理

- **工具未安装**: 提示用户安装对应的格式化工具
- **配置冲突**: 优先使用项目配置文件，覆盖默认设置
- **格式化失败**: 显示具体错误信息，帮助用户修复