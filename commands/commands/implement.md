# 智能实现引擎 (Smart Implementation Engine)

我将智能地从任何来源实现功能 - 完美适配您的项目架构，同时保持您的代码模式和标准。

参数: `$ARGUMENTS` - URLs、路径或要实现的功能描述

## 会话智能

我将检查现有的实现会话以无缝继续：

**会话文件（在当前项目目录中）：**
- `implement/plan.md` - 当前实现计划和进度
- `implement/state.json` - 会话状态和检查点

**重要提示：** 会话文件存储在当前项目根目录的`implement`文件夹中，不是在主目录或父文件夹中。如果会话存在，我将从确切的检查点恢复。否则，我将创建新的实现计划并跟踪整个过程的进度。

## 使用工具
- **list_dir**: 检查implement目录和项目结构
- **view_files**: 分析源代码和会话状态
- **search_codebase**: 理解项目架构和模式
- **web_search**: 研究外部资源和最佳实践
- **write_to_file**: 创建实现文件和会话文件
- **update_file**: 修改现有代码
- **run_command**: 执行测试和构建命令

## 阶段1：初始设置与分析

**强制第一步：**
1. 检查当前工作目录中是否存在`implement`目录
2. 如果目录存在，检查会话文件：
   - 查找`implement/state.json`
   - 查找`implement/plan.md`
   - 如果找到，从现有会话恢复
3. 如果没有目录或会话存在：
   - 创建`implement/plan.md`
   - 初始化`implement/state.json`
4. 在任何实现之前完成完整分析

**关键：** 使用当前目录中的`implement`文件夹。不要使用`$HOME/implement`或任何父目录路径

### 源检测
我将检查您提供的内容和项目结构：

#### 来源类型
- **Web URLs** (GitHub, GitLab, CodePen, JSFiddle, 文档站点)
- **本地路径** (文件、文件夹、现有代码)
- **实现计划** (带有检查清单的.md文件)
- **功能描述** (用于研究的功能描述)

#### 项目理解
- 分析现有架构模式
- 识别代码风格和约定
- 理解依赖管理
- 检查测试策略

## 阶段2：智能适配

### 架构适配
```markdown
### 🏗️ 架构分析
- **框架**: React/Vue/Angular/Next.js
- **状态管理**: Redux/Zustand/Context
- **样式方案**: Tailwind/Styled-Components/CSS Modules
- **构建工具**: Vite/Webpack/Parcel

### 🎨 代码风格
- **命名约定**: camelCase/PascalCase/kebab-case
- **文件结构**: 功能分组/类型分组
- **导入风格**: 相对路径/绝对路径
- **注释风格**: JSDoc/TypeScript
```

## Trae使用示例

```
实现GitHub上的React组件到我的项目中
```

```
基于设计稿实现用户界面
```

```
从API文档实现数据服务层
```

```
恢复上次的功能实现会话
```

## 实现策略

### 渐进式实现
1. **核心功能** - 基本功能实现
2. **样式适配** - 匹配项目UI风格
3. **集成测试** - 确保与现有代码兼容
4. **优化完善** - 性能和用户体验优化

### 代码适配模式
```javascript
// 原始代码 (外部来源)
function fetchUser(id) {
  return fetch(`/api/users/${id}`)
    .then(res => res.json());
}

// 适配后代码 (匹配项目模式)
import { apiClient } from '@/services/apiClient';
import { User } from '@/types/user';

export const fetchUser = async (id: string): Promise<User> => {
  try {
    const response = await apiClient.get(`/users/${id}`);
    return response.data;
  } catch (error) {
    logger.error('Failed to fetch user:', error);
    throw new ApiError('用户获取失败', error);
  }
};
```

## 会话状态管理

### state.json格式
```json
{
  "session_id": "implement-user-auth-20240101",
  "source_type": "github_repo",
  "source_url": "https://github.com/example/auth-component",
  "target_feature": "user-authentication",
  "created_at": "2024-01-01T10:00:00Z",
  "last_updated": "2024-01-01T11:30:00Z",
  "total_steps": 8,
  "completed_steps": 5,
  "current_step": "implementing-login-form",
  "checkpoints": [
    "analysis-complete",
    "dependencies-installed",
    "core-logic-implemented"
  ]
}
```

### plan.md格式
```markdown
# 用户认证功能实现计划

## 源信息
- **来源**: GitHub Repository
- **URL**: https://github.com/example/auth-component
- **功能**: 用户登录/注册系统

## 实现步骤

### ✅ 已完成
1. [x] 分析源代码架构
2. [x] 识别项目适配需求
3. [x] 安装必要依赖
4. [x] 实现核心认证逻辑
5. [x] 创建登录表单组件

### 🔄 进行中
6. [ ] 实现注册表单组件
7. [ ] 添加表单验证逻辑

### ⏳ 待处理
8. [ ] 集成测试和错误处理
9. [ ] 样式优化和响应式设计
10. [ ] 文档和使用示例
```

## 质量保证

### 代码质量检查
- **类型安全**: TypeScript类型定义
- **错误处理**: 完整的错误边界
- **性能优化**: 懒加载和缓存
- **可访问性**: ARIA标签和键盘导航

### 测试策略
```javascript
// 自动生成测试文件
describe('UserAuth Component', () => {
  it('should render login form', () => {
    render(<LoginForm />);
    expect(screen.getByRole('form')).toBeInTheDocument();
  });

  it('should handle form submission', async () => {
    const mockSubmit = jest.fn();
    render(<LoginForm onSubmit={mockSubmit} />);
    
    fireEvent.click(screen.getByRole('button', { name: '登录' }));
    await waitFor(() => {
      expect(mockSubmit).toHaveBeenCalled();
    });
  });
});
```

## 智能特性

### 依赖管理
- 自动检测和安装所需依赖
- 版本兼容性检查
- 依赖冲突解决

### 文档生成
- 自动生成使用文档
- 包含代码示例
- API参考文档

### 最佳实践应用
- 安全性最佳实践
- 性能优化建议
- 可维护性改进

## 重要提示
- 不添加AI归因或署名
- 完美适配现有项目架构
- 保持代码风格一致性
- 提供完整的测试覆盖
- 维护详细的实现文档