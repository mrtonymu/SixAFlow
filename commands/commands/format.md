# 自动格式化代码 - Trae版本

我将使用项目配置的格式化工具来格式化你的代码。

我会通过分析配置文件和项目结构自动检测你项目的格式化工具，而不假设特定技术。

我只会格式化修改过的文件，以避免不必要的更改并专注于你当前的工作。

如果没有配置格式化工具，我会为你的项目类型建议合适的选项，并提供使用语言约定进行格式化。

格式化后，我会显示更改内容并确保代码遵循你项目建立的样式模式。

如果格式化遇到问题，我会提供具体的错误详情并建议解决方案。

这能高效地根据你项目的标准维护一致的代码风格。

## Trae使用示例

```bash
# 1. 检测项目格式化配置
search_by_regex "prettier|eslint|black|gofmt|rustfmt" # 查找配置文件
view_files package.json # 检查格式化脚本
view_files .prettierrc # 检查Prettier配置
view_files .eslintrc # 检查ESLint配置

# 2. 检查修改的文件
run_command "git diff --name-only" # 查看修改的文件
run_command "git status --porcelain" # 查看工作区状态

# 3. 根据项目类型运行格式化
# JavaScript/TypeScript项目
run_command "npx prettier --write ."
run_command "npx eslint --fix ."

# Python项目
run_command "black ."
run_command "isort ."

# Go项目
run_command "gofmt -w ."
run_command "go mod tidy"

# Rust项目
run_command "cargo fmt"

# 4. 验证格式化结果
run_command "git diff --stat" # 查看更改统计
run_command "git diff" # 查看具体更改

# 5. 提交格式化更改
run_command "git add -A && git commit -m 'style: format code'"
```

## 支持的格式化工具

### JavaScript/TypeScript
- **Prettier**: 代码格式化
- **ESLint**: 代码质量和风格
- **Standard**: JavaScript标准风格

### Python
- **Black**: 代码格式化
- **isort**: 导入排序
- **autopep8**: PEP8格式化
- **yapf**: 代码格式化

### Go
- **gofmt**: 官方格式化工具
- **goimports**: 导入管理
- **golangci-lint**: 综合检查

### Rust
- **rustfmt**: 官方格式化工具
- **clippy**: 代码检查

### 其他语言
- **clang-format**: C/C++
- **rubocop**: Ruby
- **mix format**: Elixir
- **dartfmt**: Dart

## 配置文件检测

```bash
# 检测常见配置文件
search_by_regex "\.(prettierrc|eslintrc|editorconfig|clang-format)"
view_files .prettierrc.json
view_files .eslintrc.js
view_files pyproject.toml
view_files rustfmt.toml
```

## 格式化策略

1. **检测项目类型**
   - 查看package.json、requirements.txt等
   - 识别主要编程语言
   - 检测现有配置文件

2. **选择格式化工具**
   - 优先使用项目配置的工具
   - 回退到语言默认工具
   - 提供配置建议

3. **执行格式化**
   - 只格式化修改的文件
   - 保持现有风格一致性
   - 避免大规模更改

4. **验证结果**
   - 检查格式化是否成功
   - 确保没有语法错误
   - 显示更改摘要