# 完整贡献策略 - 上下文感知

## 命令说明
基于当前工作上下文分析所需的完整贡献策略，提供智能的代码贡献指导和质量保证。

## 战略思考过程

### 上下文分析框架
1. **当前工作上下文**
   - 会话中完成了什么工作？
   - 处于实现中还是完成后状态？
   - 变更类型（功能、修复、重构）？
   - 工作是否准备好贡献？

2. **项目类型与标准**
   - 开源、公司还是个人项目？
   - 贡献指南和工作流程？
   - 质量门禁（测试、代码检查、审核）？
   - 特定的编码标准？

3. **贡献策略**
   - 应该是单个PR还是多个？
   - 解决了哪些问题？
   - 需要更新哪些文档？
   - 谁应该审核？

## 使用工具
- `search_codebase` - 分析项目结构和贡献指南
- `view_files` - 检查CONTRIBUTING.md、README等
- `run_command` - 执行测试、代码检查、构建
- `search_by_regex` - 查找相关问题和PR模式
- `todo_write` - 创建贡献前检查清单

## 上下文检测流程

### 阶段1：环境分析
**强制步骤：**
1. 检测项目类型和技术栈
2. 分析现有贡献指南
3. 识别质量标准和工具
4. 评估当前工作状态

### 阶段2：贡献准备
1. 执行预提交检查
2. 验证代码质量
3. 确保测试通过
4. 准备贡献文档

### 阶段3：贡献执行
1. 创建合适的分支策略
2. 准备PR描述和文档
3. 执行提交和推送
4. 设置审核流程

## Trae使用示例

```markdown
用户：帮我准备贡献代码，我们刚完成了用户认证功能

助手：我来分析你的工作并准备完整的贡献策略。

*使用search_codebase分析项目结构*
*使用view_files检查CONTRIBUTING.md*
*使用run_command检查git状态*

## 上下文分析结果

### 📊 项目信息
- 类型：开源React项目
- 技术栈：React + TypeScript + Jest
- 贡献者：15人
- 最近活动：活跃开发中

### 🔍 工作分析
- 完成功能：用户认证系统
- 文件变更：8个文件（新增5个，修改3个）
- 代码行数：+420行，-15行
- 测试覆盖：新增12个测试用例

### ✅ 质量检查
- TypeScript编译：通过
- ESLint检查：通过
- 单元测试：通过（覆盖率92%）
- 集成测试：通过

### 📋 贡献准备清单
*使用todo_write创建检查清单*

准备就绪！你的代码质量很高，可以开始贡献流程。
```

## 贡献策略模板

### 开源项目贡献
```markdown
## 开源贡献策略

### 🎯 贡献目标
- 解决Issue #123：用户认证功能
- 提升代码覆盖率至90%+
- 改进用户体验

### 📝 PR描述模板
**功能描述**
实现了完整的用户认证系统，包括登录、注册、密码重置功能。

**变更内容**
- 新增：AuthProvider组件
- 新增：useAuth hook
- 新增：认证相关API
- 修改：路由保护逻辑
- 新增：认证相关测试

**测试情况**
- 单元测试：12个新增测试
- 集成测试：3个端到端测试
- 覆盖率：92%

**截图/演示**
[添加功能演示截图或GIF]

**检查清单**
- [x] 代码遵循项目规范
- [x] 添加了适当的测试
- [x] 更新了相关文档
- [x] 通过了所有CI检查
```

### 企业项目贡献
```markdown
## 企业贡献策略

### 🏢 企业标准检查
- 代码审核：需要2人审核
- 安全扫描：通过安全检查
- 性能测试：无性能回归
- 文档更新：技术文档已更新

### 📊 影响分析
- 用户影响：提升登录体验
- 系统影响：无破坏性变更
- 性能影响：登录速度提升15%
- 安全影响：增强认证安全性

### 🚀 部署计划
- 开发环境：已部署测试
- 测试环境：待部署验证
- 生产环境：计划下周发布
- 回滚计划：已准备回滚脚本
```

## 质量保证检查

### 代码质量检查
```bash
# 代码格式检查
npm run lint

# 类型检查
npm run type-check

# 单元测试
npm run test

# 集成测试
npm run test:integration

# 构建检查
npm run build

# 安全扫描
npm audit
```

### 文档检查清单
- [ ] README.md更新（如有新功能）
- [ ] CHANGELOG.md添加条目
- [ ] API文档更新
- [ ] 代码注释完整
- [ ] 示例代码正确

### 测试检查清单
- [ ] 单元测试覆盖核心逻辑
- [ ] 集成测试覆盖用户流程
- [ ] 边界条件测试
- [ ] 错误处理测试
- [ ] 性能测试（如需要）

## 分支策略指导

### Git Flow策略
```bash
# 创建功能分支
git checkout -b feature/user-authentication

# 开发完成后
git checkout develop
git merge feature/user-authentication

# 准备发布
git checkout -b release/v1.2.0
git checkout main
git merge release/v1.2.0
```

### GitHub Flow策略
```bash
# 创建功能分支
git checkout -b user-authentication

# 推送并创建PR
git push origin user-authentication
# 在GitHub上创建Pull Request
```

### GitLab Flow策略
```bash
# 功能开发
git checkout -b feature/user-auth

# 合并到主分支
git checkout main
git merge feature/user-auth

# 部署到环境分支
git checkout production
git merge main
```

## 自动化工具集成

### CI/CD检查
```yaml
# .github/workflows/pr-check.yml
name: PR Quality Check
on: [pull_request]
jobs:
  quality-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install dependencies
        run: npm ci
      - name: Run linting
        run: npm run lint
      - name: Run tests
        run: npm run test:coverage
      - name: Build project
        run: npm run build
```

### 代码质量门禁
- **覆盖率要求**：最低80%
- **复杂度限制**：单函数复杂度<10
- **重复代码**：重复率<5%
- **安全扫描**：无高危漏洞

## 审核流程管理

### 审核者分配
- **代码审核**：技术负责人
- **设计审核**：UI/UX设计师
- **安全审核**：安全工程师
- **产品审核**：产品经理

### 审核标准
```markdown
## 代码审核检查点

### 功能性
- [ ] 功能实现正确
- [ ] 边界条件处理
- [ ] 错误处理完善
- [ ] 性能表现良好

### 可维护性
- [ ] 代码结构清晰
- [ ] 命名规范一致
- [ ] 注释充分适当
- [ ] 可测试性良好

### 安全性
- [ ] 输入验证完整
- [ ] 权限控制正确
- [ ] 敏感信息保护
- [ ] 安全最佳实践
```

## 贡献后跟踪

### 合并后任务
- [ ] 监控部署状态
- [ ] 观察性能指标
- [ ] 收集用户反馈
- [ ] 准备热修复（如需要）

### 经验总结
- 记录遇到的问题和解决方案
- 更新团队知识库
- 分享最佳实践
- 改进贡献流程

## 重要提示

⚠️ **质量第一**
- 永远不要为了速度牺牲质量
- 确保所有测试通过再提交
- 遵循项目的编码标准
- 重视代码审核反馈

⚠️ **沟通协作**
- 及时响应审核意见
- 主动寻求帮助和反馈
- 保持透明的工作状态
- 尊重团队的决策过程

⚠️ **持续改进**
- 从每次贡献中学习
- 关注行业最佳实践
- 参与团队流程改进
- 分享知识和经验

⚠️ **责任意识**
- 对自己的代码负责
- 考虑变更的长远影响
- 维护代码的可持续性
- 关注用户体验和业务价值