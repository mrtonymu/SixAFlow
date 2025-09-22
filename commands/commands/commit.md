# Smart Git Commit - Trae版本

我将分析你的更改并创建有意义的提交消息。

**提交前质量检查：**
在提交之前，我会验证：
- 构建通过（如果存在构建命令）
- 测试通过（如果存在测试命令）
- 代码检查通过（如果存在lint命令）
- 更改的文件中没有明显错误

首先，让我检查这是否是git仓库以及有什么更改：

```bash
# 验证我们在git仓库中
if ! git rev-parse --git-dir > /dev/null 2>&1; then
    echo "错误：不是git仓库"
    echo "此命令需要git版本控制"
    exit 1
fi

# 检查是否有要提交的更改
if ! git diff --cached --quiet || ! git diff --quiet; then
    echo "检测到更改："
    git status --short
else
    echo "没有要提交的更改"
    exit 0
fi

# 显示详细更改
git diff --cached --stat
git diff --stat
```

现在我将分析更改以确定：
1. 修改了哪些文件
2. 更改的性质（功能、修复、重构等）
3. 受影响的范围/组件

如果分析或提交遇到错误：
- 我会解释出了什么问题
- 建议如何解决
- 确保不会发生部分提交

```bash
# 如果没有暂存任何内容，我会暂存修改的文件（不包括未跟踪的）
if git diff --cached --quiet; then
    echo "没有文件被暂存。正在暂存修改的文件..."
    git add -u
fi

# 显示将要提交的内容
git diff --cached --name-status
```

基于分析，我会创建一个符合约定的提交消息：
- **类型**: feat|fix|docs|style|refactor|test|chore
- **范围**: 受影响的组件或区域（可选）
- **主题**: 现在时态的清晰描述
- **正文**: 为什么进行更改（如果需要）

```bash
# 我会用分析的消息创建提交
# 示例: git commit -m "fix(auth): resolve login timeout issue"
```

提交消息将简洁、有意义，并遵循你项目的约定（如果我能从最近的提交中检测到）。

**重要提示**：我绝不会：
- 添加"Co-authored-by"或任何Claude签名
- 包含"Generated with Claude Code"或类似消息
- 修改git配置或用户凭据
- 在提交中添加任何AI/助手归属
- 在提交、PR或git相关内容中使用表情符号

提交将仅使用你现有的git用户配置，保持你提交的完全所有权和真实性。

## Trae使用示例

```bash
# 1. 检查git状态
run_command "git status --short"

# 2. 查看更改统计
run_command "git diff --stat"

# 3. 暂存修改的文件
run_command "git add -u"

# 4. 查看将要提交的内容
run_command "git diff --cached --name-status"

# 5. 分析更改类型并创建提交
# 基于更改内容生成合适的提交消息
run_command 'git commit -m "feat: add user authentication system"'

# 6. 验证提交
run_command "git log -1 --oneline"
```

## 提交消息模板

```
类型(范围): 简短描述

详细说明（可选）

- 具体更改1
- 具体更改2
```

**常用类型：**
- `feat`: 新功能
- `fix`: 修复bug
- `docs`: 文档更新
- `style`: 代码格式化
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建过程或辅助工具的变动