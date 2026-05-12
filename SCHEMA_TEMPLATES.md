# Schema 示例库

为不同类型的团队提供现成的 Schema 模板。  
选择最接近你们的，然后定制它。

---

## 示例 1：技术研发团队

适用于：工程团队、后端、基础设施、DevOps

```markdown
# Wiki Schema - 技术研发团队

## Entity 类型

### Core Entities

**Technology**
- 编程语言、框架、库、中间件、云服务
- 属性: 分类、版本、成熟度、学习成本、推荐程度
- 例: React 18, PostgreSQL, Redis, Docker

**Service/System**
- 我们维护的微服务、系统、工具
- 属性: 所有者、技术栈、SLA、关键链路
- 例: API Gateway, Auth Service, Data Pipeline

**Decision**
- 技术决策、架构决策、选型决定
- 属性: 背景问题、候选方案、最终选择、权衡分析、决策人、日期
- 例: "为什么选择 PostgreSQL 而不是 MongoDB"

**Bug/Issue**
- 发现的问题、技术债、坑点
- 属性: 严重程度(critical/high/medium/low)、根本原因、修复方案、预防方法
- 例: "Redis 连接泄漏导致的内存溢出"

**Pattern**
- 最佳实践、设计模式、工作流、代码约定
- 属性: 适用场景、步骤、反例、性能影响
- 例: "异步任务队列的设计", "错误处理规范"

**Person**
- 团队成员
- 属性: 角色、擅长领域(技术栈)、项目所有权、导师/学徒关系
- 例: "Alice - Backend Engineer, 擅长 Python/PostgreSQL"

**Project**
- 项目、特性、新增功能
- 属性: 所有者、时间线、技术栈、依赖关系、上线状态
- 例: "支付系统重构", "实时通知功能"

## 关键关系

- `uses`: Service A 使用 Technology B / Service C
- `depends_on`: Service A 依赖 Service B（重要！用于影响分析）
- `caused`: Bug X 由 Technology Y 的问题引起
- `fixes`: Solution A 修复了 Bug B
- `supersedes`: Decision A 替代了 Decision B（技术升级时关键）
- `implements`: Technology A 实现了 Pattern B
- `owns`: Person X 拥有/负责 Service Y

## Ingest 时的要点

### 场景 A：技术决策文档
```
Decision: "选择 PostgreSQL 还是 MongoDB"
→ 创建 Decision 页面: PostgreSQL vs MongoDB
→ 关联两个 Technology 页面
→ 如果之前有相反的决策，标记 supersedes
→ 列出关键权衡
```

### 场景 B：Bug 报告
```
Bug: "线上内存溢出，Redis 连接泄漏"
→ 创建 Bug 页面
→ 指向 Technology: Redis
→ 指向 Service: 涉及的服务
→ 关联 Pattern: 连接池最佳实践
→ 添加 fixes 关系到修复方案
```

### 场景 C：架构设计文档
```
新微服务设计
→ 创建 Service 页面
→ 列出 uses 关系：用到的 Technology
→ 列出 depends_on 关系：依赖的其他 Service
→ 关联 Decision：为什么选这个技术栈
→ 关联 Person：所有者和主要贡献者
```

## 页面模板

### Technology 页面
```markdown
---
entity_type: Technology
category: database / framework / language / library
maturity: mature / stable / beta / experimental
confidence: high / medium / low
last_updated: 2026-01-15
sources: [doc1, decision2, project3]
---

# PostgreSQL

## 概述
开源关系型数据库，强一致性，ACID 保证。

## 为什么选择它
- 强一致性，适合金融/支付场景
- 丰富的数据类型（JSON、数组等）
- 活跃的社区和良好的文档

## 版本和支持
- 生产环境: 15.x
- 升级计划: 每年升一个大版本

## 常见坑点
- [[连接池泄漏问题]]
- [[大表全表扫描性能下降]]

## 对比
vs MongoDB: [[PostgreSQL vs MongoDB]] (2024年决策)
vs MySQL: [[为什么不用 MySQL]]

## 相关决策
[[选择 PostgreSQL 的决定]]

## 相关服务
[[API Service]] uses PostgreSQL
[[Data Pipeline]] uses PostgreSQL

```

### Decision 页面
```markdown
---
entity_type: Decision
decision_date: 2024-06
decision_maker: Tech Lead + Team
status: active / archived / revisit_in_2025
confidence: high
sources: [benchmark, production_experience, RFC]
---

# 为什么选择 PostgreSQL 而不是 MongoDB

## 问题背景
需要为支付系统选择数据库。

### 约束
- 强一致性必须（金融交易）
- 10K+ QPS
- 数据量 TB 级别

### 候选方案
1. PostgreSQL（传统关系型）
2. MongoDB（NoSQL，灵活模式）
3. CockroachDB（分布式 SQL）

## 对比分析

| 维度 | PostgreSQL | MongoDB | CockroachDB |
|------|-----------|---------|------------|
| 一致性 | 强 ACID ✅ | 最终一致 ❌ | 强 ACID ✅ |
| 模式灵活性 | 低 ❌ | 高 ✅ | 低 ❌ |
| 运维成本 | 中 | 高 | 高 |
| 成本 | 低 | 中 | 高 |

## 最终决策
**选择 PostgreSQL**

### 理由
1. 金融场景必须强一致性，MongoDB 不适合
2. 数据模式相对稳定，不需要 MongoDB 的灵活性
3. PostgreSQL 运维成本更低
4. 团队对 PostgreSQL 更熟悉

### 权衡
- 失去：方便的嵌入式文档存储
- 获得：可靠性和成本

## 后续追踪
- [ ] 2024-12 月：性能基准测试（目标 10K+ QPS）
- [ ] 2025-06 月：重新评估是否需要 Sharding

## 相关页面
[[PostgreSQL]] uses
[[MongoDB]] (not chosen)
[[CockroachDB]] (not chosen)
[[支付系统架构]]

## 如果要推翻这个决策
需要满足以下至少一个条件：
1. PostgreSQL 无法达到 50K+ QPS
2. 数据模式频繁变化，强一致性需求下降
3. 引入新的关键需求（如地理分布）
```

### Bug 页面
```markdown
---
entity_type: Bug
severity: critical
status: fixed / monitoring / open
root_cause_identified: true
confidence: high
last_updated: 2026-01-10
---

# Redis 连接泄漏导致的内存溢出

## 症状
- 线上服务每 2-3 天出现 OOM
- Redis 连接数不断增长，最终达到限制

## 根本原因
在错误处理时，[[Redis 连接池]] 的连接没有正确关闭。

```python
# ❌ 错误代码
try:
    conn = redis.get_connection()
    result = conn.get(key)
except Exception:
    # 问题：异常时没有 close
    pass
```

## 修复方案
```python
# ✅ 正确代码
try:
    conn = redis.get_connection()
    result = conn.get(key)
finally:
    conn.close()  # 确保总是关闭
```

## 预防措施
- [[连接管理规范]] - 所有连接操作必须用 with 语句
- [[Code Review Checklist]] - 检查是否遗漏资源释放
- [[性能监控规范]] - 监控连接数和内存使用

## 相关技术
[[Redis]]
[[连接池最佳实践]]

## 影响分析
这个 bug 影响的服务：
[[API Service]]
[[User Service]]
[[Order Service]]

## 时间线
- 2026-01-01: 首次发现
- 2026-01-03: 根本原因确认
- 2026-01-05: 修复上线
- 2026-01-10: 监控确认无异常
```

---

## 示例 2：产品团队

适用于：产品经理、设计、运营、增长

```markdown
# Wiki Schema - 产品团队

## Entity 类型

**Feature**
- 产品特性、功能模块
- 属性: 所有者(PM)、状态(planning/building/launched/retired)、用户价值、成功指标

**User Segment**
- 用户细分、用户personas
- 属性: 规模、主要诉求、行为特征、LTV

**Design Decision**
- UI/UX 决策
- 属性: 背景问题、候选方案、最终选择、A/B 测试结果

**Experiment**
- A/B 测试、实验
- 属性: 假设、结果、影响、学习

**Learning**
- 用户研究发现、市场洞察
- 属性: 来源(用户访谈/问卷/行为数据)、关键发现、应用

**Metric**
- 关键指标、KPI
- 属性: 定义、目标、当前值、趋势

**Competitor**
- 竞争对手、市场情报
- 属性: 产品定位、优势、劣势

## 关键关系

- `solves`: Feature A 解决 User Segment B 的需求
- `measures`: Metric X 衡量 Feature Y 的成功
- `validates`: Learning A 验证/推翻了假设 B
- `inspired_by`: Design C 受到 Competitor D 的启发
- `conflicts_with`: Feature A 和 Feature B 的目标有冲突

---

## 示例 3：运维/SRE 团队

适用于：基础设施、DevOps、SRE

```markdown
# Wiki Schema - 运维团队

## Entity 类型

**Incident**
- 线上故障、紧急事件
- 属性: 严重程度、持续时间、影响范围、根本原因、事后分析、预防措施

**System/Component**
- 基础设施组件、监控、告警系统
- 属性: 可用性 SLA、所有者、依赖关系、容量、瓶颈

**Runbook**
- 应急预案、标准操作流程
- 属性: 适用场景、步骤、回滚方案、联系人

**Capacity Plan**
- 容量规划、扩展计划
- 属性: 当前容量、增长率、预期扩展时间、成本

## 关键关系

- `caused_by`: Incident A 由 System B 的问题引起
- `mitigated_by`: Incident A 可以用 Runbook B 处理
- `monitors`: Component A 监控 System B

---

## 示例 4：数据/分析团队

适用于：数据科学家、分析、BI

```markdown
# Wiki Schema - 数据团队

## Entity 类型

**Dataset**
- 数据表、数据源、数据湖中的资产
- 属性: 更新频率、数据量、关键字段、质量、PII 风险

**Metric Definition**
- 关键指标的定义和计算方法
- 属性: 计算公式、ETL 流程、所有者、用途

**Analysis**
- 数据分析报告
- 属性: 问题、数据源、结论、限制条件

**Data Quality Issue**
- 数据质量问题
- 属性: 影响范围、根本原因、修复方案

## 关键关系

- `sources_from`: Metric A 基于 Dataset B
- `validated_by`: Analysis A 验证了 Learning B
```

---

## 如何选择和定制

1. **选择最接近的模板**
   - 技术团队 → 示例 1
   - 产品团队 → 示例 2
   - 混合团队 → 合并多个示例

2. **添加你们特定的 Entity 类型**
   - 你们最常讨论的东西是什么？
   - 那就应该是一个 Entity 类型

3. **简化关键关系**
   - 不需要用上所有的关系类型
   - 选择最能表达你们知识结构的 3-5 种

4. **试运行和迭代**
   - 前两周不要改太多，先用起来
   - 看看实际使用中缺少什么
   - 然后逐步完善

