# 修复TODOs (Fix TODOs)

我将系统性地查找和解决代码库中的TODO注释，具有智能理解和跨会话连续性。

参数: `$ARGUMENTS` - 文件、目录或特定TODO模式

## 会话智能

我将跨会话维护TODO解决进度：

**会话文件（在当前项目目录中）：**
- `fix-todos/plan.md` - 找到的所有TODOs和解决状态
- `fix-todos/state.json` - 当前进度和决策

**重要提示：** 会话文件存储在当前项目目录的`fix-todos`文件夹中

**自动检测：**
- 如果会话存在：从最后一个TODO恢复
- 如果没有会话：扫描并创建新计划
- 命令：`resume`、`status`、`new`

## 使用工具
- **list_dir**: 检查fix-todos目录是否存在
- **view_files**: 读取会话状态和计划文件
- **search_by_regex**: 查找TODO标记
- **search_codebase**: 理解代码上下文
- **update_file**: 实现修复
- **write_to_file**: 创建会话文件
- **todo_write**: 跟踪修复进度

## 阶段1：发现与分析

**强制第一步：**
1. 检查当前工作目录中是否存在`fix-todos`目录
2. 如果目录存在，检查会话文件：
   - 查找`fix-todos/state.json`
   - 查找`fix-todos/plan.md`
   - 如果找到，从现有会话恢复
3. 如果没有目录或会话存在：

### 扩展思考
- 使用search_by_regex查找所有TODO模式
- 分析每个TODO的复杂性和依赖关系
- 评估修复所需的技能和时间
- 识别相关的TODOs可以批量处理

## 阶段2：智能分类

### TODO类型分析
```markdown
### 🔴 关键修复 (立即处理)
- FIXME: 功能性错误
- BUG: 已知问题
- HACK: 临时解决方案

### 🟡 功能实现 (计划处理)
- TODO: 新功能
- FEATURE: 功能增强
- IMPLEMENT: 待实现

### 🔵 优化改进 (可选处理)
- OPTIMIZE: 性能优化
- REFACTOR: 代码重构
- CLEANUP: 代码清理
```

## 阶段3：增量执行

### 修复策略
1. **简单修复** (< 10行代码)：立即实现
2. **中等修复** (10-50行)：分步实现
3. **复杂修复** (> 50行)：创建详细计划

### 验证流程
每次修复后：
- 运行相关测试
- 检查代码风格
- 验证功能完整性
- 更新文档（如需要）

## Trae使用示例

```
修复所有关键TODOs
```

```
修复特定文件的TODOs
```

```
恢复上次的TODO修复会话
```

```
显示TODO修复进度状态
```

## 会话状态管理

### state.json格式
```json
{
  "session_id": "fix-todos-20240101",
  "created_at": "2024-01-01T10:00:00Z",
  "last_updated": "2024-01-01T11:30:00Z",
  "total_todos": 15,
  "completed": 8,
  "in_progress": 2,
  "pending": 5,
  "current_todo": "src/utils/helper.js:42"
}
```

### plan.md格式
```markdown
# TODO修复计划

## 会话信息
- 开始时间: 2024-01-01 10:00
- 总计TODOs: 15个
- 已完成: 8个
- 进行中: 2个

## 修复进度

### ✅ 已完成
- [x] src/auth.js:25 - 实现密码验证
- [x] src/api.js:15 - 添加错误处理

### 🔄 进行中
- [ ] src/utils/helper.js:42 - 优化算法性能
- [ ] src/components/Modal.js:18 - 添加键盘导航

### ⏳ 待处理
- [ ] src/database.js:67 - 实现连接池
- [ ] src/tests/unit.js:33 - 添加边界测试
```

## 智能修复建议
- 分析TODO上下文和相关代码
- 提供多种实现方案
- 考虑性能和维护性影响
- 建议测试策略

## 重要提示
- 不添加AI归因或署名
- 保持现有代码风格和约定
- 在修复前备份重要更改
- 逐步验证每个修复
- 维护会话状态的准确性