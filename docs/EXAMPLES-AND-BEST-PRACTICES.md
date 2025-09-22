# 📚 Trae智能命令集 - 使用示例与最佳实践

> 实战案例集合，让你快速掌握每个命令的最佳使用方式

## 🎯 目录

- [🎬 会话管理示例](#会话管理示例)
- [🧠 项目理解示例](#项目理解示例)
- [⚡ 开发核心示例](#开发核心示例)
- [🛡️ 质量保证示例](#质量保证示例)
- [🔧 维护工具示例](#维护工具示例)
- [🏆 最佳实践](#最佳实践)
- [🎨 工作流模板](#工作流模板)

## 🎬 会话管理示例

### `session-start` - 智能会话开始

#### 场景1：新项目开发
```
用户输入：session-start

AI响应：
🚀 开始新的编程会话

📊 项目分析：
- 技术栈：Next.js 14 + TypeScript + Tailwind CSS
- 数据库：Supabase PostgreSQL
- 架构：App Router + Server Components
- 状态管理：Zustand

🎯 会话目标设定：
请告诉我今天要开发什么功能？

💡 建议工作流：
1. understand - 深入理解项目结构
2. implement - 实现核心功能
3. review - 代码质量检查
4. test - 生成测试用例
```

#### 场景2：维护现有项目
```
用户输入：session-start

AI响应：
🔧 继续项目维护会话

📈 项目状态：
- 最后修改：2天前
- 待处理TODO：12个
- 测试覆盖率：78%
- 技术债务：中等

🎯 建议今日任务：
1. fix-todos - 处理积压的TODO
2. security-scan - 安全检查
3. refactor - 代码重构
4. test - 提升测试覆盖率
```

### `session-end` - 会话总结

#### 场景：功能开发完成
```
用户输入：session-end

AI响应：
🎉 会话总结

✅ 完成的工作：
- 实现了用户认证模块
- 添加了JWT token管理
- 创建了登录/注册页面
- 编写了单元测试（覆盖率85%）
- 生成了API文档

📊 代码统计：
- 新增文件：8个
- 代码行数：+1,247行
- 测试用例：23个
- 修复问题：3个

🔄 下次会话建议：
1. 实现用户权限管理
2. 添加密码重置功能
3. 优化登录性能
4. 集成第三方登录

💾 会话记录已保存到：.trae/session-logs/
```

## 🧠 项目理解示例

### `understand` - 深度项目分析

#### 场景：接手新项目
```
用户输入：understand

AI响应：
🔍 项目深度分析报告

📁 项目结构：
├── app/                 # Next.js App Router
│   ├── (auth)/         # 认证相关页面
│   ├── dashboard/      # 仪表板模块
│   └── api/           # API路由
├── components/         # 可复用组件
├── lib/               # 工具库
└── types/             # TypeScript类型定义

🛠️ 技术栈分析：
- 前端：Next.js 14 + TypeScript + Tailwind CSS
- UI库：daisyUI + Headless UI
- 状态管理：Zustand + React Query
- 数据库：Supabase (PostgreSQL)
- 认证：Supabase Auth
- 部署：Vercel

🏗️ 架构模式：
- 设计模式：组件化 + 模块化
- 数据流：Server Components + Client Components
- 路由：文件系统路由 + 动态路由
- 样式：Utility-first CSS

🔍 关键发现：
✅ 优点：
- 现代化技术栈
- 良好的类型安全
- 清晰的目录结构
- 响应式设计

⚠️ 需要关注：
- 部分组件缺少错误边界
- API错误处理不够完善
- 测试覆盖率偏低（45%）
- 缺少国际化支持

💡 改进建议：
1. 添加全局错误处理
2. 完善API错误处理机制
3. 提升测试覆盖率到80%+
4. 考虑添加i18n支持
```

### `explain-like-senior` - 资深视角解释

#### 场景：理解复杂代码
```
用户输入：explain-like-senior

AI响应：
👨‍💻 资深开发者视角解析

🎯 代码核心逻辑：
这是一个典型的React Server Components + Client Components混合架构：

📊 数据流设计：
1. Server Component负责数据获取（SEO友好）
2. Client Component处理交互逻辑（用户体验）
3. 通过props传递数据，避免prop drilling

🏗️ 架构决策分析：
✅ 为什么选择这种架构：
- SSR性能优势：首屏加载快
- SEO优化：搜索引擎友好
- 开发体验：类型安全 + 热重载

🔧 实现细节：
- 使用Suspense处理异步状态
- 错误边界捕获组件异常
- React Query管理客户端状态
- Zustand处理全局状态

💡 最佳实践体现：
1. 关注点分离：UI逻辑与业务逻辑分离
2. 可测试性：纯函数 + 依赖注入
3. 可维护性：模块化 + 类型安全
4. 性能优化：懒加载 + 代码分割

⚠️ 潜在风险：
- 过度抽象可能影响可读性
- Server/Client边界需要谨慎处理
- 状态管理复杂度随业务增长
```

## ⚡ 开发核心示例

### `implement` - 6A流程实现功能

#### 场景：实现用户管理模块

**Step 1 - Align (需求对齐)**
```
用户输入：implement "构建用户管理模块"

AI响应：
🎯 需求对齐 (Align)

📋 功能需求理解：
- 🎯 目标：构建完整的用户管理CRUD系统
- 📥 输入：用户数据（姓名、邮箱、角色、状态）
- 📤 输出：用户列表、创建表单、编辑功能、删除确认
- ⛔ 边界：不包含用户权限系统，不涉及第三方集成

🔍 技术要求：
- 使用Supabase users表
- 遵循daisyUI设计规范
- 支持搜索和筛选
- 响应式设计

请确认需求是否正确？回复 "Approved" 继续下一步。
```

**Step 2 - Architect (架构设计)**
```
用户确认：Approved

AI响应：
🏗️ 架构设计 (Architect)

📁 文件结构：
app/
├── users/
│   ├── page.tsx              # 用户列表页
│   ├── create/
│   │   └── page.tsx          # 创建用户页
│   ├── [id]/
│   │   ├── page.tsx          # 用户详情页
│   │   └── edit/
│   │       └── page.tsx      # 编辑用户页
│   └── components/
│       ├── UserList.tsx      # 用户列表组件
│       ├── UserForm.tsx      # 用户表单组件
│       ├── UserCard.tsx      # 用户卡片组件
│       └── UserFilters.tsx   # 筛选组件

🗄️ 数据库查询：
- getUserList() - 获取用户列表（支持分页、搜索）
- getUserById() - 获取单个用户详情
- createUser() - 创建新用户
- updateUser() - 更新用户信息
- deleteUser() - 删除用户

🎨 UI设计：
- 列表页：卡片布局 + 搜索栏 + 筛选器
- 表单页：两列布局 + 实时验证
- 详情页：信息展示 + 操作按钮
- 样式：rounded-2xl卡片 + shadow-lg阴影

请确认架构设计？回复 "Approved" 继续。
```

**Step 3 - Atomize (任务拆解)**
```
用户确认：Approved

AI响应：
⚡ 任务拆解 (Atomize)

📝 开发任务清单：
□ 1. 创建用户列表页面 (/users)
□ 2. 实现用户搜索和筛选功能
□ 3. 构建用户创建表单 (/users/create)
□ 4. 实现表单验证和提交
□ 5. 创建用户详情页面 (/users/[id])
□ 6. 构建用户编辑功能 (/users/[id]/edit)
□ 7. 实现用户删除功能
□ 8. 添加加载状态和错误处理
□ 9. 优化响应式设计
□ 10. 集成Supabase数据操作

请选择要实现的任务编号（建议从1开始）：
```

**Step 4 - Approve (人工审批)**
```
用户选择：1

AI响应：
✅ 任务确认 (Approve)

即将实现：创建用户列表页面 (/users)

包含功能：
- 用户数据展示（卡片布局）
- 基础搜索功能
- 分页控制
- 加载状态
- 错误处理

确认开始实现？回复 "Approved"
```

**Step 5 - Automate (执行交付)**
```
用户确认：Approved

AI响应：
🔧 开始实现 (Automate)

正在创建用户列表页面...

[生成具体代码文件]
```

**Step 6 - Assess (质量评估)**
```
AI自动执行：
📊 质量评估 (Assess)

✅ 设计文档符合度：100%
✅ 架构集成度：完美集成现有系统
✅ 响应式设计：支持移动端和桌面端
✅ 错误处理：完整的错误边界和用户反馈
✅ 性能优化：懒加载 + 虚拟滚动
✅ 代码质量：TypeScript类型安全 + ESLint规范

🎉 任务1完成！可以继续下一个任务。
```

### `scaffold` - 快速搭建骨架

#### 场景：创建新模块
```
用户输入：scaffold "订单管理模块"

AI响应：
🏗️ 快速搭建：订单管理模块

📁 创建目录结构：
app/orders/
├── page.tsx                 # 订单列表
├── [id]/
│   ├── page.tsx            # 订单详情
│   └── edit/
│       └── page.tsx        # 编辑订单
├── create/
│   └── page.tsx            # 创建订单
└── components/
    ├── OrderList.tsx       # 订单列表组件
    ├── OrderForm.tsx       # 订单表单
    ├── OrderCard.tsx       # 订单卡片
    └── OrderStatus.tsx     # 状态组件

🔧 生成基础文件：
- 路由页面（带基础布局）
- 组件模板（带TypeScript类型）
- 样式文件（daisyUI类名）
- 数据类型定义

⚡ 下一步建议：
1. 使用 `implement` 完善具体功能
2. 使用 `review` 检查代码质量
3. 使用 `test` 添加测试用例
```

## 🛡️ 质量保证示例

### `review` - 全面代码审查

#### 场景：功能完成后的代码审查
```
用户输入：review

AI响应：
🔍 代码审查报告

📊 总体评分：B+ (85/100)

✅ 优点：
1. 代码结构清晰，遵循Next.js最佳实践
2. TypeScript类型定义完整
3. 组件职责单一，可复用性好
4. 错误处理机制完善

⚠️ 需要改进：
1. 性能优化：
   - UserList组件缺少React.memo优化
   - 建议使用useMemo缓存计算结果
   
2. 安全性：
   - 用户输入验证不够严格
   - 建议添加XSS防护

3. 可维护性：
   - 部分组件过于复杂，建议拆分
   - 缺少单元测试

🔧 具体修改建议：

1. 性能优化：
```typescript
// 优化前
const UserList = ({ users }) => {
  return users.map(user => <UserCard key={user.id} user={user} />)
}

// 优化后
const UserList = React.memo(({ users }) => {
  const sortedUsers = useMemo(() => 
    users.sort((a, b) => a.name.localeCompare(b.name)), 
    [users]
  )
  return sortedUsers.map(user => <UserCard key={user.id} user={user} />)
})
```

2. 安全性增强：
```typescript
// 添加输入验证
const userSchema = z.object({
  name: z.string().min(2).max(50).regex(/^[a-zA-Z\s]+$/),
  email: z.string().email(),
  role: z.enum(['admin', 'user', 'moderator'])
})
```

📈 改进后预期评分：A (92/100)
```

### `test` - 智能测试生成

#### 场景：为用户管理模块生成测试
```
用户输入：test

AI响应：
🧪 测试用例生成

📋 测试覆盖计划：
- 单元测试：组件逻辑测试
- 集成测试：API交互测试
- E2E测试：用户流程测试

🔧 生成的测试文件：

1. __tests__/components/UserList.test.tsx
```typescript
import { render, screen } from '@testing-library/react'
import { UserList } from '../UserList'

describe('UserList', () => {
  const mockUsers = [
    { id: '1', name: 'John Doe', email: 'john@example.com' },
    { id: '2', name: 'Jane Smith', email: 'jane@example.com' }
  ]

  it('renders user list correctly', () => {
    render(<UserList users={mockUsers} />)
    expect(screen.getByText('John Doe')).toBeInTheDocument()
    expect(screen.getByText('Jane Smith')).toBeInTheDocument()
  })

  it('handles empty user list', () => {
    render(<UserList users={[]} />)
    expect(screen.getByText('No users found')).toBeInTheDocument()
  })
})
```

2. __tests__/api/users.test.ts
```typescript
import { createUser, getUserList } from '../api/users'

describe('User API', () => {
  it('creates user successfully', async () => {
    const userData = { name: 'Test User', email: 'test@example.com' }
    const result = await createUser(userData)
    expect(result.success).toBe(true)
    expect(result.data.name).toBe('Test User')
  })
})
```

📊 测试覆盖率目标：
- 组件测试：90%+
- API测试：85%+
- 整体覆盖率：80%+

🚀 运行测试：
```bash
npm run test
npm run test:coverage
```
```

### `security-scan` - 安全漏洞扫描

#### 场景：上线前安全检查
```
用户输入：security-scan

AI响应：
🛡️ 安全扫描报告

🔍 扫描范围：
- 依赖包漏洞检查
- 代码安全问题
- 配置安全审查
- 数据库安全检查

📊 扫描结果：

⚠️ 发现问题：
1. 高风险（1个）：
   - SQL注入风险：用户搜索功能未使用参数化查询
   
2. 中风险（2个）：
   - XSS风险：用户输入未进行HTML转义
   - 敏感信息泄露：错误信息包含数据库结构信息

3. 低风险（3个）：
   - 缺少CSRF保护
   - 密码强度验证不足
   - 缺少请求频率限制

🔧 修复建议：

1. 修复SQL注入：
```typescript
// 危险写法
const query = `SELECT * FROM users WHERE name LIKE '%${searchTerm}%'`

// 安全写法
const { data } = await supabase
  .from('users')
  .select('*')
  .ilike('name', `%${searchTerm}%`)
```

2. 防止XSS攻击：
```typescript
import DOMPurify from 'dompurify'

const sanitizedInput = DOMPurify.sanitize(userInput)
```

3. 错误处理优化：
```typescript
// 避免泄露敏感信息
catch (error) {
  console.error('Database error:', error) // 仅记录到日志
  return { error: 'Internal server error' } // 返回通用错误
}
```

🎯 修复后安全等级：A级（预期）
```

## 🔧 维护工具示例

### `fix-todos` - 批量处理TODO

#### 场景：清理技术债务
```
用户输入：fix-todos

AI响应：
🔧 TODO处理报告

🔍 发现的TODO项：
1. // TODO: 添加用户头像上传功能 (UserProfile.tsx:45)
2. // TODO: 优化数据库查询性能 (api/users.ts:23)
3. // TODO: 添加国际化支持 (components/Header.tsx:12)
4. // FIXME: 修复移动端布局问题 (UserList.tsx:67)
5. // TODO: 实现数据导出功能 (Dashboard.tsx:89)

📊 优先级分析：
🔴 高优先级（需要立即处理）：
- FIXME: 修复移动端布局问题

🟡 中优先级（本周处理）：
- 优化数据库查询性能
- 添加用户头像上传功能

🟢 低优先级（下个迭代）：
- 添加国际化支持
- 实现数据导出功能

🔧 开始处理高优先级问题：

修复移动端布局问题：
```typescript
// 问题代码
<div className="grid grid-cols-3 gap-4">

// 修复后
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
```

✅ 已修复：移动端布局问题
📝 已更新：TODO列表（剩余4项）

继续处理下一个？回复 "yes" 继续。
```

### `docs` - 自动生成文档

#### 场景：为API生成文档
```
用户输入：docs

AI响应：
📚 文档生成完成

📁 生成的文档文件：
1. docs/api/users.md - 用户API文档
2. docs/components/UserList.md - 组件使用说明
3. docs/deployment.md - 部署指南
4. README.md - 项目概览（已更新）

📖 API文档示例：

## 用户管理API

### 获取用户列表
```http
GET /api/users?page=1&limit=10&search=john

Response:
{
  "data": [
    {
      "id": "uuid",
      "name": "John Doe",
      "email": "john@example.com",
      "role": "user",
      "created_at": "2024-01-01T00:00:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 10,
    "total": 100
  }
}
```

### 创建用户
```http
POST /api/users

Body:
{
  "name": "Jane Doe",
  "email": "jane@example.com",
  "role": "user"
}

Response:
{
  "success": true,
  "data": {
    "id": "new-uuid",
    "name": "Jane Doe",
    "email": "jane@example.com"
  }
}
```

🎯 文档特性：
- 自动生成API接口文档
- 包含请求/响应示例
- 错误码说明
- 使用示例代码
```

## 🏆 最佳实践

### 🔄 标准开发流程

#### 新功能开发
```
1. session-start          # 开始会话，设置上下文
2. understand             # 理解项目结构
3. implement "功能描述"    # 6A流程实现功能
4. review                 # 代码质量检查
5. test                   # 生成测试用例
6. security-scan          # 安全检查
7. docs                   # 生成文档
8. session-end            # 总结会话
```

#### 代码维护流程
```
1. session-start          # 开始维护会话
2. find-todos             # 发现待处理项
3. fix-todos              # 批量处理TODO
4. refactor               # 代码重构
5. review                 # 质量检查
6. test                   # 更新测试
7. session-end            # 完成维护
```

#### 项目交接流程
```
1. understand             # 深度理解项目
2. explain-like-senior    # 获取专业解释
3. review                 # 全面代码审查
4. docs                   # 补充文档
5. test                   # 完善测试
```

### 🎯 命令组合策略

#### 快速原型开发
```
scaffold → implement → review
```

#### 生产级开发
```
understand → implement → review → test → security-scan → docs
```

#### 性能优化
```
review → refactor → test → security-scan
```

#### 技术债务清理
```
find-todos → fix-todos → refactor → test
```

## 🎨 工作流模板

### 模板1：企业级SaaS开发
```yaml
name: "企业级SaaS功能开发"
steps:
  - session-start
  - understand
  - implement: "基于6A流程的功能实现"
  - review: "代码质量和安全检查"
  - test: "单元测试和集成测试"
  - security-scan: "安全漏洞扫描"
  - docs: "API和组件文档"
  - session-end
```

### 模板2：快速MVP开发
```yaml
name: "快速MVP原型"
steps:
  - session-start
  - scaffold: "快速搭建基础结构"
  - implement: "核心功能实现"
  - review: "基础质量检查"
  - session-end
```

### 模板3：代码重构
```yaml
name: "代码重构和优化"
steps:
  - session-start
  - understand: "分析现有代码"
  - review: "识别重构点"
  - refactor: "执行重构"
  - test: "确保功能完整"
  - session-end
```

### 模板4：Bug修复
```yaml
name: "Bug修复流程"
steps:
  - session-start
  - understand: "理解问题上下文"
  - fix-todos: "修复具体问题"
  - test: "验证修复效果"
  - review: "确保无副作用"
  - session-end
```

## 💡 高级技巧

### 1. 命令链式调用
```bash
# 一次性执行多个命令
session-start && understand && implement "用户认证" && review && test
```

### 2. 条件执行
```bash
# 只有review通过才执行test
review && test
```

### 3. 并行处理
```bash
# 同时进行文档生成和测试
docs & test
```

### 4. 自定义工作流
创建自己的命令组合：
```bash
# 保存为脚本
echo "session-start && understand && implement" > my-workflow.sh
chmod +x my-workflow.sh
```

---

<div align="center">

**🎯 掌握这些示例，让你的AI编程效率提升10倍！**

[返回主页](README-NEW-PROJECT.md) • [快速开始](QUICK-START.md) • [架构文档](ARCHITECTURE.md)

</div>