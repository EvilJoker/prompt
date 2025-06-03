---
type: prefix-router
version: "1.0"
description: "智能前缀路由和规则分发系统"
---

# 🎯 前缀路由配置

## 🚀 Agent执行指令

### 核心执行流程
1. **首先读取全局配置**：加载 `00-global-config.md` 和 `02-common-standards.md`
2. **解析用户输入**：识别前缀、关键词、上下文
3. **匹配规则**：按优先级匹配对应的规则文件
4. **动态加载执行**：加载主规则 + 依赖的公共标准
5. **质量控制**：按统一基线执行质量检查

### 执行模板
```
📋 执行信息
- 应用规则：[规则名称]
- 加载依赖：02-common-standards.md
- 质量基线：按全局配置执行
- 执行模式：[步骤化/一次性]
```

---

## 📍 前缀路由表

### 1️⃣ 明确前缀匹配（最高优先级）

| 前缀 | 规则文件 | 执行模式 | 说明 |
|------|----------|----------|------|
| `需求` / `requirements` | `01-requirements.md` | 步骤化 | 需求分析流程 |
| `design` | `02-design.md` | 步骤化 | 功能设计流程 |
| `dev` | `03-develop.md` | 步骤化 | 代码开发流程 |
| `test` / `测试` | `04-testing.md` | 步骤化 | 测试流程 |
| `review` / `评审` | `05-review.md` | 一次性 | 代码评审 |
| `bugfix` / `修复` | `06-bugfix.md` | 步骤化 | Bug修复流程 |
| `debug` / `调试` | `07-debug.md` | 步骤化 | 问题调试 |
| `deploy` / `部署` | `08-deployment.md` | 步骤化 | 部署发布 |
| `维护` / `optimize` | `09-maintenance.md` | 步骤化 | 维护优化 |
| `性能` / `performance` | `10-performance.md` | 步骤化 | 性能优化 |

### 2️⃣ 关键词智能匹配（中等优先级）

| 关键词组 | 规则文件 | 触发条件 |
|----------|----------|----------|
| `需求分析`, `用户故事`, `需求澄清` | `01-requirements.md` | 包含任一关键词 |
| `设计方案`, `架构设计`, `功能设计` | `02-design.md` | 包含任一关键词 |
| `代码实现`, `编程`, `开发` | `03-develop.md` | 包含任一关键词 |
| `测试用例`, `测试计划`, `质量保证` | `04-testing.md` | 包含任一关键词 |
| `代码检查`, `质量评审`, `Code Review` | `05-review.md` | 包含任一关键词 |
| `错误修复`, `故障处理`, `Bug处理` | `06-bugfix.md` | 包含任一关键词 |
| `问题排查`, `故障定位`, `调试分析` | `07-debug.md` | 包含任一关键词 |
| `发布`, `上线`, `部署流程` | `08-deployment.md` | 包含任一关键词 |
| `系统维护`, `代码重构`, `优化改进` | `09-maintenance.md` | 包含任一关键词 |
| `性能分析`, `性能调优`, `响应优化` | `10-performance.md` | 包含任一关键词 |

### 3️⃣ 上下文智能推荐（低优先级）

| 上下文场景 | 推荐规则 | 推荐理由 |
|------------|----------|----------|
| 用户描述模糊需求 | `01-requirements.md` | 需要需求澄清流程 |
| 提及具体功能实现 | `02-design.md` → `03-develop.md` | 设计→开发流程 |
| 代码相关问题 | `07-debug.md` | 问题定位优先 |
| 提及用户反馈bug | `06-bugfix.md` | Bug修复流程 |
| 系统上线相关 | `08-deployment.md` | 部署发布流程 |

### 4️⃣ 默认规则（最低优先级）

| 场景 | 规则文件 | 说明 |
|------|----------|------|
| 无明确匹配 | `02-common-standards.md` | 使用通用开发标准 |
| 通用代码生成 | `02-common-standards.md` | 基础代码规范 |

---

## 🔄 动态加载机制

### 规则依赖关系
```yaml
01-requirements.md:
  depends: [02-common-standards.md]
  
02-design.md:
  depends: [02-common-standards.md, 01-requirements.md]
  
03-develop.md:
  depends: [02-common-standards.md, 02-design.md]
  
04-testing.md:
  depends: [02-common-standards.md, 03-develop.md]
  
05-review.md:
  depends: [02-common-standards.md]
  
06-bugfix.md:
  depends: [02-common-standards.md, 07-debug.md]
  
07-debug.md:
  depends: [02-common-standards.md]
  
08-deployment.md:
  depends: [02-common-standards.md, 04-testing.md]
  
09-maintenance.md:
  depends: [02-common-standards.md, 05-review.md]
  
10-performance.md:
  depends: [02-common-standards.md, 07-debug.md]
```

### 加载顺序
1. **基础加载**：全局配置 + 公共标准
2. **主规则加载**：根据匹配结果加载主规则文件
3. **依赖注入**：自动加载依赖的规则文件
4. **冲突检测**：检查规则间是否存在冲突
5. **执行准备**：整合所有规则，准备执行

---

## ⚠️ 冲突处理机制

### 优先级规则
1. **明确前缀** > **关键词匹配** > **上下文推荐** > **默认规则**
2. **用户明确指定** > **系统自动匹配**
3. **最新版本规则** > **旧版本规则**

### 冲突解决策略
- **规则冲突**：提示用户选择，显示冲突规则列表
- **标准冲突**：以公共标准为准，记录差异
- **依赖冲突**：按依赖关系图解决，提示循环依赖

---

## 📊 使用统计和优化

### 统计维度
- **规则使用频率**：跟踪各规则的使用情况
- **匹配准确率**：评估自动匹配的准确性
- **用户满意度**：跟踪用户对规则执行结果的反馈

### 自动优化
- **关键词词典更新**：基于用户使用习惯优化关键词
- **上下文模式学习**：改进上下文智能推荐
- **规则权重调整**：优化规则匹配优先级

🎯 **目标**：通过智能分发系统，实现精准、高效的规则匹配和执行！ 