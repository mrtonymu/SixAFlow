# 代码审查 - Trae版本

我将审查你的代码以发现潜在问题。

让我在详细分析前创建一个检查点：
```bash
git add -A  
git commit -m "Pre-review checkpoint" || echo "No changes to commit"
```

我将使用专门的子代理进行全面分析：
- **安全子代理**：凭据暴露、输入验证、漏洞
- **性能子代理**：瓶颈、内存问题、优化机会
- **质量子代理**：代码复杂度、可维护性、最佳实践
- **架构子代理**：层分离、依赖方向、可扩展性模式

我将使用Trae工具检查文件以分析：
1. **安全问题** - 凭据暴露、输入验证
2. **逻辑问题** - 错误处理、边缘情况
3. **性能问题** - 低效模式、瓶颈
4. **代码质量** - 复杂度、可维护性

当我发现多个问题时，我会创建一个todo列表来系统地解决它们。

对于每个问题，我会：
- 显示带文件引用的确切位置
- 解释问题和潜在影响
- 提供具体的修复步骤
- 按严重性和工作量优先排序

审查后，我会询问："为关键发现创建GitHub问题？"
- 是：我会创建带详细描述的优先级问题
- 仅待办事项：我会维护本地跟踪以供解决
- 摘要：我会提供可操作的报告

**重要提示**：我绝不会：
- 在提交中添加"Co-authored-by"或任何Claude签名
- 在问题中添加"Created by Claude"或任何AI归属
- 在任何输出中包含"Generated with Claude Code"
- 修改git配置或仓库设置
- 添加任何AI/助手签名或水印
- 在提交、PR、问题或git相关内容中使用表情符号

这专注于影响你应用程序可靠性和可维护性的真实问题。

## Trae使用示例

```bash
# 1. 创建审查前检查点
run_command "git add -A && git commit -m 'Pre-review checkpoint' || echo 'No changes to commit'"

# 2. 安全审查 - 查找敏感信息
search_by_regex "password|secret|key|token|api_key"
search_by_regex "console\.log.*password|console\.log.*secret"

# 3. 性能审查 - 查找性能问题
search_by_regex "for.*for.*for" # 嵌套循环
search_by_regex "\.map\(.*\.map\(" # 嵌套map
search_codebase "性能瓶颈模式"

# 4. 代码质量审查
search_by_regex "function.*{[\s\S]{300,}" # 长函数
search_by_regex "if.*if.*if.*if" # 深度嵌套
search_by_regex "TODO|FIXME|XXX|HACK"

# 5. 架构审查
search_codebase "循环依赖"
search_codebase "紧耦合模式"

# 6. 生成审查报告
write_to_file "review-report.md" "审查结果和建议"
```

## 审查清单

### 安全审查
- [ ] 敏感信息是否暴露在日志中？
- [ ] 用户输入是否经过验证？
- [ ] 是否存在SQL注入风险？
- [ ] API端点是否有适当的认证？
- [ ] 密码是否正确哈希？

### 性能审查
- [ ] 是否存在N+1查询问题？
- [ ] 大数据集是否分页处理？
- [ ] 是否有不必要的重复计算？
- [ ] 内存泄漏风险？
- [ ] 缓存策略是否合理？

### 代码质量审查
- [ ] 函数是否过长（>50行）？
- [ ] 圈复杂度是否过高？
- [ ] 变量命名是否清晰？
- [ ] 是否有重复代码？
- [ ] 错误处理是否完善？

### 架构审查
- [ ] 模块职责是否单一？
- [ ] 依赖关系是否清晰？
- [ ] 是否遵循SOLID原则？
- [ ] 接口设计是否合理？
- [ ] 可测试性如何？

## 问题严重性分级

**严重（Critical）**
- 安全漏洞
- 数据丢失风险
- 系统崩溃

**高（High）**
- 性能严重问题
- 功能缺陷
- 可维护性问题

**中（Medium）**
- 代码质量问题
- 轻微性能问题
- 文档缺失

**低（Low）**
- 代码风格问题
- 优化建议
- 最佳实践建议