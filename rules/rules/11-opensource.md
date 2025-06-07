---
type: project_check
number: "10"
version: "1.0"
description: "开源项目完整性检查和创建助手"
execution_mode: "step_by_step"
depends: ["02-common-standards.md"]
---

# 🔍 开源项目完整性检查与创建助手

## 🎯 触发条件
当用户输入包含以下关键词时自动应用此规则：
- `开源项目检查` / `opensource check`
- `项目完整性` / `project completeness`
- `开源规范` / `open source standards`
- `项目创建` / `create project`
- `开源文档` / `opensource documentation`

执行时请说明："本次回答应用了：10-opensource.md"

## 📋 开源项目必备要素清单

### 🏆 一级必备文件 (Critical - 必须有)
- [ ] **README.md** - 项目介绍和使用指南
  - 项目简介与目标
  - 特性列表
  - 快速开始指南
  - 安装说明
  - 基本使用示例
- [ ] **LICENSE** - 开源许可证
- [ ] **CHANGELOG.md** - 版本变更记录
- [ ] **.gitignore** - Git忽略文件配置

### 🎯 二级重要文件 (Important - 强烈推荐)
- [ ] **CONTRIBUTING.md** - 贡献指南
- [ ] **CODE_OF_CONDUCT.md** - 行为准则
- [ ] **SECURITY.md** - 安全政策
- [ ] **docs/** - 详细文档目录
- [ ] **examples/** - 示例代码目录

### 🛠️ 三级推荐文件 (Recommended - 建议添加)
- [ ] **ROADMAP.md** - 项目路线图
- [ ] **FAQ.md** - 常见问题解答
- [ ] **GOVERNANCE.md** - 项目治理结构
- [ ] **SUPPORT.md** - 获取帮助指南
- [ ] **ARCHITECTURE.md** - 架构设计文档
- [ ] **API.md** - API文档

### ⚙️ 四级配置文件 (Configuration - 技术配置)
- [ ] **package.json** / **requirements.txt** / **Cargo.toml** - 依赖管理
- [ ] **Dockerfile** - 容器化配置
- [ ] **docker-compose.yml** - 多容器编排
- [ ] **.github/workflows/** - CI/CD配置
- [ ] **.pre-commit-config.yaml** - 代码质量检查

## 🔍 检查执行流程

### Step 1: 项目扫描
```bash
# 1. 扫描当前项目目录结构
# 2. 检查根目录必备文件
# 3. 扫描源码目录结构
# 4. 识别项目技术栈
# 5. 分析现有文档完整性
```

### Step 2: 缺失分析
```yaml
缺失文件分析:
  critical_missing: []     # 一级必备缺失 (阻塞发布)
  important_missing: []    # 二级重要缺失 (影响体验)
  recommended_missing: []  # 三级推荐缺失 (影响专业度)
  config_missing: []       # 四级配置缺失 (影响自动化)
```

### Step 3: 优先级排序
1. **P0 (紧急)**: README.md, LICENSE 缺失 - 必须立即创建
2. **P1 (高)**: CHANGELOG.md, CONTRIBUTING.md 缺失 - 发布前创建
3. **P2 (中)**: 文档目录、安全政策缺失 - 后续完善
4. **P3 (低)**: 治理文档、配置优化 - 项目成熟后添加

### Step 4: 自动创建
根据检查结果，自动创建缺失的文件，并提供模板内容。

## 📄 核心文档模板

### README.md 完整模板
```markdown
# 项目名称

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Build Status](https://github.com/username/repo/workflows/CI/badge.svg)](https://github.com/username/repo/actions)
[![Version](https://img.shields.io/github/v/release/username/repo)](https://github.com/username/repo/releases)
[![Downloads](https://img.shields.io/github/downloads/username/repo/total)](https://github.com/username/repo/releases)

## 📖 项目简介
[一句话描述项目是什么，解决什么问题]

详细的项目描述，包括：
- 🎯 **项目目标**: 这个项目要解决什么问题
- 🚀 **核心价值**: 为用户带来什么价值
- 🔍 **应用场景**: 在什么情况下使用

## ✨ 主要特性
- 🚀 **特性1**: [具体描述，突出优势]
- 💡 **特性2**: [具体描述，突出优势]
- 🔒 **特性3**: [具体描述，突出优势]
- ⚡ **特性4**: [具体描述，突出优势]

## 🚀 快速开始

### 📋 环境要求
- [运行环境，如 Node.js >= 16.0.0]
- [依赖要求，如 Python >= 3.8]
- [系统要求，如 macOS/Linux/Windows]

### 📦 安装

#### 方式一：包管理器安装 (推荐)
```bash
# npm
npm install your-package-name

# yarn  
yarn add your-package-name

# pip
pip install your-package-name
```

#### 方式二：源码安装
```bash
git clone https://github.com/username/repo.git
cd repo
npm install  # 或其他安装命令
```

### 🎯 基本使用

#### 快速示例
```javascript
// 引入
const yourPackage = require('your-package-name');

// 基本使用
const result = yourPackage.basicFunction('参数');
console.log(result);
```

#### 高级用法
```javascript
// 更复杂的使用示例
const config = {
  option1: 'value1',
  option2: 'value2'
};

const advanced = new yourPackage.AdvancedClass(config);
advanced.doSomething();
```

## 📚 详细文档
- [📖 完整文档](docs/README.md)
- [🔧 API 参考](docs/api.md)
- [💡 使用示例](examples/)
- [🎓 教程指南](docs/tutorial.md)
- [❓ 常见问题](FAQ.md)

## 🛠️ 开发指南

### 本地开发
```bash
# 克隆项目
git clone https://github.com/username/repo.git
cd repo

# 安装依赖
npm install

# 启动开发模式
npm run dev

# 运行测试
npm test

# 构建
npm run build
```

### 项目结构
```
project/
├── src/                # 源代码
├── docs/              # 文档
├── examples/          # 示例
├── tests/             # 测试
├── scripts/           # 构建脚本
└── README.md         # 项目说明
```

## 🤝 贡献
我们欢迎所有形式的贡献！

- 🐛 [报告问题](https://github.com/username/repo/issues/new?template=bug_report.md)
- 💡 [提出建议](https://github.com/username/repo/issues/new?template=feature_request.md)
- 📖 [改进文档](https://github.com/username/repo/blob/main/CONTRIBUTING.md)
- 🔧 [提交代码](https://github.com/username/repo/blob/main/CONTRIBUTING.md)

请查看 [贡献指南](CONTRIBUTING.md) 了解详细信息。

## 📊 项目状态
- ✅ **稳定版本**: v1.0.0
- 🔄 **开发状态**: 活跃开发中
- 🧪 **测试覆盖率**: 85%+
- 📈 **性能基准**: [基准测试结果](docs/benchmarks.md)

## 📄 许可证
本项目采用 [MIT 许可证](LICENSE) - 查看 LICENSE 文件了解详情。

## 📞 支持与联系
- 🐛 [报告问题](https://github.com/username/repo/issues)
- 💬 [讨论区](https://github.com/username/repo/discussions)
- 📧 [邮件联系](mailto:maintainer@example.com)
- 🐦 [Twitter](https://twitter.com/username)

## 🙏 致谢
感谢所有贡献者的努力！

[![Contributors](https://contrib.rocks/image?repo=username/repo)](https://github.com/username/repo/graphs/contributors)

## 🔗 相关项目
- [相关项目1](https://github.com/username/related1) - 简要说明
- [相关项目2](https://github.com/username/related2) - 简要说明
```

### LICENSE 选择指南
```text
# 主流开源许可证选择指南

MIT License (推荐) ⭐
- ✅ 最宽松，商业友好
- ✅ 简单易懂
- ✅ 社区接受度最高
- 适用：大多数开源项目

Apache License 2.0
- ✅ 企业级项目首选
- ✅ 专利保护
- ✅ 商业友好
- 适用：企业开源项目

GPL v3
- ✅ 强制开源（Copyleft）
- ❌ 商业使用限制
- 适用：要求衍生作品也开源

BSD 3-Clause
- ✅ 学术项目友好
- ✅ 简单宽松
- 适用：研究项目
```

### CHANGELOG.md 模板
```markdown
# 变更日志

所有重要的项目变更都将记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [未发布]

### 新增 Added
- 新功能描述

### 变更 Changed  
- 现有功能的变更

### 弃用 Deprecated
- 即将移除的功能

### 移除 Removed
- 已移除的功能

### 修复 Fixed
- Bug修复

### 安全 Security
- 安全相关的修复

## [1.0.0] - 2024-01-01

### 新增
- 🎉 初始版本发布
- ✨ 核心功能实现
- 📚 完整文档
- 🧪 测试套件

### 已知问题
- ⚠️  问题描述及临时解决方案
```

### CONTRIBUTING.md 模板
```markdown
# 🤝 贡献指南

感谢您对本项目的关注！我们欢迎各种形式的贡献。

## 🚀 贡献方式

### 🐛 报告问题
1. 搜索 [现有Issues](../../issues) 避免重复
2. 使用 [Bug报告模板](../../issues/new?template=bug_report.md)
3. 提供详细的复现步骤和环境信息

### 💡 功能建议
1. 在 [讨论区](../../discussions) 分享你的想法
2. 使用 [功能请求模板](../../issues/new?template=feature_request.md)
3. 等待社区讨论和反馈

### 📖 文档改进
- 修正错别字和语法错误
- 补充缺失的文档
- 改进示例和教程
- 翻译文档

### 🔧 代码贡献

#### 开发流程
1. **Fork** 本仓库到你的GitHub账户
2. **Clone** 你的Fork到本地
3. **创建** 新的功能分支
4. **开发** 并测试你的更改
5. **提交** 有意义的commit
6. **推送** 到你的Fork
7. **创建** Pull Request

```bash
# 1. 克隆你的fork
git clone https://github.com/yourusername/repo.git
cd repo

# 2. 添加上游仓库
git remote add upstream https://github.com/originalowner/repo.git

# 3. 创建功能分支
git checkout -b feature/amazing-feature

# 4. 开发完成后提交
git add .
git commit -m "feat: add amazing feature"

# 5. 推送到你的fork
git push origin feature/amazing-feature

# 6. 在GitHub上创建Pull Request
```

## 🛠️ 开发环境设置

### 环境要求
- Node.js >= 16.0.0
- npm >= 7.0.0
- Git >= 2.20.0

### 初始化
```bash
# 安装依赖
npm install

# 运行测试
npm test

# 启动开发服务器
npm run dev

# 代码格式化
npm run format

# 代码检查
npm run lint
```

## 📋 开发规范

### 代码风格
- 使用 ESLint + Prettier
- 遵循 [Airbnb JavaScript 规范](https://github.com/airbnb/javascript)
- 变量命名使用驼峰命名法
- 函数和类名使用Pascal命名法

### 提交规范
遵循 [约定式提交](https://www.conventionalcommits.org/zh-hans/v1.0.0/)：

```
<类型>[可选范围]: <简短描述>

[可选正文]

[可选页脚]
```

**类型说明：**
- `feat`: 新功能
- `fix`: Bug修复  
- `docs`: 文档更新
- `style`: 代码格式调整
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建或工具变更

**示例：**
```
feat(auth): add user authentication system

- Implement JWT token authentication
- Add login/logout endpoints  
- Create user session management

Closes #123
```

### 测试要求
- 新功能必须包含测试
- 保持测试覆盖率 > 80%
- 所有测试必须通过
- 包含单元测试和集成测试

### Pull Request 要求
- 清晰的标题和描述
- 链接相关的Issue
- 通过所有CI检查
- 代码审查通过
- 文档更新（如需要）

## 🎯 高质量PR指南

### PR标题格式
```
type(scope): description

Examples:
feat(api): add user authentication
fix(ui): resolve button alignment issue
docs(readme): update installation guide
```

### PR描述模板
```markdown
## 🎯 更改类型
- [ ] 🐛 Bug修复
- [ ] ✨ 新功能
- [ ] 📚 文档更新
- [ ] 🎨 代码格式
- [ ] ♻️ 代码重构
- [ ] ⚡ 性能优化

## 📋 更改说明
简要描述你的更改...

## 🧪 测试
- [ ] 添加了测试用例
- [ ] 所有测试通过
- [ ] 手动测试通过

## 📸 截图/演示
如果是UI更改，请添加截图或GIF

## 📋 检查清单
- [ ] 代码遵循项目规范
- [ ] 自我审查完成
- [ ] 添加了必要的注释
- [ ] 更新了相关文档
- [ ] 没有新的警告产生
```

## 🎉 认可贡献者
所有贡献者都会被添加到项目的贡献者列表中，感谢你们的努力！

## 📞 获取帮助
如果在贡献过程中遇到问题：
- 📖 查看 [项目文档](docs/)
- 💬 在 [讨论区](../../discussions) 提问
- 📧 发邮件给维护者
- 🐦 在社交媒体上联系我们

## 📄 行为准则
请遵守我们的 [行为准则](CODE_OF_CONDUCT.md)，营造友好的协作环境。
```

## ✅ 质量评分标准

### 评分体系 (100分制)
- **一级必备 (40分)**: 
  - README.md (15分) - 项目门面
  - LICENSE (10分) - 法律保护
  - CHANGELOG.md (10分) - 版本追踪  
  - .gitignore (5分) - 基础配置

- **二级重要 (30分)**:
  - CONTRIBUTING.md (10分) - 社区参与
  - CODE_OF_CONDUCT.md (10分) - 社区规范
  - SECURITY.md (10分) - 安全保障

- **三级推荐 (20分)**:
  - docs/ 目录 (10分) - 详细文档
  - examples/ 目录 (5分) - 使用示例  
  - FAQ.md (5分) - 常见问题

- **四级配置 (10分)**:
  - CI/CD配置 (5分) - 自动化
  - 依赖管理 (3分) - 环境配置
  - 容器化 (2分) - 部署支持

### 项目评级
- **🏆 优秀 (90-100分)**: 完整的开源项目，可作为最佳实践参考
- **✅ 良好 (70-89分)**: 基本完整，适合公开发布和推广
- **⚠️  及格 (50-69分)**: 缺少重要文件，需要补充完善
- **❌ 不合格 (<50分)**: 严重缺失，不建议公开发布

## 🎯 执行示例

当用户输入："检查我的开源项目完整性" 或 "开源项目检查"

### 系统自动执行：
1. **📊 项目扫描**
   - 扫描目录结构
   - 识别技术栈
   - 检查现有文件

2. **📋 生成报告**
   ```
   🔍 开源项目完整性检查报告
   
   📊 总体评分: 75/100 (良好)
   
   ✅ 已有文件:
   - README.md ✓
   - LICENSE ✓
   - .gitignore ✓
   
   ❌ 缺失文件:
   - CHANGELOG.md (P1-高优先级)
   - CONTRIBUTING.md (P1-高优先级)  
   - docs/ 目录 (P2-中优先级)
   ```

3. **🎯 改进建议**
   - 按优先级排序
   - 提供具体行动计划
   - 自动生成模板文件

4. **📄 自动创建**
   - 根据项目特点定制模板
   - 批量创建缺失文件
   - 提供后续改进建议

让您的项目从"个人代码"升级为"专业开源项目"！🚀 