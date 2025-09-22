# Clean Project - Trae版本

我将帮助清理开发过程中的临时文件和调试代码，同时保留你的工作代码。

## 战略思考过程

<think>
在清理之前，我需要仔细考虑：

1. **文件识别**
   - 什么模式表明是临时/调试文件？
   - 哪些文件看起来是临时的但实际上很重要？
   - 项目是否有特定的临时文件约定？
   - 生成的文件中哪些应该保留？

2. **安全分析**
   - 哪些删除是绝对安全的？
   - 哪些需要更仔细的检查？
   - 是否有活动进程在使用这些文件？
   - 删除这些文件会破坏开发环境吗？

3. **常见陷阱**
   - .env文件可能看起来像临时文件但包含配置
   - .cache目录可能是性能所需的
   - 某些.tmp文件可能是活动会话数据
   - 调试日志可能包含重要的错误信息

4. **清理策略**
   - 从明显的临时文件开始（*.log, *.tmp, *~）
   - 检查文件年龄 - 较旧的文件通常更安全删除
   - 通过git status验证已跟踪vs未跟踪的文件
   - 将相似文件分组进行批量决策
</think>

基于此分析，我将创建一个git检查点以确保安全：
```bash
git add -A
git commit -m "Pre-cleanup checkpoint" || echo "No changes to commit"
```

**重要提示**：我绝不会：
- 添加"Co-authored-by"或任何Claude签名
- 包含"Generated with Claude Code"或类似消息
- 修改git配置或用户凭据
- 在提交中添加任何AI/助手归属
- 在提交、PR或git相关内容中使用表情符号

我将使用Trae工具识别清理目标：
- **search_by_regex工具** 查找临时和调试文件
- **search_codebase工具** 检测代码中的调试语句
- **view_files工具** 在删除前验证文件内容

关键目录自动受保护：
- .git目录（版本控制）
- node_modules, vendor（依赖目录）
- 重要配置文件

当我发现多个需要清理的项目时，我会创建一个todo列表来系统地处理它们。

我会在采取行动前向你展示将要删除的内容及原因：
- 调试/日志文件和临时文件
- 失败的实现尝试
- 仅用于开发的文件
- 代码中的调试语句

清理后，我会验证项目完整性并报告清理了什么。

如果出现任何问题，我可以从开始时创建的git检查点恢复。

这样可以只保留干净的工作代码，同时保持完全的安全性。

## Trae使用示例

```bash
# 1. 创建安全检查点
git add -A && git commit -m "Pre-cleanup checkpoint" || echo "No changes to commit"

# 2. 查找调试代码
search_by_regex "console\.log|debugger|TODO|FIXME|XXX"

# 3. 查找临时文件
search_by_regex "\.(log|tmp|temp|bak|swp|swo)$|~$"

# 4. 清理调试代码（示例）
update_file "移除console.log语句"

# 5. 删除临时文件
delete_file ["path/to/temp/file"]

# 6. 验证清理结果
run_command "git status"
```