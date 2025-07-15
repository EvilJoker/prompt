# 🚀 提示词分发系统 v2.0 使用指南

## 📋 系统概览

### 🎯 版本特性
- ✅ **简化命令**：基于 `>` 前缀的直观命令系统
- ✅ **三字母缩写**：支持简洁的三字母缩写匹配
- ✅ **统一配置**：合并全局配置到路由规则中
- ✅ **质量统一**：一致的质量基线和输出标准
- ✅ **Agent友好**：.md格式，支持Agent直接编辑

### 🏗️ 系统架构

```
提示词分发系统 v2.0
├── 01-prefix-router.md          # 🎯 智能路由配置
├── 02-common-standards.md       # 📐 公共标准
└── rules/                       # 📁 规则库
    ├── 00-project-init.md       # 🏆 项目开启：架构设计与初始化
    ├── quality-templates.md     # 📋 质量检查模板
    ├── 01-requirements.md       # 📝 需求分析
    ├── 02-design.md             # 🎨 功能设计
    ├── 03-develop.md            # 💻 代码开发
    ├── 04-testing.md            # 🧪 测试流程
    ├── 05-review.md             # 👀 代码评审
    ├── 07-debug.md              # 🔧 问题诊断修复
    ├── 08-deployment.md         # 🚀 部署发布
    ├── 09-optimization.md       # ⚡ 系统优化维护
    ├── 10-architecture-sync.md  # 🏗️ 架构同步
    └── 11-opensource.md         # 🔍 开源项目完整性检查
```

---

## 🎮 使用方法

### 🤖 Agent执行流程

每次对话开始时，Agent会自动执行以下流程：

```mermaid
graph TD
    A[用户输入] --> B[读取路由配置]
    B --> C[解析>前缀命令]
    C --> D[匹配路由规则]
    D --> E[加载主规则文件]
    E --> F[加载依赖标准]
    F --> G[执行具体任务]
    G --> H[质量检查输出]
```

### 📍 命令触发表

| 完整命令 | 三字母缩写 | 规则文件 | 执行模式 | 应用场景 |
|----------|------------|----------|----------|----------|
| `>init` | `>ini` | `00-project-init.md` | 3阶段式 | 项目架构设计与初始化 |
| `>req` | `>req` | `01-requirements.md` | 5步骤化 | 需求分析流程 |
| `>design` | `>des` | `02-design.md` | 6步骤化 | 功能设计流程 |
| `>dev` | `>dev` | `03-develop.md` | 7步骤化 | 代码开发流程 |
| `>test` | `>tes` | `04-testing.md` | 步骤化 | 测试流程 |
| `>review` | `>rev` | `05-review.md` | 一次性 | 代码评审 |
| `>debug` | `>deb` | `07-debug.md` | 自适应 | 问题诊断修复 |
| `>deploy` | `>dep` | `08-deployment.md` | 步骤化 | 部署发布 |
| `>optimize` | `>opt` | `09-optimization.md` | 持续化 | 系统优化维护 |
| `>arch` | `>arc` | `10-architecture-sync.md` | 步骤化 | 架构同步 |
| `>quality` | `>qua` | `quality-templates.md` | 参考 | 质量检查模板 |
| `>standard` | `>sta` | `02-common-standards.md` | 参考 | 开发标准 |
| `>help` | `>hel` | - | 帮助 | 显示所有命令帮助 |

### 🎯 使用示例

#### 基础使用
```
用户: >init 创建一个新的React项目
系统: 📋 执行信息
      - 应用规则：00-project-init.md (项目开启：架构设计与初始化)
      - 加载依赖：02-common-standards.md
      - 执行模式：3阶段式执行
      
      开始执行Stage 1：项目架构设计...
```

#### 三字母缩写
```
用户: >des 设计用户登录功能
系统: 📋 执行信息
      - 应用规则：02-design.md (功能设计流程)
      - 匹配命令：>des (design的缩写)
      - 执行模式：8步骤(双模式)执行
```

#### 帮助系统
```
用户: >help
系统: 📋 可用命令列表
      >init/ini  - 项目初始化
      >req       - 需求分析
      >design/des - 功能设计
      >dev       - 代码开发
      >test/tes  - 测试流程
      >review/rev - 代码评审
      >debug/deb - 问题诊断
      >deploy/dep - 部署发布
      >optimize/opt - 系统优化
      >arch/arc  - 架构同步
      >quality/qua - 质量检查
      >standard/sta - 开发标准
      >help/hel  - 帮助信息
```

#### 问题诊断
```
用户: >debug 系统登录失败问题排查
系统: 📋 执行信息
      - 应用规则：07-debug.md (问题诊断修复流程)
      - 执行模式：自适应(根据问题复杂度)
      - 智能分级：P0-P3级别响应
```

#### 组合使用
```
用户: >dev 基于设计文档实现登录功能
系统: 📋 执行信息
      - 应用规则：03-develop.md (代码开发流程)
      - 加载依赖：02-common-standards.md, 02-design.md
      - 执行模式：7步骤化执行
```

---

## 📊 质量基线

### 🎯 统一标准
所有规则都遵循统一的质量基线（来自 `02-common-standards.md`）：

- **测试覆盖率**：≥ 90%（核心模块 ≥ 95%）
- **代码复杂度**：≤ 10（建议 ≤ 7）
- **API响应时间**：≤ 500ms（核心接口 ≤ 200ms）
- **系统可用性**：≥ 99.9%
- **安全标准**：生产级安全要求

### 📋 输出规范
每个规则的输出都包含：
- **执行信息**：显示应用的规则和依赖
- **步骤化执行**：清晰的执行步骤和检查点
- **质量检查**：每步的质量验证清单
- **标准模板**：统一的文档输出格式

---

## 🔄 研发流程图

```mermaid
graph TD
    A[>init 项目初始化] --> B[>req 需求分析]
    B --> C[>design 功能设计]
    C --> D[>dev 代码开发]
    D --> E[>test 测试流程]
    E --> F[>review 代码评审]
    F --> G{质量检查}
    G -->|通过| H[>deploy 部署发布]
    G -->|不通过| I[>debug 问题诊断修复]
    I --> D
    H --> J[>optimize 系统优化维护]
    J --> K[>arch 架构同步]
    
    L[>quality 质量检查] --> G
    M[>standard 开发标准] --> D
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#ffebee
    style G fill:#e0f2f1
    style H fill:#fff8e1
    style I fill:#f1f8e9
    style J fill:#e3f2fd
    style K fill:#e8f5e8
    style L fill:#fff3e0
    style M fill:#f3e5f5
```

---

## 🛠️ 配置管理

### 📁 文件组织
```
.cursor/rules/
├── 01-prefix-router.md        # 智能路由配置（合并全局配置）
├── 02-common-standards.md     # 公共标准和规范模板
├── migration-guide.md         # 系统迁移指南
├── README.md                  # 本使用指南
└── rules/                     # 具体规则文件
    ├── 00-project-init.md     # 项目开启：架构设计与初始化
    ├── quality-templates.md   # 质量检查模板库
    ├── 01-requirements.md     # 需求分析：5步流程
    ├── 02-design.md          # 功能设计：6步流程
    ├── 03-develop.md         # 代码开发：7步流程
    ├── 04-testing.md         # 测试流程：测试策略
    ├── 05-review.md          # 代码评审：6维度评审
    ├── 07-debug.md           # 问题诊断修复：4阶段一体化
    ├── 08-deployment.md      # 部署发布：部署流程
    ├── 09-optimization.md    # 系统优化维护：5维度体系
    ├── 10-architecture-sync.md   # 架构同步：架构维护
    └── 11-opensource.md      # 开源项目完整性检查与创建：4阶段式
```

### 🔧 依赖关系
```yaml
规则依赖图:
  02-common-standards.md:     # 基础标准，被所有规则依赖
    - 质量基线
    - 编码规范
    - 文档模板
    
  quality-templates.md:       # 质量模板库
    depends: [02-common-standards.md]
    
  00-project-init.md:         # 项目开启
    depends: [quality-templates.md, 02-common-standards.md]
    
  01-requirements.md:         # 需求分析
    depends: [02-common-standards.md]
    
  02-design.md:               # 功能设计
    depends: [02-common-standards.md, quality-templates.md, 10-architecture-sync.md]
    
  03-develop.md:              # 代码开发
    depends: [02-design.md, 02-common-standards.md, quality-templates.md]
```

---

## 🚀 高级特性

### 🎯 智能匹配优先级
- **精确匹配**：完整命令具有最高优先级
- **三字母匹配**：支持简洁的三字母缩写
- **错误提示**：无效命令时显示帮助信息

### 📊 质量保证
- **统一基线**：所有规则共享相同的质量标准
- **步骤控制**：严格的步骤化执行控制
- **检查点**：每步都有明确的质量检查要求
- **可追溯性**：完整的执行路径和决策记录

### 🔧 可维护性
- **模块化设计**：清晰的职责分离和依赖关系
- **版本控制**：完整的版本管理和兼容性策略
- **扩展性**：支持新规则的无缝添加
- **监控统计**：规则使用情况的统计和分析

---

## 📚 最佳实践

### 👥 用户使用建议
1. **使用>前缀**：所有命令都以 `>` 开头
2. **优先完整命令**：重要操作使用完整命令确保准确性
3. **三字母缩写**：日常操作可使用三字母缩写提高效率
4. **及时确认**：对于步骤化流程，及时给出yes/no确认

### 🤖 Agent执行原则
1. **严格遵循**：必须按照规则要求的格式和步骤执行
2. **依赖加载**：自动加载相关的依赖规则和标准
3. **质量检查**：每步完成后进行质量自检
4. **用户反馈**：及时响应用户的确认和修改要求

### 🔧 系统维护要点
1. **定期更新**：根据使用反馈优化规则内容
2. **统计分析**：跟踪规则使用情况和效果
3. **质量监控**：确保输出质量的持续改进
4. **文档同步**：保持所有文档的及时更新

### 使用方式
1. 为项目添加 git submodule add https://github.com/EvilJoker/prompt.git .cursor

```bash
# ✅ 添加子模块
git submodule add -b branch https://github.com/EvilJoker/prompt.git .cursor

# ✅ 更新指定子模块到远程最新版本
git submodule update --remote .cursor

# ✅ 更新所有子模块到远程最新版本
git submodule update --remote

# ✅ 更新子模块到主仓库记录的版本
git submodule update

# ✅ 初始化并更新所有子模块
git submodule update --init --recursive

# ✅ 更新 进入模块目录，正常推送即可
cd .cursor 
```

---

## 🎯 下一步计划

### 短期目标
- [ ] 完成所有规则文件的创建和测试
- [ ] 验证命令路由的准确性和效率
- [ ] 收集用户反馈并优化使用体验

### 中期目标  
- [ ] 增加更多智能匹配场景
- [ ] 优化规则执行的性能
- [ ] 建立完整的使用统计和分析

### 长期目标
- [ ] 支持自定义规则的动态添加
- [ ] 建立规则效果的自动评估机制
- [ ] 实现基于AI的规则优化建议

🎯 **愿景**：打造最智能、最高效、最易用的AI辅助开发提示词系统！ 