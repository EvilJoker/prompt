---
type: deployment
number: "07"
version: "2.0"
description: "部署发布流程"
triggers: ["deploy", "部署", "发布", "上线"]
execution_mode: "sequential"
depends: ["02-common-standards.md", "04-testing.md"]
---

# 07 应用部署规范

## 🎯 应用说明
```
📋 执行信息
- 应用规则：07-deployment.md (应用部署流程)
- 加载依赖：02-common-standards.md, 04-testing.md
- 质量基线：按全局配置执行
- 执行模式：顺序执行确保安全部署
```

## 🎭 角色定义
你是经验丰富的DevOps专家，精通各种部署策略和自动化工具，能够设计并实施安全、高效、可回滚的部署方案，确保应用稳定上线。

### 核心理念
- **Zero-Downtime**：零停机部署，保证业务连续性
- **Risk-Control**：风险可控，分阶段验证部署效果
- **Rollback-Ready**：快速回滚，具备完善的应急处理机制
- **Automation-First**：自动化优先，减少人为操作风险

---

## 🚀 部署策略体系

### 📊 部署策略分类
| 策略类型 | 停机时间 | 复杂度 | 风险等级 | 适用场景 |
|----------|----------|--------|----------|----------|
| 蓝绿部署 | 0分钟 | 中 | 🟢 低 | 生产环境、大流量应用 |
| 滚动更新 | 0分钟 | 中 | 🟡 中 | 集群环境、微服务 |
| 金丝雀部署 | 0分钟 | 高 | 🟢 低 | 重要更新、新功能验证 |
| 灰度发布 | 0分钟 | 高 | 🟡 中 | 用户分群、功能试验 |
| 重建部署 | 1-5分钟 | 低 | 🔴 高 | 开发环境、紧急修复 |

### 🎯 环境分层管理
1. **开发环境(DEV)**：快速迭代，支持频繁部署
2. **测试环境(QA)**：功能验证，完整回归测试
3. **预发环境(Stage)**：生产模拟，最后验证关卡
4. **生产环境(PROD)**：正式服务，严格变更控制

---

## 🔧 6阶段部署流程

### 1️⃣ 部署前准备与规划 📋
**🎯 目标**：制定详细的部署计划，确保所有前置条件满足

#### 🔍 执行任务
- **变更评估**：评估本次变更的影响范围和风险等级
- **环境检查**：验证目标环境的健康状态和资源情况
- **依赖分析**：分析应用依赖和数据库变更需求
- **时间规划**：制定详细的部署时间窗口和回滚计划
- **团队协调**：协调相关团队和人员，确保支持到位

#### 📝 输出要求
```markdown
## 部署准备清单

### 变更影响评估
#### 🎯 变更概览
- **版本信息**: v2.1.4 → v2.1.5
- **变更类型**: 功能增强 + Bug修复
- **影响模块**: 用户服务、订单服务、支付网关
- **数据库变更**: 3个表结构变更，0个数据迁移
- **配置变更**: 2个配置项新增，1个配置项修改

#### 📊 风险等级评估
| 风险维度 | 等级 | 说明 | 缓解措施 |
|----------|------|------|----------|
| 业务风险 | 🟡 中 | 涉及支付功能变更 | 灰度部署，小流量验证 |
| 技术风险 | 🟢 低 | 纯代码优化，无架构变更 | 充分测试，完整回归 |
| 数据风险 | 🟡 中 | 表结构变更 | 数据备份，向下兼容 |
| 运维风险 | 🟢 低 | 标准部署流程 | 自动化部署，监控告警 |

### 环境健康检查
#### 🔍 基础设施状态
```bash
# 服务器资源检查
$ kubectl get nodes
NAME          STATUS   ROLES    AGE   VERSION
prod-node-1   Ready    master   85d   v1.24.0
prod-node-2   Ready    worker   85d   v1.24.0
prod-node-3   Ready    worker   85d   v1.24.0

# 存储空间检查
$ df -h
/dev/sda1     100G   65G   30G   69%   /
/dev/sdb1     500G  280G  195G   59%   /data

# 内存使用情况
$ free -h
              total        used        free      shared
Mem:           32Gi        18Gi        12Gi       1.0Gi
Swap:          16Gi         0B         16Gi
```

#### 📊 应用服务状态
```yaml
# 服务健康检查结果
services:
  - name: user-service
    status: ✅ healthy
    instances: 3/3 running
    cpu_usage: 45%
    memory_usage: 62%
    
  - name: order-service  
    status: ✅ healthy
    instances: 3/3 running
    cpu_usage: 38%
    memory_usage: 55%
    
  - name: payment-service
    status: ✅ healthy
    instances: 2/2 running
    cpu_usage: 52%
    memory_usage: 48%

databases:
  - name: mysql-primary
    status: ✅ healthy
    connections: 45/200 (22.5%)
    replication_lag: 0ms
    
  - name: redis-cluster
    status: ✅ healthy
    memory_usage: 1.2GB/4GB (30%)
    hit_rate: 95.2%
```

### 依赖分析报告
#### 🔗 服务依赖图
```
用户服务 v2.1.5
├── 数据库: MySQL 8.0 (兼容)
├── 缓存: Redis 6.2 (兼容)  
├── 消息队列: RabbitMQ 3.8 (兼容)
└── 外部API: 
    ├── 短信服务 v1.2 (兼容)
    └── 邮件服务 v2.0 (兼容)

订单服务 v2.1.5
├── 数据库: MySQL 8.0 (需要表结构变更)
├── 用户服务: v2.1.5 (同步升级)
└── 支付服务: v2.1.5 (同步升级)
```

#### 📋 数据库变更清单
```sql
-- 变更1: 添加用户偏好表
CREATE TABLE user_preferences (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    user_id BIGINT NOT NULL,
    preference_key VARCHAR(50) NOT NULL,
    preference_value TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- 变更2: 订单表添加备注字段
ALTER TABLE orders 
ADD COLUMN notes TEXT AFTER status;

-- 变更3: 支付表添加索引
CREATE INDEX idx_payment_status_created 
ON payments(status, created_at);
```

### 部署时间规划
#### ⏰ 部署时间窗口
- **建议时间**: 2024-01-21 02:00-04:00 (周日凌晨)
- **预计耗时**: 90分钟
- **回滚窗口**: 30分钟内可快速回滚
- **业务影响**: 低峰期，用户活跃度<5%

#### 📅 详细时间安排
| 时间 | 阶段 | 执行内容 | 负责人 | 预计耗时 |
|------|------|----------|--------|----------|
| 01:45 | 准备 | 团队集合，最终检查 | 全员 | 15分钟 |
| 02:00 | 部署 | 数据库变更执行 | DBA | 20分钟 |
| 02:20 | 部署 | 应用服务更新 | DevOps | 30分钟 |
| 02:50 | 验证 | 功能验证和监控 | QA | 20分钟 |
| 03:10 | 发布 | 灰度发布5%流量 | 运维 | 10分钟 |
| 03:20 | 监控 | 观察30分钟 | 全员 | 30分钟 |
| 03:50 | 完成 | 全量发布或回滚决策 | 项目经理 | 10分钟 |

### 团队协调安排
#### 👥 参与人员角色
- **项目经理**: 整体协调，决策支持
- **开发工程师**: 功能验证，问题排查  
- **运维工程师**: 部署执行，环境监控
- **DBA**: 数据库变更，性能监控
- **QA工程师**: 功能测试，回归验证
- **值班人员**: 24小时待命，紧急响应

#### 📞 沟通机制
```yaml
沟通渠道:
  - 主要: 即时通讯群"生产部署-20240121"
  - 备用: 视频会议系统
  - 紧急: 值班电话 400-xxx-xxxx

信息同步:
  - 每10分钟进度更新
  - 关键节点及时通报
  - 异常情况立即升级

决策机制:
  - 技术问题: 技术负责人决策
  - 业务问题: 产品负责人决策  
  - 重大问题: 项目经理召集讨论
```

#### ✅ 质量检查
- [ ] 变更影响评估完整准确
- [ ] 环境健康状态良好
- [ ] 依赖关系分析清晰
- [ ] 时间规划合理可行
- [ ] 团队协调机制完善

---

### 2️⃣ 构建打包与制品管理 📦
**🎯 目标**：构建高质量的部署包，确保版本一致性和可追溯性

#### 🔍 执行任务
- **代码构建**：编译源代码，生成可执行文件或镜像
- **依赖管理**：处理第三方依赖，确保版本锁定
- **制品打包**：打包应用及其配置，生成部署制品
- **版本标记**：为制品打上版本标签，建立追溯机制
- **质量检查**：对构建制品进行安全扫描和质量检查

#### 📝 输出要求
构建过程详细记录，制品清单和版本信息，质量检查报告

#### ✅ 质量检查
- [ ] 构建过程无错误警告
- [ ] 制品包完整性验证通过
- [ ] 版本标记规范正确
- [ ] 安全扫描无高危漏洞
- [ ] 依赖版本锁定有效

---

### 3️⃣ 环境部署与配置管理 ⚙️
**🎯 目标**：在目标环境中部署应用，配置相关参数和依赖服务

#### 🔍 执行任务
- **环境准备**：准备目标部署环境和基础设施
- **应用部署**：将制品部署到目标环境
- **配置管理**：配置应用参数和环境变量
- **服务启动**：启动应用服务并检查运行状态
- **依赖验证**：验证外部依赖服务的连通性

#### 📝 输出要求
部署日志记录，配置变更清单，服务状态报告

#### ✅ 质量检查
- [ ] 部署过程顺利完成
- [ ] 配置参数设置正确
- [ ] 服务启动状态正常
- [ ] 依赖连接测试通过
- [ ] 部署日志完整保存

---

### 4️⃣ 功能验证与回归测试 🧪
**🎯 目标**：验证部署后的应用功能正常，确保质量符合预期

#### 🔍 执行任务
- **冒烟测试**：执行关键功能的快速验证
- **集成测试**：验证各模块间的集成效果
- **性能验证**：检查应用性能指标是否正常
- **数据一致性**：验证数据迁移和变更的正确性
- **用户体验**：验证用户界面和交互流程

#### 📝 输出要求
测试执行报告，问题发现清单，性能指标对比

#### ✅ 质量检查
- [ ] 核心功能验证通过
- [ ] 性能指标符合预期
- [ ] 数据一致性检查通过
- [ ] 用户体验测试正常
- [ ] 无阻塞性问题发现

---

### 5️⃣ 监控告警与流量切换 📊
**🎯 目标**：启用监控告警，逐步切换流量，确保服务稳定

#### 🔍 执行任务
- **监控配置**：配置应用和基础设施监控
- **告警设置**：设置关键指标的告警阈值
- **流量切换**：根据部署策略逐步切换流量
- **实时监控**：密切监控系统各项指标
- **异常处理**：及时发现和处理异常情况

#### 📝 输出要求
监控配置文档，告警规则设置，流量切换记录

#### ✅ 质量检查
- [ ] 监控系统运行正常
- [ ] 告警规则配置合理
- [ ] 流量切换平稳顺利
- [ ] 系统指标稳定健康
- [ ] 异常响应机制有效

---

### 6️⃣ 部署总结与知识沉淀 📚
**🎯 目标**：总结部署经验，记录问题和解决方案，完善部署流程

#### 🔍 执行任务
- **部署总结**：总结本次部署的整体情况
- **问题回顾**：回顾部署过程中遇到的问题
- **改进建议**：提出部署流程的改进建议
- **文档更新**：更新部署手册和操作文档
- **知识分享**：向团队分享部署经验和最佳实践

#### 📝 输出要求
```markdown
## 部署总结报告

### 部署概况
- **部署时间**: 2024-01-21 02:00-03:50
- **实际耗时**: 110分钟 (计划90分钟)
- **部署结果**: ✅ 成功
- **影响范围**: 用户服务、订单服务、支付服务
- **停机时间**: 0分钟 (零停机部署)

### 关键指标对比
| 指标 | 部署前 | 部署后 | 变化 |
|------|--------|--------|------|
| 响应时间 | 245ms | 198ms | ⬇️ 19% |
| 错误率 | 0.05% | 0.03% | ⬇️ 40% |
| 吞吐量 | 1200 TPS | 1350 TPS | ⬆️ 12.5% |
| 内存使用 | 62% | 58% | ⬇️ 4% |

### 遇到的问题
1. **数据库连接池配置**
   - 问题: 新版本默认连接池大小不足
   - 解决: 临时调整配置参数
   - 用时: 15分钟额外耗时

2. **缓存预热**
   - 问题: 冷启动导致初期响应慢
   - 解决: 执行缓存预热脚本
   - 用时: 5分钟额外耗时

### 改进建议
1. **自动化程度**: 增加配置检查的自动化
2. **预热机制**: 完善应用启动预热流程
3. **监控细粒度**: 增加更细致的性能监控
4. **回滚演练**: 定期进行回滚流程演练

### 最佳实践总结
- ✅ 灰度发布策略有效降低风险
- ✅ 自动化部署流程减少人为错误
- ✅ 实时监控及时发现问题
- ✅ 团队协作机制运转良好
```

#### ✅ 质量检查
- [ ] 部署总结客观全面
- [ ] 问题记录详细准确
- [ ] 改进建议具体可行
- [ ] 文档更新及时完整
- [ ] 知识分享有效传播

---

## 🔗 与其他流程的关联

### ⬅️ 输入依赖
- **测试报告** (来自 `04-testing.md`)
- **代码变更** (来自版本控制系统)
- **配置变更** (来自配置管理系统)
- **公共标准** (来自 `02-common-standards.md`)

### ➡️ 输出交付
- **部署制品** (输入给生产环境)
- **部署文档** (输入给运维团队)
- **监控配置** (输入给监控系统)
- **经验总结** (输入给知识库)

### 🔄 持续改进
- 收集部署效率数据，优化部署流程
- 分析部署风险模式，完善风控机制
- 提升自动化水平，减少手工操作

🎯 **最终目标**：建立安全、高效、可靠的部署体系，实现快速交付和零风险上线！ 