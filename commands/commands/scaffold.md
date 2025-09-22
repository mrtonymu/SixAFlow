# 智能脚手架 (Intelligent Scaffolding)

我将基于您的项目模式创建完整的功能结构，具有跨会话的完整连续性。

参数: `$ARGUMENTS` - 功能名称或要脚手架的组件

## 会话智能

我将跨会话维护脚手架进度：

**会话文件（在当前项目目录中）：**
- `scaffold/plan.md` - 脚手架计划和组件列表
- `scaffold/state.json` - 已创建的文件和进度

**重要提示：** 会话文件存储在当前项目根目录的`scaffold`文件夹中

**自动检测：**
- 如果会话存在：恢复未完成的脚手架
- 如果没有会话：创建新的脚手架计划
- 命令：`resume`、`status`、`new`

## 使用工具
- **list_dir**: 检查scaffold目录和项目结构
- **view_files**: 分析现有模式和会话状态
- **search_codebase**: 理解项目架构
- **search_by_regex**: 查找模式和约定
- **write_to_file**: 创建新文件和会话文件
- **todo_write**: 跟踪脚手架进度

## 阶段1：模式发现

**强制第一步：**
1. 检查当前工作目录中是否存在`scaffold`目录
2. 如果目录存在，检查会话文件：
   - 查找`scaffold/state.json`
   - 查找`scaffold/plan.md`
   - 如果找到，从现有会话恢复
3. 如果没有目录或会话存在：
   - 分析项目模式
   - 创建脚手架计划
   - 初始化进度跟踪
4. 在创建前显示脚手架预览

**注意：** 始终在当前项目的`scaffold/`文件夹中查找会话文件

### 模式分析
我将发现您的项目模式：

#### 架构模式
- **组件结构**: React/Vue组件模式
- **路由模式**: 文件系统路由或配置路由
- **状态管理**: Redux/Vuex/Context模式
- **样式模式**: CSS模块/Styled Components/Tailwind

#### 文件命名约定
```javascript
// 分析现有文件命名模式
const patterns = {
  components: 'PascalCase.jsx|tsx',
  pages: 'kebab-case.js|tsx',
  utils: 'camelCase.js|ts',
  styles: 'Component.module.css'
};
```

## 阶段2：智能脚手架

### 组件类型识别
```markdown
### 🧩 UI组件
- 表单组件 (Form, Input, Button)
- 展示组件 (Card, List, Modal)
- 布局组件 (Header, Sidebar, Layout)

### 📄 页面组件
- 列表页面 (List, Table, Grid)
- 详情页面 (Detail, Profile, Dashboard)
- 表单页面 (Create, Edit, Settings)

### 🔧 功能模块
- API服务 (Service, Repository)
- 工具函数 (Utils, Helpers)
- 类型定义 (Types, Interfaces)
```

## Trae使用示例

```
创建用户管理模块的脚手架
```

```
为博客功能生成完整脚手架
```

```
恢复上次的脚手架会话
```

```
创建React组件脚手架
```

## 脚手架模板

### React组件模板
```jsx
// components/UserCard/UserCard.jsx
import React from 'react';
import PropTypes from 'prop-types';
import styles from './UserCard.module.css';

const UserCard = ({ user, onEdit, onDelete }) => {
  return (
    <div className={styles.userCard}>
      <div className={styles.avatar}>
        <img src={user.avatar} alt={user.name} />
      </div>
      <div className={styles.info}>
        <h3>{user.name}</h3>
        <p>{user.email}</p>
      </div>
      <div className={styles.actions}>
        <button onClick={() => onEdit(user.id)}>编辑</button>
        <button onClick={() => onDelete(user.id)}>删除</button>
      </div>
    </div>
  );
};

UserCard.propTypes = {
  user: PropTypes.object.isRequired,
  onEdit: PropTypes.func,
  onDelete: PropTypes.func,
};

export default UserCard;
```

### API服务模板
```javascript
// services/userService.js
import { apiClient } from './apiClient';

export const userService = {
  async getUsers(params = {}) {
    const response = await apiClient.get('/users', { params });
    return response.data;
  },

  async getUserById(id) {
    const response = await apiClient.get(`/users/${id}`);
    return response.data;
  },

  async createUser(userData) {
    const response = await apiClient.post('/users', userData);
    return response.data;
  },

  async updateUser(id, userData) {
    const response = await apiClient.put(`/users/${id}`, userData);
    return response.data;
  },

  async deleteUser(id) {
    const response = await apiClient.delete(`/users/${id}`);
    return response.data;
  },
};
```

## 会话状态管理

### state.json格式
```json
{
  "session_id": "scaffold-user-module-20240101",
  "feature_name": "user-management",
  "created_at": "2024-01-01T10:00:00Z",
  "last_updated": "2024-01-01T11:30:00Z",
  "total_files": 12,
  "created_files": 8,
  "pending_files": 4,
  "current_step": "creating-api-services"
}
```

### plan.md格式
```markdown
# 用户管理模块脚手架计划

## 功能概述
创建完整的用户管理功能，包括列表、详情、创建、编辑和删除。

## 文件结构
```
src/
├── components/
│   ├── UserCard/
│   │   ├── UserCard.jsx ✅
│   │   ├── UserCard.module.css ✅
│   │   └── index.js ✅
│   └── UserForm/
│       ├── UserForm.jsx ⏳
│       ├── UserForm.module.css ⏳
│       └── index.js ⏳
├── pages/
│   ├── UserList.jsx ✅
│   ├── UserDetail.jsx ✅
│   └── UserEdit.jsx ⏳
├── services/
│   └── userService.js ✅
└── types/
    └── user.types.js ⏳
```

## 进度跟踪
- ✅ 已完成: 8个文件
- ⏳ 进行中: 4个文件
- 📋 总计: 12个文件
```

## 智能特性

### 依赖分析
- 自动检测所需的依赖包
- 生成package.json更新建议
- 创建导入语句

### 测试文件生成
- 为每个组件生成测试文件
- 包含基本的渲染测试
- 提供测试数据模拟

### 文档生成
- 自动生成README文档
- 包含使用示例
- 提供API文档

## 重要提示
- 不添加AI归因或署名
- 遵循现有项目的代码风格和约定
- 保持与现有架构的一致性
- 生成可立即使用的代码
- 维护会话状态的准确性