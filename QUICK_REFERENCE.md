# 快速参考卡：第二大脑实操指南

## 30 秒理解核心概念

| 概念 | 解释 |
|------|------|
| **Raw Sources** | 你的原始文档（不改动） |
| **Wiki** | LLM 生成的知识库（Markdown） |
| **Schema** | 操作规则（告诉 LLM 怎样维护 wiki） |
| **Ingest** | 导入新文档 |
| **Query** | 查询 wiki（不查原文件） |
| **Lint** | 定期检查健康状况 |

---

## 🚀 5 分钟快速启动

```bash
# 1. 创建文件夹
mkdir my-team-wiki && cd my-team-wiki && git init

# 2. 初始化目录
mkdir sources wiki
touch CLAUDE.md index.md log.md

# 3. 把你的文档放进 sources/
cp /path/to/your/docs sources/

# 4. 写 CLAUDE.md（参考 SCHEMA_TEMPLATES.md）

# 5. 打开 Claude Code，运行 workshop
```

---

## 📝 Claude 提示词速查

### Ingest 新文档
```markdown
我的 wiki schema：
[粘贴你的 CLAUDE.md]

请读这份文档，按规则整合到 wiki 里：
[粘贴或上传文档]

生成/更新相关页面。
```

### 查询 Wiki
```markdown
根据 wiki 信息，[你的问题]？

如果 wiki 中找不到答案，告诉我缺少什么。
```

### 执行 Lint 检查
```markdown
请对 wiki 做一次完整的 lint 检查：

检查清单：
- [ ] 孤立页面（没有反向链接）
- [ ] 6 个月未更新的页面
- [ ] 重复的 entity
- [ ] 死链
- [ ] 矛盾的声明

报告所有问题和修复建议。
```

### 生成可视化
```markdown
根据 wiki 数据，生成：
1. 技术栈关系图（用 Markdown 或 ASCII）
2. 项目依赖矩阵
3. 团队知识地图
```

---

## 📊 Wiki 文件结构一览

```
my-team-wiki/
├── CLAUDE.md              # 你的 Schema（最重要！）
├── sources/               # 原始文档（不改）
│   ├── doc1.md
│   ├── doc2.pdf
│   └── ...
├── wiki/                  # LLM 生成的页面
│   ├── entities/          # Entity 页面
│   │   ├── Technology.md
│   │   ├── Decision.md
│   │   └── ...
│   ├── relationships.md   # 关系总览
│   └── ...
├── index.md               # Wiki 目录（目录树）
├── log.md                 # 操作日志
├── .gitignore
└── .git/                  # 版本控制
```

---

## ✅ 关键检查清单

### 第一周
- [ ] 定义了 Entity 类型（3-5 个）
- [ ] 定义了关键关系（3-5 种）
- [ ] 写好了 CLAUDE.md
- [ ] Ingest 了 3-5 份现有文档
- [ ] Wiki 有 10+ 个页面
- [ ] index.md 是最新的

### 第二周
- [ ] 尝试了查询（成功率 >70%）
- [ ] 发现了缺失的页面并补充
- [ ] 修正了 Schema 中的问题
- [ ] 做了第一次 lint 检查

### 第三周+
- [ ] 每个新决策都自动 ingest 到 wiki
- [ ] 定期（周 1 次或月 1 次）lint
- [ ] 尝试了 Confidence Scoring 或 Graph Analysis
- [ ] 团队成员开始主动查询 wiki

---

## 🎯 成功指标

你会知道 wiki 有用，当：

1. **新人上手快** - 入职不用问 10 遍同样的问题
2. **问题有答案** - "我们之前怎样做的？" → wiki 给出答案
3. **知识不流失** - 某人离职了，知识留了下来
4. **决策有记录** - "为什么选这个技术？" → wiki 有历史
5. **工作有复利** - 你的分析、学习今后还被引用

---

## ⚠️ 常见陷阱和解决方案

| 陷阱 | 症状 | 解决方案 |
|------|------|--------|
| **Schema 太复杂** | Entity 类型 >10 个，关系 >15 种 | 删减到核心 3-5 个 |
| **Wiki 不同步** | 页面信息矛盾 | 加强 Lint 检查 |
| **页面太长** | 单个页面 >1000 字 | 拆分成多个小页面 |
| **人工维护** | "谁来维护 wiki？" | 自动化 Ingest，Lint 变成日常 |
| **信息太旧** | 6 个月没更新 | 定期 Lint，标记 outdated |
| **无人用** | Wiki 建好了但没人查 | 在日常工作中推广（Slack 分享、周会提及） |

---

## 💡 进阶技巧

### 1. Entity 的命名约定
```markdown
技术:    [小写]-[小写]  → postgresql, react-18, docker
项目:    [大写][大写]   → ProjectA, DataPipeline
人:      [名字]         → Alice, Bob
决策:    [谓宾式]       → 为什么选PostgreSQL, Redis缓存策略
```

### 2. 关系的方向
- 总是用有向图的思路（A → B）
- `uses`, `depends_on` 表示依赖方向
- `supersedes` 表示替代（新 → 旧）

### 3. Confidence 的简单方法
```markdown
✅ High: 经过 3+ 个项目验证，最近 1 月确认
⚠️ Medium: 1-2 个项目用过，3 个月内有验证
❓ Low: 理论上有效，还未大规模验证
```

### 4. 自动化 Lint 的频率
- 小团队（<10 人）：月 1 次
- 中等团队（10-50 人）：周 1 次
- 大团队（>50 人）：日 1 次

### 5. Git Commit Message 约定
```
ingest: 技术文档整合 - React 最佳实践
lint: 删除孤立页面，修复 3 个死链
query: 新增分析报告 - 2024 技术栈对比
supersede: Decision-PostgreSQL 替代 Decision-MongoDB
```

---

## 📚 参考资源

| 资源 | 链接 | 用途 |
|------|------|------|
| 核心论文 | [Karpathy LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) | 理解核心理念 |
| 进阶版本 | [LLM Wiki v2](https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2) | 学习生命周期管理 |
| Obsidian 教程 | [官方文档](https://help.obsidian.md/) | Wiki 编辑工具 |
| Claude Code | [Anthropic Docs](https://docs.claude.ai/) | 操作 wiki |

---

## 🎓 学习路径

### 周 1：基础
- [ ] 读 Karpathy LLM Wiki 原文
- [ ] 完成 Workshop
- [ ] 初始化 wiki，导入 3-5 份文档

### 周 2：实践
- [ ] 日常查询 wiki
- [ ] 第一次 lint 检查
- [ ] 邀请团队成员试用

### 周 3：优化
- [ ] 读 LLM Wiki v2
- [ ] 实验 Confidence Scoring
- [ ] 设计自动化流程

### 月 2+：运营
- [ ] 建立定期 lint 习惯
- [ ] 测量 wiki 的业务价值
- [ ] 不断迭代 schema

---

## 🤝 建议讨论议题

分享完后，和团队讨论：

1. **我们最想自动化什么？**
   - 决策记录、问题追踪、技术文档...

2. **谁会是 Wiki 的"所有者"？**
   - 通常是一个人初期维护，逐步分散责任

3. **第一批导入什么内容？**
   - 关键决策、架构文档、常见问题...

4. **多久 Lint 一次？**
   - 小团队从月 1 次开始

5. **怎样在日常中推广？**
   - Slack 提醒、周会提及、新人任务...

---

## 📞 获得帮助

遇到问题？

1. **Wiki 更新不对** → 检查 schema 定义，可能 Entity 类型不匹配
2. **查询找不到答案** → 运行 lint 检查，可能页面不存在或名字错了
3. **团队不用** → 从关键问题开始演示价值（"这个 bug 之前怎样处理的？"）
4. **不知道怎样继续** → 参考 LLM Wiki v2 中的"Implementation Spectrum"

---

## 最后的话

> "The cost of maintaining knowledge is near zero when LLMs do it.  
> Your job is to curate sources, ask good questions, and think about what it all means."
>
> — Andrej Karpathy

开始吧。从小处开始，逐步演进。  
你的第二大脑会慢慢长大。

