# 第二大脑进化论：完整分享包

> 赋能个体，沉淀集体，构建团队的"复利型"记忆  
> 基于 Andrej Karpathy LLM Wiki 和 Rohit G00 LLM Wiki v2

这是一套完整的演讲资料、工作坊指南和实操工具包，帮助你的团队构建一个由 AI 驱动的、永不遗忘的知识库系统。

---

## 📂 核心文件

| 文件 | 用途 | 字数 |
|------|------|------|
| **slides.md** | Slidev 演讲 PPT（60 分钟） | 完整大纲 |
| **WORKSHOP_GUIDE.md** | 30 分钟实操指南 | 完整教程 |
| **SCHEMA_TEMPLATES.md** | 4 种行业 Schema 模板 | 开箱即用 |
| **QUICK_REFERENCE.md** | 快速参考卡 | 速查表 |

---

## 🚀 快速启动

### 启动演讲
```bash
pnpm install
pnpm run dev
# 访问 http://localhost:3030
```

### 启动 Workshop（演讲后）
1. 发给参会者本文件夹的全部内容
2. 他们打开 `WORKSHOP_GUIDE.md`
3. 遵循 4 个 Phase，30 分钟完成初始化

---

## 💡 核心概念速览

### 问题
- 💼 项目知识重复发现
- 📚 Slack 讨论随时消失
- 👥 人员离职，知识跟着走
- ⏰ 每次都重新检索和整理

### 解决方案
```
原始文档 → [LLM] → Wiki（编译的知识）
              ↓
           Schema（操作规则）
```

**核心优势**：
- ✅ 知识有生命周期（不是平的）
- ✅ 知识自动维护（人专注思考）
- ✅ 知识结构化（知识图谱）
- ✅ 知识复利增长（团队智慧）

---

## 📊 分享推荐流程

### 第一阶段：演讲（1 小时）
- 用 Slidev 展示 `slides.md`（60 分钟）
- 讲解 Karpathy 模式、LLM Wiki v2、实际案例

### 第二阶段：Workshop（30 分钟，立即跟进）
- Phase 0：准备（5 分钟）
- Phase 1：定义 Schema（10 分钟）
- Phase 2：初始化 Wiki（15 分钟）
- 使用 `QUICK_REFERENCE.md` 作为速查表

### 第三阶段：自主实践（后续 2-4 周）
- 参会者自己建立 wiki
- 选择合适的 Schema（`SCHEMA_TEMPLATES.md`）
- 定期 Workshop 分享进度

---

## 🎯 使用场景

### 技术团队
- 架构决策记录
- 技术栈选型
- 问题和解决方案
- 最佳实践积累

### 产品团队
- 功能设计决策
- 用户研究发现
- 实验结果
- 竞品分析

### 运维/SRE 团队
- 线上事件记录
- 应急预案
- 容量规划
- 监控告警规则

---

## 🌟 成功指标

当你看到以下现象，说明这套系统有用了：

1. **新人上手快 50%** - "这个怎样做？" → wiki 一查就有答案
2. **知识不流失** - 关键人离职，知识保留下来了
3. **团队主动用** - 人们自发查询和更新 wiki
4. **决策有记录** - "为什么选这个?" → 有历史和权衡记录
5. **工作有复利** - 你的分析、学习被后续的人重用

---

## ⚠️ 常见陷阱

| 陷阱 | 症状 | 解决 |
|------|------|------|
| Schema 太复杂 | Entity 类型 >10 个 | 精简到核心 3-5 个 |
| 无人使用 | Wiki 建好了但没人查 | 在日常工作中推广 |
| 信息矛盾 | 不同页面说不同的话 | 定期 Lint 检查 |
| 人工维护 | "谁来更新 wiki？" | 自动化 Ingest，减少人工 |

---

## 📚 参考资源

- **原始论文**：[Karpathy LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- **进阶版本**：[LLM Wiki v2](https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2)
- **编辑工具**：[Obsidian](https://obsidian.md/)
- **演讲工具**：[Slidev](https://sli.dev/)

---

## 💬 Q&A

**Q: 这适合我们吗？**  
A: 只要你的团队有知识积累的需求，就适合。从 3 人团队到 500 人都用过。

**Q: 需要投入多少时间？**  
A: 初期 1-2 周（定义 Schema + ingest 文档）。后期维护成本接近 0（LLM 做）。

**Q: 我们不用 Claude 怎样办？**  
A: 支持任何 LLM（GPT-4、Claude、本地模型等）。核心思想不变。

**Q: Wiki 会不会积累错误？**  
A: 会。解决：人工审核重要决策 + 定期 Lint 检查 + 版本历史（Git）。

---

## 🎓 下一步

### 对于演讲者
1. 先读 [Karpathy 原文](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
2. 理解 [LLM Wiki v2](https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2)
3. 自己试验一个小 wiki
4. 根据需要修改 `slides.md`

### 对于参会者
1. 听完演讲，理解概念
2. 找到合适的 Schema（`SCHEMA_TEMPLATES.md`）
3. 跟 `WORKSHOP_GUIDE.md` 做一遍
4. 用 `QUICK_REFERENCE.md` 作为后续查阅

---

## 📝 文件导航

```
2ed-llm-wiki/
├── slides.md                # 📊 演讲 PPT（Slidev）
├── WORKSHOP_GUIDE.md        # 🛠️ 30 分钟实操指南
├── SCHEMA_TEMPLATES.md      # 📋 4 种行业模板
├── QUICK_REFERENCE.md       # 📌 快速参考卡
├── README.md                # 📖 本文件
├── package.json             # 项目配置
└── pnpm-lock.yaml           # 依赖锁定
```

---

## 🚀 现在就开始

1. **启动演讲**
   ```bash
   pnpm run dev
   ```

2. **分享资料**
   - 发送 `WORKSHOP_GUIDE.md` 给参会者
   - 发送 `SCHEMA_TEMPLATES.md` 和 `QUICK_REFERENCE.md`

3. **支持后续**
   - 回答参会者的问题
   - 分享他们的成功案例
   - 帮助他们优化 Schema

---

**记住**：好的 Schema 是成功的一半。  
前期多花点时间定义 Schema，后续的维护成本会大大降低。

祝你的分享成功！🎉
