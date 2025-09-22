# 智能测试运行器 - 上下文感知 (Smart Test Runner - Context Aware)

我将基于您当前的上下文智能运行测试，并积极帮助修复失败。

## 上下文检测优先

让我理解我所处的上下文：

### 1. 冷启动（无先前上下文）
- 运行完整测试套件和覆盖率
- 生成完整的健康报告
- 识别慢性失败

### 2. 活跃会话（您正在实现功能）
- 检查git diff查看修改的文件
- 读取会话目标
- 仅测试您正在工作的内容
- 编码时增量测试

### 3. 命令后上下文
- 在`/scaffold`后：测试新组件
- 在`/fix-todos`后：测试修改的文件
- 在`/fix-imports`后：重新运行之前失败的测试
- 在`/security-scan`后：安全相关测试
- 在`/format`后：仅快速冒烟测试

### 4. 调试上下文（之前的测试失败）
- 专注于失败的测试，详细输出
- 添加策略性调试日志
- 在隔离模式下运行

### 5. 提交前上下文
- 完整套件 + lint + 类型检查
- PR的覆盖率报告
- 不允许跳过测试

## 使用工具
- **search_by_regex**: 查找测试配置和模式
- **view_files**: 分析测试配置和CI/CD工作流
- **run_command**: 执行测试命令
- **search_codebase**: 理解测试架构
- **update_file**: 修复测试代码
- **todo_write**: 跟踪测试修复进度

## 阶段1：深度项目分析

使用原生工具理解您的测试设置：
- **搜索** 项目根目录中的配置文件
- **读取** 测试配置和CI/CD工作流
- **查找** 测试模式以理解测试风格

### 测试框架检测
```javascript
// 自动检测测试框架
const testFrameworks = {
  jest: 'jest.config.js|package.json',
  vitest: 'vitest.config.js|vite.config.js',
  mocha: 'mocha.opts|.mocharc.json',
  cypress: 'cypress.config.js',
  playwright: 'playwright.config.js'
};
```

## Trae使用示例

```
运行所有测试并生成覆盖率报告
```

```
只测试修改的文件
```

```
运行失败的测试并修复问题
```

```
执行端到端测试
```

## 智能测试策略

### 上下文感知测试
```markdown
### 🔍 文件变更检测
- 检测git diff中的修改文件
- 运行相关测试套件
- 跳过不相关的测试

### ⚡ 增量测试
- 仅运行受影响的测试
- 缓存测试结果
- 并行执行优化

### 🎯 焦点测试
- 专注于失败的测试
- 详细错误输出
- 调试模式运行
```

### 测试类型识别
```javascript
// 测试类型分类
const testTypes = {
  unit: '*.test.js|*.spec.js',
  integration: '*.integration.test.js',
  e2e: 'cypress/**/*.spec.js|playwright/**/*.spec.js',
  performance: '*.perf.test.js'
};
```

## 测试修复助手

### 常见问题诊断
```markdown
### 🐛 常见测试失败
- **异步问题**: 缺少await或Promise处理
- **模拟问题**: Mock配置不正确
- **环境问题**: 测试环境配置错误
- **依赖问题**: 模块导入或依赖注入问题

### 🔧 自动修复建议
- 添加缺失的await
- 修复Mock配置
- 更新测试数据
- 修复断言逻辑
```

### 测试增强
```javascript
// 自动添加测试改进
describe('UserService', () => {
  beforeEach(() => {
    // 清理模拟和状态
    jest.clearAllMocks();
  });

  it('should handle API errors gracefully', async () => {
    // 模拟API错误
    mockApiClient.get.mockRejectedValue(new Error('Network error'));
    
    await expect(userService.getUser('123')).rejects.toThrow('Network error');
    expect(logger.error).toHaveBeenCalledWith('Failed to fetch user:', expect.any(Error));
  });
});
```

## 测试报告和分析

### 覆盖率分析
```markdown
### 📊 覆盖率报告
- **语句覆盖率**: 85% (目标: 90%)
- **分支覆盖率**: 78% (目标: 85%)
- **函数覆盖率**: 92% (目标: 95%)
- **行覆盖率**: 87% (目标: 90%)

### 🎯 改进建议
- 添加边界条件测试
- 增加错误处理测试
- 提高集成测试覆盖率
```

### 性能监控
```javascript
// 测试性能监控
describe('Performance Tests', () => {
  it('should load user list within 100ms', async () => {
    const startTime = performance.now();
    await userService.getUsers();
    const endTime = performance.now();
    
    expect(endTime - startTime).toBeLessThan(100);
  });
});
```

## CI/CD集成

### 自动化测试流程
```yaml
# GitHub Actions 测试配置
name: Test Suite
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - name: Install dependencies
        run: npm ci
      - name: Run tests
        run: npm run test:coverage
      - name: Upload coverage
        uses: codecov/codecov-action@v3
```

### 测试质量门禁
```javascript
// 质量门禁配置
module.exports = {
  coverageThreshold: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80
    }
  },
  testTimeout: 10000,
  maxWorkers: '50%'
};
```

## 调试和故障排除

### 测试调试工具
```javascript
// 调试辅助工具
const debugTest = (testName, fn) => {
  return process.env.DEBUG_TESTS 
    ? it.only(testName, fn)
    : it(testName, fn);
};

// 使用示例
debugTest('should handle user creation', async () => {
  console.log('Debug: Testing user creation...');
  // 测试逻辑
});
```

### 错误分析
```markdown
### 🔍 错误分析模式
1. **收集错误信息** - 完整的堆栈跟踪
2. **识别根本原因** - 分析错误模式
3. **提供修复建议** - 具体的解决方案
4. **验证修复** - 重新运行测试确认
```

## 重要提示
- 不添加AI归因或署名
- 基于项目上下文智能选择测试策略
- 提供可操作的修复建议
- 保持测试的可维护性和可读性
- 优化测试执行性能