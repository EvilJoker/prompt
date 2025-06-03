# 🔄 提示词系统迁移指南

## 📋 迁移概要

### 迁移目标
1. **解决Agent编辑限制**：.mdc → .md 格式迁移
2. **建立编号体系**：按研发流程添加 01-10 编号
3. **构建分发系统**：全局配置 + 前缀路由 + 公共标准

### 迁移架构对比

#### 旧架构（.mdc）
```
.cursor/rules/
├── generate-rules.mdc
├── requirements-rules.mdc
├── design/
│   ├── design-rules.mdc
│   └── design-spec-rules.mdc
├── develop/
│   ├── develop-rules.mdc
│   └── develop-spec-rules.mdc
├── bugfix-rules.mdc
├── debug-rules.mdc
├── review-rules.mdc
├── testing-rules.mdc
├── deployment-rules.mdc
├── maintenance-rules.mdc
└── performance-rules.mdc
```

#### 新架构（.md + 编号）
```
.cursor/rules/
├── 00-global-config.md       # 全局配置
├── 01-prefix-router.md       # 前缀路由
├── 02-common-standards.md    # 公共标准
└── rules/
    ├── 01-requirements.md    # 需求分析
    ├── 02-design.md         # 功能设计
    ├── 03-develop.md        # 代码开发
    ├── 04-testing.md        # 测试流程
    ├── 05-review.md         # 代码评审
    ├── 06-bugfix.md         # Bug修复
    ├── 07-debug.md          # 问题调试
    ├── 08-deployment.md     # 部署发布
    ├── 09-maintenance.md    # 维护优化
    └── 10-performance.md    # 性能优化
```

## 🗂️ 文件迁移映射表

| 旧文件 | 新文件 | 编号逻辑 | 变更说明 |
|--------|--------|----------|----------|
| `requirements-rules.mdc` | `01-requirements.md` | 需求是研发起点 | 合并spec版本，统一格式 |
| `design/design-rules.mdc` | `02-design.md` | 设计在需求之后 | 整合设计相关规则 |
| `develop/develop-rules.mdc` | `03-develop.md` | 开发基于设计 | 整合开发相关规则 |
| `testing-rules.mdc` | `04-testing.md` | 测试验证开发 | 增强测试策略 |
| `review-rules.mdc` | `05-review.md` | 评审保证质量 | 完善评审标准 |
| `bugfix-rules.mdc` | `06-bugfix.md` | 修复发现问题 | 优化修复流程 |
| `debug-rules.mdc` | `07-debug.md` | 调试定位问题 | 系统化调试方法 |
| `deployment-rules.mdc` | `08-deployment.md` | 部署交付价值 | 规范部署流程 |
| `maintenance-rules.mdc` | `09-maintenance.md` | 维护保证稳定 | 持续维护策略 |
| `performance-rules.mdc` | `10-performance.md` | 优化提升体验 | 性能优化方法 |
| `generate-rules.mdc` | `02-common-standards.md` | 转为公共标准 | 提取公共规范 |

## 🔧 迁移步骤

### 第一阶段：创建新架构文件
- [x] 创建 `00-global-config.md`
- [x] 创建 `01-prefix-router.md`  
- [x] 创建 `02-common-standards.md`
- [ ] 创建 `rules/` 目录下的编号文件

### 第二阶段：迁移内容
- [ ] 迁移需求分析规则到 `01-requirements.md`
- [ ] 迁移设计规则到 `02-design.md`
- [ ] 迁移开发规则到 `03-develop.md`
- [ ] 迁移其他专项规则

### 第三阶段：验证和清理
- [ ] 测试新系统的功能完整性
- [ ] 验证前缀路由的准确性
- [ ] 备份旧文件（重命名为.backup）
- [ ] 更新 README.md 文档

## 📝 迁移检查清单

### 内容完整性检查
- [ ] 所有原始规则内容已迁移
- [ ] 前缀触发机制正常工作
- [ ] 质量标准已统一
- [ ] 文档模板已标准化

### 功能验证检查
- [ ] 前缀匹配准确率 ≥ 95%
- [ ] 规则加载速度正常
- [ ] 依赖关系正确
- [ ] 冲突处理机制有效

### 用户体验检查
- [ ] 使用流程更加简洁
- [ ] 规则触发更加智能
- [ ] 输出质量更加一致
- [ ] 错误处理更加友好

## ⚠️ 迁移注意事项

### 兼容性考虑
1. **保留旧文件**：迁移过程中保留原文件作为备份
2. **渐进迁移**：可以先测试新系统，确认无误后再删除旧文件
3. **用户习惯**：保持用户熟悉的前缀和触发词

### 风险控制
1. **备份策略**：迁移前完整备份现有文件
2. **回滚计划**：如有问题可快速回滚到旧系统
3. **测试验证**：充分测试新系统的各种场景

### 性能优化
1. **加载效率**：新系统采用按需加载，提高响应速度
2. **内容去重**：消除重复内容，减少维护成本
3. **智能匹配**：提高规则匹配的准确性和效率

🎯 **迁移目标**：构建更智能、更高效、更易维护的提示词分发系统！ 