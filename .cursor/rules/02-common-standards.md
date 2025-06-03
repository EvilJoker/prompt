---
type: common-standards
version: "1.0"
description: "统一的公共标准和基础规范"
alwaysApply: true
---

# 📐 公共标准规范

## 🎯 核心理念
- **Quality-First**：质量优先原则
- **Consistency-Driven**：一致性驱动
- **User-Centric**：用户中心思维
- **Maintainable-Scalable**：可维护可扩展

---

## 📊 统一质量基线

### 🔍 代码质量标准
- **测试覆盖率**：≥ 90%（核心模块 ≥ 95%）
- **圈复杂度**：≤ 10（建议 ≤ 7）
- **代码重复率**：≤ 3%
- **技术债务比例**：≤ 5%
- **代码审查通过率**：100%

### ⚡ 性能质量标准
- **页面加载时间**：≤ 2秒（首屏 ≤ 1秒）
- **API响应时间**：≤ 500ms（核心接口 ≤ 200ms）
- **并发用户数**：≥ 1000（峰值 ≥ 5000）
- **系统可用性**：≥ 99.9%
- **错误率**：≤ 0.1%

### 🔒 安全质量标准
- **身份认证**：多因子认证（MFA）
- **数据加密**：传输（TLS 1.3）+ 存储（AES-256）
- **权限控制**：RBAC + 最小权限原则
- **安全审计**：100%关键操作有日志
- **漏洞修复**：高危漏洞 24小时内修复

### 📋 文档质量标准
- **API文档覆盖率**：100%
- **代码注释覆盖率**：≥ 80%（复杂逻辑 100%）
- **设计文档完整性**：核心功能 100%
- **用户手册可用性**：≥ 95%用户满意度
- **文档时效性**：与代码同步更新

---

## 🏗️ 架构设计原则

### SOLID原则
- **S**ingle Responsibility：单一职责
- **O**pen/Closed：开闭原则
- **L**iskov Substitution：里氏替换
- **I**nterface Segregation：接口隔离
- **D**ependency Inversion：依赖倒置

### 设计模式应用
- **创建型**：工厂模式、单例模式、建造者模式
- **结构型**：适配器模式、装饰者模式、外观模式
- **行为型**：观察者模式、策略模式、命令模式

### 系统架构规范
- **分层架构**：表现层 → 业务层 → 数据层
- **模块化设计**：高内聚、低耦合
- **接口规范**：RESTful API + OpenAPI规范
- **数据一致性**：ACID特性保证

---

## 🎨 编码规范标准

### 命名规范
```typescript
// 变量和函数：camelCase
const userName = 'john';
function getUserInfo() { }

// 类和接口：PascalCase
class UserService { }
interface UserProfile { }

// 常量：SCREAMING_SNAKE_CASE
const MAX_RETRY_COUNT = 3;

// 文件名：kebab-case
user-service.ts, user-profile.interface.ts
```

### 注释规范
```typescript
/**
 * 用户信息服务类
 * 提供用户CRUD操作和权限验证
 * 
 * @author 开发者姓名
 * @version 1.0.0
 * @since 2024-01-01
 */
class UserService {
    /**
     * 获取用户信息
     * 
     * @param userId - 用户ID
     * @param includeProfile - 是否包含详细信息
     * @returns Promise<UserInfo> 用户信息对象
     * @throws {UserNotFoundError} 用户不存在时抛出
     */
    async getUserInfo(userId: string, includeProfile = false): Promise<UserInfo> {
        // 实现逻辑...
    }
}
```

### 错误处理规范
```typescript
// 统一错误类型定义
class BusinessError extends Error {
    constructor(
        public code: string,
        public message: string,
        public details?: any
    ) {
        super(message);
        this.name = 'BusinessError';
    }
}

// 统一错误处理
try {
    const result = await riskyOperation();
    return result;
} catch (error) {
    logger.error('操作失败', { error, context });
    throw new BusinessError('OPERATION_FAILED', '操作失败', error);
}
```

---

## 🧪 测试标准规范

### 测试分层策略
```
测试金字塔
├── E2E测试 (10%)          # 端到端业务流程测试
├── 集成测试 (20%)         # 模块间接口测试
└── 单元测试 (70%)         # 函数级逻辑测试
```

### 测试用例设计
- **正常流程**：标准输入的预期输出
- **边界条件**：临界值和极值测试
- **异常情况**：错误输入和异常处理
- **性能测试**：响应时间和并发测试

### 测试命名规范
```typescript
describe('UserService', () => {
    describe('getUserInfo', () => {
        it('should return user info when valid userId provided', async () => {
            // 测试正常情况
        });
        
        it('should throw UserNotFoundError when userId not exists', async () => {
            // 测试异常情况
        });
        
        it('should return user info with profile when includeProfile is true', async () => {
            // 测试边界条件
        });
    });
});
```

---

## 📝 文档标准模板

### 功能设计文档模板
```markdown
# [功能名称] 设计文档

## 1. 需求概述
- **业务背景**：[业务场景描述]
- **用户故事**：作为[角色]，我希望[功能]，以便[价值]
- **验收标准**：[可量化的成功标准]

## 2. 设计方案
- **架构设计**：[系统架构图和说明]
- **接口设计**：[API接口规范]
- **数据模型**：[数据结构定义]

## 3. 实现细节
- **核心流程**：[主要业务流程]
- **关键算法**：[核心算法说明]
- **异常处理**：[错误处理策略]

## 4. 测试方案
- **测试策略**：[测试方法和覆盖范围]
- **测试用例**：[主要测试场景]
- **验收标准**：[质量验收要求]
```

### API文档模板
```yaml
# OpenAPI 3.0 规范
openapi: 3.0.0
info:
  title: [API名称]
  version: 1.0.0
  description: [API功能描述]

paths:
  /users/{userId}:
    get:
      summary: 获取用户信息
      parameters:
        - name: userId
          in: path
          required: true
          schema:
            type: string
          description: 用户ID
      responses:
        '200':
          description: 成功返回用户信息
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/UserInfo'
        '404':
          description: 用户不存在
```

---

## 🔄 版本控制规范

### Git工作流
```
主分支策略：
├── main/master        # 生产发布分支
├── develop           # 开发集成分支
├── feature/*         # 功能开发分支
├── hotfix/*          # 紧急修复分支
└── release/*         # 发布准备分支
```

### 提交信息规范
```
<type>(<scope>): <subject>

<body>

<footer>
```

**提交类型**：
- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档更新
- `style`: 代码格式调整
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建工具或依赖更新

**示例**：
```
feat(user): add user profile editing functionality

- Add user profile form component
- Implement profile update API
- Add validation for profile fields

Closes #123
```

---

## 🚀 部署发布规范

### 环境管理
- **开发环境**：开发和调试
- **测试环境**：功能测试和集成测试
- **预发布环境**：生产前的最终验证
- **生产环境**：正式服务环境

### 发布流程
1. **代码审查**：通过Code Review
2. **自动化测试**：通过所有测试用例
3. **安全扫描**：通过安全漏洞检测
4. **性能测试**：达到性能指标要求
5. **灰度发布**：小范围验证功能
6. **全量发布**：正式发布到生产环境

### 监控告警
- **系统监控**：CPU、内存、磁盘、网络
- **应用监控**：错误率、响应时间、吞吐量
- **业务监控**：关键业务指标和用户行为
- **日志监控**：错误日志和异常追踪

---

## 🛡️ 质量检查清单

### 开发阶段检查点
- [ ] 代码符合编码规范
- [ ] 函数复杂度符合标准
- [ ] 单元测试覆盖率达标
- [ ] 代码注释完整准确
- [ ] 没有安全漏洞风险

### 发布前检查点
- [ ] 功能完整实现需求
- [ ] 所有测试用例通过
- [ ] 性能指标达到要求
- [ ] 安全扫描无高危问题
- [ ] 文档更新完整同步

### 生产监控检查点
- [ ] 系统运行稳定
- [ ] 业务指标正常
- [ ] 用户反馈良好
- [ ] 错误率在可接受范围
- [ ] 性能指标符合预期

🎯 **目标**：通过统一标准，确保高质量的一致性输出！ 