---
type: global-config
version: "1.0"
description: "提示词分发系统全局配置"
---

# 🌐 全局配置文件

## 系统架构
```
提示词分发系统
├── 00-global-config.md        # 全局配置（本文件）
├── 01-prefix-router.md         # 前缀路由配置
├── 02-common-standards.md      # 公共标准规范
└── rules/                      # 具体规则文件
    ├── 01-requirements.md      # 需求分析
    ├── 02-design.md           # 功能设计
    ├── 03-develop.md          # 代码开发
    ├── 04-testing.md          # 测试流程
    ├── 05-review.md           # 代码评审
    ├── 06-bugfix.md           # Bug修复
    ├── 07-debug.md            # 问题调试
    ├── 08-deployment.md       # 部署发布
    ├── 09-maintenance.md      # 维护优化
    └── 10-performance.md      # 性能优化
```

## 分发机制
1. **Agent启动时读取**：00-global-config.md → 01-prefix-router.md → 02-common-standards.md
2. **根据前缀匹配**：解析用户输入，匹配对应规则
3. **动态加载规则**：加载主规则 + 依赖的公共标准
4. **执行质量控制**：按统一标准执行质量检查

## 质量基线
- **测试覆盖率**：≥ 90%
- **代码复杂度**：圈复杂度 < 10
- **响应时间**：页面加载 < 2秒，API响应 < 500ms
- **安全等级**：生产级安全标准
- **文档完整性**：100%关键功能有文档

## 版本控制
- **当前版本**：v1.0
- **兼容性**：向下兼容策略
- **更新机制**：增量更新，保持向后兼容 