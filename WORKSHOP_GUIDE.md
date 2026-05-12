# 第二大脑实操 Workshop 指南

## 目的
在 30 分钟内，一个小团队可以：
1. 理解你们团队的知识是什么
2. 设计一个简单的 Schema（操作规则）
3. 用 Claude 初始化第一个 Wiki
4. 尝试查询和维护

---

## Phase 0：准备（5 分钟）

### 建立项目结构
```bash
mkdir team-wiki && cd team-wiki
git init

# 创建必要目录
mkdir sources      # 原始文档
mkdir wiki         # Wiki 页面（LLM 维护）

# 创建核心文件
touch CLAUDE.md    # Schema 和操作规则
touch index.md     # Wiki 目录
touch log.md       # 操作日志
```

### 准备工作材料
收集 3-5 份你们团队现有的文档/记录：
- 技术决策记录（ADR）
- 项目总结
- Bug 修复报告
- 架构文档
- 任何 Slack 讨论整理

放到 `sources/` 目录里。

---

## Phase 1：定义 Schema（10 分钟）

这是最关键的部分。**你定义的好坏，直接影响 wiki 的质量。**

### 第一步：识别 Entity 类型

**问题**：你们团队的知识里，最重要的"东西"有哪些？

**示例**（技术团队）：
```
Person        - 团队成员、决策者
Project       - 项目、产品线
Technology    - 编程语言、框架、库
Decision      - 架构决策、技术选型
Bug/Issue     - 发现的问题、坑点
Pattern       - 最佳实践、工作流
```

**示例**（产品团队）：
```
User Segment  - 目标用户群
Feature       - 产品特性
Design        - UI/UX 决策
Metric        - 关键指标
Experiment    - A/B 测试
Learning      - 用户研究发现
```

### 第二步：定义关键关系

**问题**：这些 Entity 之间的关系是什么？

**常见关系**：
```
uses          - A 使用 B
depends_on    - A 依赖 B
contradicts   - A 和 B 矛盾
caused        - A 导致了 B
fixes         - A 修复了 B
supersedes    - A 替代了 B（新的比旧的更好）
relates_to    - A 和 B 有关
```

### 第三步：写 CLAUDE.md

这是你给 Claude 的"工作手册"。看[下面的模板](#claude-schema-模板)。

---

## Phase 2：初始化 Wiki（15 分钟）

### 第一步：准备工作

在 Obsidian 或你选择的编辑器里打开这个文件夹。

### 第二步：给 Claude 下命令

打开 Claude Code，给它这个提示：

```markdown
我要你帮我维护一个团队知识库（Wiki）。

这是我的操作规则和 schema：
[粘贴你的 CLAUDE.md]

现在，请读这份文档，按照上面的规则，为它生成 wiki 页面。

操作步骤：
1. 读文档，找关键信息
2. 创建或更新相关的 wiki 页面
3. 在 wiki/entities.md 中记录所有提到的 entity
4. 在 wiki/relationships.md 中记录所有关系
5. 在 index.md 中添加或更新这些页面的链接
6. 在 log.md 的最后添加一条操作记录

记住：
- 保持页面简洁（每页 100-300 字）
- 每个页面开头用 YAML frontmatter 标记 entity 类型
- 使用 [[wikilink]] 连接相关页面
- 当新信息和旧信息矛盾时，用"Superseded by"标记

开始吧！
```

### 第三步：重复 ingest

对你的 3-5 份文档依次重复，一份一份处理：

```markdown
请 ingest 这份文档：[粘贴文档或上传]

保持现有的 wiki 结构，更新相关页面。
```

### 看到的结果
- `wiki/` 目录下应该有 10-30 个页面
- `index.md` 是一个目录，列出所有页面
- `log.md` 记录了 ingest 的历史

---

## Phase 3：尝试查询（10 分钟）

### 查询 1：简单的关键词查询
```markdown
wiki 里有关于 [某技术] 的信息吗？总结一下。
```

### 查询 2：对比查询
```markdown
[方案 A] 和 [方案 B] 的区别是什么？
基于 wiki 的信息，哪个更好？为什么？
```

### 查询 3：关系查询
```markdown
[项目 X] 依赖哪些技术？这些技术有什么风险？
```

### 查询 4：历史查询
```markdown
我们在 [问题] 上的认识是怎样演进的？
现在的最佳实践是什么？
```

---

## 收获与反思（5 分钟）

问你的团队：

1. **Wiki 有多完整？**
   - 它回答了多少你想问的问题？
   - 缺失了哪些关键信息？

2. **Schema 是否适合你们？**
   - Entity 类型够用吗？
   - 需要添加或移除什么关系？

3. **下一步是什么？**
   - 继续 ingest 更多文档
   - 改进 Schema 的定义
   - 自动化定期的 lint 检查

---

## CLAUDE Schema 模板

把这个保存为 `CLAUDE.md`，根据你的需求修改。

```markdown
# Wiki 操作规则 (Schema)

## Entity 类型

### 技术相关
- **Technology**: 编程语言、框架、库、工具
  - 属性: 类型(语言/框架/库)、版本、用途、推荐指数
  
- **Decision**: 技术决策、架构选型
  - 属性: 决策人、决策时间、背景、选择、权衡

- **Project**: 项目、产品线、服务
  - 属性: 所有者、技术栈、状态、关键指标

### 人相关
- **Person**: 团队成员
  - 属性: 角色、擅长领域、经验
  
- **Team**: 团队
  - 属性: 成员列表、目标、文化

### 知识相关
- **Pattern**: 最佳实践、设计模式、工作流
  - 属性: 适用场景、步骤、风险
  
- **Bug/Issue**: 问题、坑点
  - 属性: 严重程度、原因、解决方案、预防措施

- **Learning**: 学习收获、经验教训
  - 属性: 来源、关键点、应用场景

## 关键关系

- `uses`: A 使用或依赖 B
- `contradicts`: A 和 B 有冲突或不同意见
- `caused`: A 导致了 B
- `fixes`: A 解决了 B
- `supersedes`: A 替代或更新了 B（新的更好）
- `part_of`: A 是 B 的一部分
- `related_to`: A 和 B 相关

## 页面格式

每个 wiki 页面开头添加 YAML frontmatter：

```yaml
---
entity_type: Technology
tags: [framework, frontend, recommended]
confidence: high
last_updated: 2026-01-15
sources:
  - Project A
  - Project B
---

# 页面标题

简介（100 字以内）

## 核心特性
- 特性 1
- 特性 2

## 使用场景
...

## 权衡与选择
...

## 相关页面
[[related-page-1]] [[related-page-2]]
```

## Ingest 流程

1. **读源文件** - 理解核心内容
2. **提取 entities** - 识别所有重要的概念/人/技术/决策
3. **映射关系** - 这些 entities 之间如何相关
4. **创建或更新页面**
   - 如果已有相关页面，更新它（添加新信息、更新日期）
   - 如果没有，创建新页面
5. **更新交叉引用** - 确保相关页面都有相互链接
6. **发现矛盾** - 新信息是否与现有知识矛盾？如果是，标记为 "Potentially supersedes"
7. **更新索引** - index.md 中添加或更新页面列表
8. **记录操作** - log.md 中添加一条记录

格式：
```
## [YYYY-MM-DD] ingest | 文档标题
- 新增页面: [page1], [page2]
- 更新页面: [page3], [page4]
- 发现矛盾: [page5] vs [page6]
- 关键发现: [3-5 行总结]
```

## Lint 检查清单

定期（每周或每月）检查：

- [ ] 孤立页面（没有反向链接）- 需要连接
- [ ] 过时声明（6 个月以上没更新）- 需要验证
- [ ] 死链（指向不存在的页面）- 需要修复
- [ ] 矛盾声明（多个页面说不同的话）- 需要调和
- [ ] 重复页面（同一个东西有多个页面）- 需要合并
- [ ] 关键概念缺失（经常被提到但没有专门页面）- 需要创建

## 查询策略

用户提问时，Claude 应该：

1. 在 wiki 中搜索相关页面（关键词、entity、关系）
2. 如果找到，返回相关页面的摘要和链接
3. 如果没找到，告诉用户 wiki 中缺乏这个信息
4. 可选：提议创建新页面来填补空白

## 保留策略

- 所有页面永久保留（不删除）
- 过时的页面标记为 "Archived" 或 "Superseded By"
- 保留修改历史（git）
```

---

## 常见问题

**Q: Schema 一开始就要完美吗？**  
A: 不用。第一版粗糙没关系，用几周后你就知道需要调整什么。

**Q: 用什么工具编辑 Wiki？**  
A: 任何能编辑 Markdown 的都行。推荐 Obsidian（有图表、反向链接）。

**Q: 需要手工维护吗？**  
A: 最初需要。但随着时间，可以配置 Claude 自动处理大部分任务。

**Q: 怎样防止 Wiki 积累错误？**  
A: 定期 lint 检查、人工审核关键决策、保持 schema 约束。

**Q: 多个人编辑怎样同步？**  
A: 用 Git。每次 ingest 一个 commit。冲突解决遵循"最新来源优先"原则。

---

## 下一步

1. **完成初始化**（第一周）
   - 把现有文档都 ingest 到 wiki
   - 调整 schema 至稳定状态
   
2. **建立工作流**（第二周）
   - 每次有新的项目/决策，自动更新 wiki
   - 定期（每周）做 lint 检查
   
3. **升级到 v2 功能**（第三周+）
   - 添加 confidence scoring（评分）
   - 实现自动的矛盾检测
   - 多团队间的 wiki 同步
   
4. **测量价值**（持续）
   - 新人上手快了吗？
   - 解决问题的时间减少了吗？
   - 重复工作消除了吗？

