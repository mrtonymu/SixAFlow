# 🚀 Trae智能命令集 - 快速开始指南

> 5分钟快速上手，让AI编程更高效！

## 📋 前置要求

- ✅ macOS / Linux / Windows
- ✅ AI编程环境：Trae AI / Cursor / VS Code + Copilot
- ✅ 网络连接（用于下载命令文件）

## 🎯 安装步骤

### Step 1: 一键安装

**方式A：在线安装（推荐）**
```bash
curl -sSL https://raw.githubusercontent.com/tonymumu/trae-commands-plugin/main/install.sh | bash
```

**方式B：本地安装**
```bash
# 下载项目
git clone https://github.com/tonymumu/trae-commands-plugin.git
cd trae-commands-plugin

# 运行安装脚本
chmod +x install.sh
./install.sh
```

### Step 2: 验证安装

安装完成后，你会看到类似输出：
```
🎉 安装完成！

📊 安装统计: 23/23 个命令安装成功
✅ 配置文件已创建
💡 命令安装在: ~/.trae/commands
```

### Step 3: 测试命令

在AI编程环境中输入：
```
session-start
```

如果看到AI开始执行会话初始化，说明安装成功！

## 🎬 第一次使用

### 场景：开发一个新功能

假设你要开发一个"用户管理模块"：

#### 1. 开始会话
```
session-start
```
AI会：
- 分析当前项目结构
- 设置开发上下文
- 准备工作环境

#### 2. 理解项目
```
understand
```
AI会：
- 识别技术栈
- 分析架构模式
- 梳理依赖关系

#### 3. 实现功能（6A流程）
```
implement "构建用户管理模块"
```

AI会按照6A流程执行：

**🎯 Align (需求对齐)**
```
目标：构建用户管理模块
输入：用户数据、权限配置
输出：CRUD界面、权限控制
边界：不包含第三方登录
```

**🏗️ Architect (架构设计)**
```
路由：/users/*
组件：UserList, UserForm, UserDetail
数据库：users表, roles表
UI：daisyUI卡片布局
```

**⚡ Atomize (任务拆解)**
```
□ 创建用户列表页面
□ 构建用户创建表单
□ 实现用户详情页面
□ 添加权限控制
□ 集成数据库操作
```

**✅ Approve (等待确认)**
AI会停下来等你说 "Approved"

**🔧 Automate (执行交付)**
AI开始编写代码

**📊 Assess (质量评估)**
AI进行自检和优化

#### 4. 代码审查
```
review
```

#### 5. 生成测试
```
test
```

#### 6. 结束会话
```
session-end
```

## 🎨 常用命令速查

### 🎬 会话管理
| 命令 | 功能 | 使用场景 |
|------|------|----------|
| `session-start` | 开始编程会话 | 每次开发开始时 |
| `session-end` | 结束会话总结 | 完成开发任务后 |

### 🧠 项目理解
| 命令 | 功能 | 使用场景 |
|------|------|----------|
| `understand` | 深度项目分析 | 接手新项目时 |
| `explain-like-senior` | 资深视角解释 | 学习复杂代码时 |

### ⚡ 开发核心
| 命令 | 功能 | 使用场景 |
|------|------|----------|
| `implement` | 6A流程实现功能 | 开发新功能时 |
| `scaffold` | 快速搭建骨架 | 创建新模块时 |
| `refactor` | 智能重构代码 | 优化现有代码时 |

### 🛡️ 质量保证
| 命令 | 功能 | 使用场景 |
|------|------|----------|
| `review` | 全面代码审查 | 代码完成后 |
| `test` | 智能生成测试 | 需要测试覆盖时 |
| `security-scan` | 安全漏洞扫描 | 上线前检查 |

### 🔧 维护工具
| 命令 | 功能 | 使用场景 |
|------|------|----------|
| `fix-todos` | 批量处理TODO | 清理技术债务时 |
| `docs` | 自动生成文档 | 需要文档时 |
| `format` | 代码格式化 | 统一代码风格时 |

## 💡 最佳实践

### 🔄 标准开发流程
```
session-start → understand → implement → review → test → docs → session-end
```

### 🎯 功能开发流程
```
implement → review → test → refactor → docs
```

### 🛡️ 质量保证流程
```
review → test → security-scan → format
```

### 🧹 维护流程
```
find-todos → fix-todos → refactor → docs
```

## 🚨 常见问题

### Q: 命令不生效怎么办？
**A**: 检查安装路径
```bash
ls -la ~/.trae/commands/
cat ~/.trae/commands/.trae-commands-config
```

### Q: 如何更新命令？
**A**: 重新运行安装脚本
```bash
./install.sh
```

### Q: 如何卸载？
**A**: 删除命令目录
```bash
rm -rf ~/.trae/commands
```

### Q: 支持哪些AI环境？
**A**: 
- ✅ Trae AI（原生支持）
- ✅ Cursor（完全兼容）
- ✅ VS Code + Copilot（兼容）
- ✅ 其他支持自定义命令的AI环境

### Q: 可以自定义命令吗？
**A**: 可以！编辑命令文件：
```bash
vim ~/.trae/commands/implement.md
```

## 🎓 进阶使用

### 自定义工作流
你可以根据项目需求调整6A流程：

**快速原型开发**
```
understand → scaffold → implement → review
```

**生产环境开发**
```
understand → implement → review → test → security-scan → docs
```

**维护现有项目**
```
understand → review → refactor → test → docs
```

### 团队协作
建议团队统一使用相同的命令集：
```bash
# 团队安装脚本
curl -sSL https://your-company.com/trae-commands/install.sh | bash
```

## 🔗 相关资源

- 📖 [详细文档](docs/USAGE.md)
- 🎯 [使用示例](examples/)
- 🤝 [贡献指南](CONTRIBUTING.md)
- 🐛 [问题反馈](https://github.com/tonymumu/trae-commands-plugin/issues)

## 🎉 开始你的AI编程之旅！

现在你已经掌握了基本使用方法，开始在你的项目中使用这些智能命令吧！

记住：**6A工作流是关键** - Align → Architect → Atomize → Approve → Automate → Assess

---

<div align="center">

**🚀 祝你编程愉快！**

[返回主页](README-NEW-PROJECT.md) • [查看示例](examples/) • [获取帮助](https://github.com/tonymumu/trae-commands-plugin/discussions)

</div>