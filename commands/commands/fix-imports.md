# 修复损坏的导入 (Fix Broken Imports)

我将系统性地修复由文件移动或重命名导致的损坏导入语句，具有跨会话的完整连续性。

参数: `$ARGUMENTS` - 特定路径或要修复的导入模式

## 会话智能

我将维护导入修复进度：

**会话文件（在当前项目目录中）：**
- `fix-imports/plan.md` - 所有损坏的导入和修复方案
- `fix-imports/state.json` - 解决进度

**重要提示：** 会话文件存储在当前项目根目录的`fix-imports`文件夹中

**自动检测：**
- 如果会话存在：从最后一个导入恢复
- 如果没有会话：扫描损坏的导入
- 命令：`resume`、`status`、`new`

## 使用工具
- **list_dir**: 检查fix-imports目录和项目结构
- **view_files**: 分析导入语句和会话状态
- **search_by_regex**: 查找导入模式和损坏的引用
- **search_codebase**: 定位文件和模块
- **update_file**: 修复导入语句
- **run_command**: 执行构建和类型检查
- **write_to_file**: 创建会话文件

## 阶段1：导入分析

**强制第一步：**
1. 检查当前工作目录中是否存在`fix-imports`目录
2. 如果目录存在，检查会话文件：
   - 查找`fix-imports/state.json`
   - 查找`fix-imports/plan.md`
   - 如果找到，从现有会话恢复
3. 如果没有目录或会话存在：
   - 扫描所有损坏的导入
   - 创建修复计划
   - 初始化进度跟踪
4. 显示导入问题摘要

**注意：** 始终在当前项目的`fix-imports/`文件夹中查找会话文件

### 导入模式检测
我将检测损坏的导入：

#### 导入类型识别
```javascript
// ES6 导入模式
import { Component } from './components/Component';
import Component from './components/Component';
import * as Utils from './utils';

// CommonJS 导入模式
const Component = require('./components/Component');
const { helper } = require('./utils/helper');

// 动态导入
const Component = await import('./components/Component');
```

## Trae使用示例

```
修复所有损坏的导入语句
```

```
修复特定目录的导入问题
```

```
恢复上次的导入修复会话
```

```
检查并修复TypeScript导入错误
```

## 导入问题分类

### 常见导入问题
```markdown
### 🔴 文件不存在
- 文件已被删除或移动
- 文件名拼写错误
- 路径不正确

### 🟡 路径问题
- 相对路径错误
- 绝对路径配置问题
- 别名路径未配置

### 🔵 模块问题
- 默认导出vs命名导出
- 模块未安装
- 版本兼容性问题
```

### 修复策略
```javascript
// 修复前
import { OldComponent } from './components/OldComponent';

// 修复后 - 文件已移动
import { OldComponent } from './components/ui/OldComponent';

// 修复前
import Component from './Component';

// 修复后 - 改为命名导出
import { Component } from './Component';
```

## 智能修复算法

### 文件定位算法
```markdown
### 🔍 文件查找策略
1. **精确匹配** - 在预期位置查找
2. **模糊搜索** - 在整个项目中搜索文件名
3. **相似性匹配** - 查找相似名称的文件
4. **历史记录** - 检查git历史中的文件移动
```

### 路径解析
```javascript
// 路径解析逻辑
const resolveImportPath = (currentFile, importPath, targetFile) => {
  const currentDir = path.dirname(currentFile);
  const targetDir = path.dirname(targetFile);
  const relativePath = path.relative(currentDir, targetFile);
  
  return relativePath.startsWith('.') ? relativePath : `./${relativePath}`;
};
```

## 会话状态管理

### state.json格式
```json
{
  "session_id": "fix-imports-20240101",
  "created_at": "2024-01-01T10:00:00Z",
  "last_updated": "2024-01-01T11:30:00Z",
  "total_imports": 25,
  "fixed_imports": 18,
  "failed_imports": 2,
  "pending_imports": 5,
  "current_file": "src/components/UserList.jsx"
}
```

### plan.md格式
```markdown
# 导入修复计划

## 扫描结果
- 总计损坏导入: 25个
- 已修复: 18个
- 修复失败: 2个
- 待处理: 5个

## 修复进度

### ✅ 已修复
- [x] src/App.js:3 - './components/Header' → './components/layout/Header'
- [x] src/utils/api.js:1 - './config' → './config/api'

### ❌ 修复失败
- [ ] src/legacy/old.js:5 - './removed-module' (文件已删除)
- [ ] src/test/mock.js:2 - './non-existent' (找不到文件)

### ⏳ 待处理
- [ ] src/components/UserList.jsx:8 - './UserCard'
- [ ] src/services/auth.js:12 - '../utils/token'
```

## 高级修复功能

### 批量重构
```javascript
// 批量路径更新
const batchUpdatePaths = {
  './components/': './components/ui/',
  './utils/': './shared/utils/',
  './services/': './api/services/'
};
```

### 智能建议
```markdown
### 💡 修复建议
1. **文件移动检测** - 基于git历史
2. **命名模式匹配** - 相似文件名建议
3. **依赖关系分析** - 基于使用模式
4. **最佳实践建议** - 改进导入结构
```

### 类型检查集成
```typescript
// TypeScript 导入修复
interface ImportFix {
  file: string;
  line: number;
  oldImport: string;
  newImport: string;
  confidence: number;
}

const fixTypeScriptImports = async (fixes: ImportFix[]) => {
  for (const fix of fixes) {
    if (fix.confidence > 0.8) {
      await updateImportStatement(fix);
    }
  }
};
```

## 验证和测试

### 修复验证
```javascript
// 验证修复结果
const validateFix = async (file, importPath) => {
  try {
    const resolved = await import(importPath);
    return { success: true, module: resolved };
  } catch (error) {
    return { success: false, error: error.message };
  }
};
```

### 构建测试
```bash
# 验证修复后的构建
npm run build
npm run type-check
npm run lint
```

## 报告生成

### 修复报告
```markdown
## 导入修复报告

### 📊 统计信息
- 扫描文件: 156个
- 发现问题: 25个
- 成功修复: 23个
- 修复失败: 2个

### 🔧 修复详情
| 文件 | 行号 | 原导入 | 新导入 | 状态 |
|------|------|--------|--------|------|
| App.js | 3 | ./Header | ./layout/Header | ✅ |
| api.js | 1 | ./config | ./config/api | ✅ |

### ⚠️ 需要手动处理
- src/legacy/old.js:5 - 引用已删除的模块
- src/test/mock.js:2 - 找不到目标文件
```

## 预防措施

### 导入最佳实践
```javascript
// 推荐的导入模式
// 1. 使用绝对路径别名
import { Component } from '@/components/Component';

// 2. 明确的文件扩展名
import { utils } from './utils/index.js';

// 3. 分组导入
import React from 'react';
import { useState, useEffect } from 'react';

import { Component } from '@/components';
import { api } from '@/services';
```

## 重要提示
- 不添加AI归因或署名
- 在修复前备份重要文件
- 验证每个修复的正确性
- 保持导入路径的一致性
- 提供详细的修复报告