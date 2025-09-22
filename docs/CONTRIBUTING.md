# 贡献指南 - Trae智能命令集

欢迎为Trae智能命令集项目做出贡献！本指南将帮助您了解如何参与项目开发、提交代码和改进文档。

## 📋 目录
- [开始贡献](#开始贡献)
- [开发环境设置](#开发环境设置)
- [贡献类型](#贡献类型)
- [开发流程](#开发流程)
- [代码规范](#代码规范)
- [测试指南](#测试指南)
- [文档贡献](#文档贡献)
- [社区准则](#社区准则)

## 🚀 开始贡献

### 前置要求
- 熟悉Git和GitHub工作流
- 了解Shell脚本编程
- 理解Markdown文档格式
- 具备基本的软件开发经验

### 快速开始
1. **Fork项目仓库**
   ```bash
   # 在GitHub上Fork项目
   # 克隆您的Fork到本地
   git clone https://github.com/YOUR_USERNAME/trae-commands.git
   cd trae-commands
   ```

2. **设置开发环境**
   ```bash
   # 添加上游仓库
   git remote add upstream https://github.com/tonymumu/trae-commands.git
   
   # 安装开发版本
   ./install.sh
   ```

3. **创建功能分支**
   ```bash
   git checkout -b feature/your-feature-name
   ```

## 🛠️ 开发环境设置

```bash
git clone https://github.com/brennercruvinel/CCPlugins
cd CCPlugins
python install.py  # Test your changes
```

## Pull Request Guidelines

1. **One command per PR** - Makes review easier
2. **Test your changes** - Run `python install.py` to verify
3. **Keep it simple** - This project values pragmatism over perfection
4. **Update README** - Add your command to the table with a one-line description
5. **Quick merges** - If it works and helps, we merge it

### Commit Messages
Keep them simple:
- `add: command-name` for new commands
- `fix: what you fixed` for fixes
- `docs: what you updated` for documentation

## Command Quality Checklist

- [ ] Saves real time (5+ minutes)
- [ ] Works without configuration
- [ ] Handles common edge cases
- [ ] Clear, actionable output
- [ ] Under 100 lines
- [ ] Includes validation phase for complex commands
- [ ] No emojis in git-related output

## Advanced Command Features

For complex commands, consider implementing:

### Validation Phases
Commands like `/refactor` and `/implement` should include validation:
```
/refactor validate  # Check completeness, find loose ends
/implement validate # Verify integration completeness
```

### Extended Thinking
Use `<think>` blocks for sophisticated analysis in:
- Complex architectural refactoring
- Security vulnerability detection
- Multi-step problem solving

### Command Integration
Minimal, pragmatic suggestions for natural workflow:
- Suggest `/test` after major changes
- Suggest `/commit` at logical checkpoints
- Avoid over-engineering command chains

## What We're Looking For

**Yes:**
- Commands that automate tedious tasks
- Cross-platform compatibility improvements  
- Real-world workflow optimizations
- Validation phases for complex operations
- Pragmatic command integration

**No:**
- Framework-specific tools (unless very popular)
- Commands requiring external dependencies
- Overly complex multi-step wizards
- Over-engineered command orchestration

## Issue Templates

When creating issues, please use these templates:

### Bug Report
```
**Command:** /command-name
**Expected behavior:** What should happen
**Actual behavior:** What actually happened
**Steps to reproduce:**
1. Run command with these arguments
2. See error

**Environment:**
- OS: Windows/Linux/macOS
- Claude Code version: X.X.X
```

### Feature Request
```
**Problem:** What repetitive task are you doing?
**Solution:** How would the command help?
**Time saved:** Estimate minutes saved per use
**Example usage:** /proposed-command argument
```

## Community Standards

1. **Professional Communication** - Clear, concise, technical
2. **No Emojis in Code** - Keep commands, commits, PRs, and issues clean and professional
3. **Respect Time** - Quick reviews, fast merges for good contributions
4. **Test Before Submit** - Ensure your command works on major platforms
5. **Clean Architecture** - Follow clean code principles, no over-engineering

## Continuous Improvement

CCPlugins is actively maintained. We:
- Test commands thoroughly before release
- Refine based on real usage patterns
- Fix issues as they're discovered
- Welcome community feedback

Remember: Every command should make a developer's day a little easier.
