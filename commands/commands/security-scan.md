# 安全分析 - Trae版本

我将执行全面的安全分析，跨会话跟踪和修复连续性。

参数：`$ARGUMENTS` - 特定路径或安全重点区域

## 会话智能

我将维护安全修复进度：

**会话文件（在当前项目目录中）：**
- `security-scan/plan.md` - 所有漏洞和修复
- `security-scan/state.json` - 修复进度

**重要提示：** 会话文件存储在当前项目根目录的`security-scan`文件夹中

**自动检测：**
- 如果会话存在：显示已修复vs待处理的漏洞
- 如果没有会话：执行新的安全扫描
- 命令：`resume`、`status`、`new`

## 阶段1：安全评估

### 安全分析的扩展思考

对于复杂的安全场景，我将使用扩展思考来识别复杂的漏洞：

<think>
分析安全时：
- 不是立即显而易见的攻击向量
- 多层防御的薄弱环节
- 业务逻辑漏洞
- 供应链安全风险
- 数据泄露可能性
</think>

## Trae使用示例

```bash
# 1. 检查现有安全扫描会话
list_dir security-scan

# 2. 如果存在，读取状态
view_files security-scan/state.json
view_files security-scan/plan.md

# 3. 敏感信息扫描
search_by_regex "password|secret|key|token|api_key|private"
search_by_regex "console\.log.*password|console\.log.*secret"

# 4. 输入验证检查
search_by_regex "req\.body|req\.query|req\.params" # Express.js
search_by_regex "innerHTML|dangerouslySetInnerHTML" # XSS风险

# 5. 认证授权检查
search_by_regex "jwt|session|auth|login"
search_codebase "认证绕过"

# 6. SQL注入检查
search_by_regex "SELECT.*\+|INSERT.*\+|UPDATE.*\+" # 字符串拼接
search_by_regex "query\(.*\+|execute\(.*\+"

# 7. 文件上传安全
search_by_regex "multer|upload|file"
search_by_regex "\.exe|\.php|\.jsp"

# 8. CORS和安全头检查
search_by_regex "cors|Access-Control|X-Frame-Options"

# 9. 生成安全报告
write_to_file "security-scan/report.md" "安全扫描结果"
```

## 安全检查清单

### 认证和授权
- [ ] 密码是否正确哈希？
- [ ] JWT令牌是否安全存储？
- [ ] 会话管理是否安全？
- [ ] 权限检查是否完整？
- [ ] 多因素认证是否实现？

### 输入验证
- [ ] 所有用户输入是否验证？
- [ ] SQL注入防护是否到位？
- [ ] XSS防护是否实现？
- [ ] CSRF保护是否启用？
- [ ] 文件上传是否安全？

### 数据保护
- [ ] 敏感数据是否加密？
- [ ] 传输是否使用HTTPS？
- [ ] 数据库连接是否安全？
- [ ] 日志是否包含敏感信息？
- [ ] 备份是否安全？

### 配置安全
- [ ] 默认密码是否更改？
- [ ] 调试模式是否关闭？
- [ ] 错误信息是否泄露？
- [ ] 安全头是否配置？
- [ ] 依赖是否有漏洞？

## 漏洞严重性分级

### 严重（Critical）
- 远程代码执行
- SQL注入
- 认证绕过
- 敏感数据泄露

### 高（High）
- XSS攻击
- CSRF攻击
- 权限提升
- 文件包含漏洞

### 中（Medium）
- 信息泄露
- 会话固定
- 弱加密
- 配置错误

### 低（Low）
- 信息收集
- 版本泄露
- 缺少安全头
- 弱密码策略

## 修复建议模板

```markdown
# 安全漏洞修复计划

## 漏洞概述
- **类型**: [SQL注入/XSS/认证绕过等]
- **严重性**: [Critical/High/Medium/Low]
- **影响**: [具体影响描述]
- **位置**: [文件路径和行号]

## 技术细节
```javascript
// 有问题的代码
const query = "SELECT * FROM users WHERE id = " + userId;

// 修复后的代码
const query = "SELECT * FROM users WHERE id = ?";
db.query(query, [userId]);
```

## 修复步骤
1. [具体修复步骤1]
2. [具体修复步骤2]
3. [验证步骤]

## 验证方法
- [如何验证修复有效]
- [测试用例]
- [安全测试]

## 预防措施
- [如何防止类似问题]
- [代码审查要点]
- [自动化检测]
```

## 安全工具集成

```bash
# 依赖漏洞扫描
run_command "npm audit"
run_command "yarn audit"

# 静态代码分析
run_command "eslint --ext .js,.ts src/ --config .eslintrc-security.js"

# 密钥扫描
search_by_regex "-----BEGIN.*KEY-----"
search_by_regex "[A-Za-z0-9]{32,}"
```