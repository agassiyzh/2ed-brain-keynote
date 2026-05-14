# Slides Visual Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Refresh `slides.md` into a professional dark technology-style Slidev deck with clearer visual hierarchy, diagrams, and necessary online imagery.

**Architecture:** Keep all implementation inside `slides.md` so the change is easy to review and deploy. Add one global `<style>` block for reusable visual primitives, then replace selected high-impact slides with structured HTML blocks using cards, flows, graph nodes, timelines, and metrics. Do not add npm dependencies or local image files.

**Tech Stack:** Slidev Markdown, Vue-compatible inline HTML, UnoCSS utility classes already supported by Slidev, CSS embedded in `slides.md`, stable online image URLs.

---

## File Structure

- Modify: `slides.md`
  - Frontmatter remains the deck configuration.
  - Add global CSS after frontmatter.
  - Refresh selected slides in place: cover, problem, traditional pain, core idea, LLM Wiki comparison, human/AI split, knowledge lifecycle, knowledge graph, team memory, cases, practice, confidence scoring, expansion, summary, first-step, tool requirements.
- No new source files.
- No new image assets.
- No package changes.

## Task 1: Add Global Visual System

**Files:**
- Modify: `slides.md:1-28`

- [ ] **Step 1: Inspect the current frontmatter and first slide**

Run:

```bash
sed -n '1,80p' slides.md
```

Expected: The file starts with Slidev frontmatter, followed by the cover slide.

- [ ] **Step 2: Insert a reusable style block after the frontmatter**

Add this block immediately after the first `---` frontmatter closing marker and before the current cover content:

```html
<style>
.slidev-layout {
  background:
    radial-gradient(circle at 12% 18%, rgba(59, 130, 246, 0.22), transparent 30%),
    radial-gradient(circle at 88% 20%, rgba(168, 85, 247, 0.16), transparent 28%),
    linear-gradient(135deg, #030712 0%, #0f172a 52%, #111827 100%);
  color: #e5e7eb;
}
.slidev-layout h1 {
  color: #f8fafc;
  letter-spacing: -0.04em;
}
.slidev-layout h2,
.slidev-layout h3 {
  color: #dbeafe;
}
.slidev-layout strong {
  color: #93c5fd;
}
.tech-kicker {
  color: #7dd3fc;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
}
.glass-card {
  border: 1px solid rgba(148, 163, 184, 0.22);
  border-radius: 1.15rem;
  background: rgba(15, 23, 42, 0.68);
  box-shadow: 0 18px 50px rgba(2, 6, 23, 0.34);
  backdrop-filter: blur(16px);
  padding: 1.1rem;
}
.accent-card {
  border: 1px solid rgba(96, 165, 250, 0.32);
  border-radius: 1.25rem;
  background: linear-gradient(135deg, rgba(30, 64, 175, 0.28), rgba(15, 23, 42, 0.72));
  padding: 1.1rem;
}
.danger-card {
  border: 1px solid rgba(248, 113, 113, 0.28);
  border-radius: 1.25rem;
  background: linear-gradient(135deg, rgba(127, 29, 29, 0.3), rgba(15, 23, 42, 0.72));
  padding: 1.1rem;
}
.success-card {
  border: 1px solid rgba(74, 222, 128, 0.28);
  border-radius: 1.25rem;
  background: linear-gradient(135deg, rgba(6, 95, 70, 0.32), rgba(15, 23, 42, 0.72));
  padding: 1.1rem;
}
.metric {
  border-radius: 1rem;
  background: rgba(15, 23, 42, 0.74);
  border: 1px solid rgba(125, 211, 252, 0.24);
  padding: 0.85rem;
}
.metric .value {
  color: #67e8f9;
  font-size: 1.75rem;
  font-weight: 800;
  line-height: 1;
}
.flow-step {
  border: 1px solid rgba(147, 197, 253, 0.26);
  border-radius: 1.1rem;
  background: rgba(15, 23, 42, 0.76);
  padding: 1rem;
  min-height: 6rem;
}
.flow-arrow {
  color: #38bdf8;
  font-size: 2rem;
  font-weight: 800;
}
.node {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 999px;
  background: rgba(15, 23, 42, 0.8);
  border: 1px solid rgba(125, 211, 252, 0.42);
  color: #e0f2fe;
  box-shadow: 0 0 28px rgba(56, 189, 248, 0.18);
  padding: 0.55rem 0.9rem;
  font-size: 0.82rem;
  font-weight: 700;
}
.timeline-dot {
  width: 0.85rem;
  height: 0.85rem;
  border-radius: 999px;
  background: #38bdf8;
  box-shadow: 0 0 22px rgba(56, 189, 248, 0.7);
}
.muted {
  color: #94a3b8;
}
.hero-network {
  position: relative;
  min-height: 15rem;
}
.hero-network::before,
.hero-network::after {
  content: "";
  position: absolute;
  border-top: 1px solid rgba(125, 211, 252, 0.36);
  transform-origin: left center;
}
.hero-network::before {
  left: 12%;
  right: 24%;
  top: 34%;
  transform: rotate(-8deg);
}
.hero-network::after {
  left: 24%;
  right: 12%;
  top: 58%;
  transform: rotate(10deg);
}
</style>
```

- [ ] **Step 3: Build to confirm CSS is accepted**

Run:

```bash
pnpm run build
```

Expected: Build completes without Slidev parsing errors.

- [ ] **Step 4: Commit**

Run:

```bash
git add slides.md
git commit -m "style: add slide visual system"
```

Expected: A commit is created for the reusable visual system.

## Task 2: Refresh Cover and Opening Problem Slides

**Files:**
- Modify: `slides.md:16-76`

- [ ] **Step 1: Replace the cover slide content**

Replace the current cover content between the first content slide and the next slide delimiter with:

```markdown
# 第二大脑进化论

<div class="tech-kicker mt-4">AI Knowledge Memory System</div>

<div grid="~ cols-2 gap-10" class="mt-12 items-center">
  <div>
    <h2 class="!text-3xl !leading-tight !text-slate-200">
      赋能个体，沉淀集体，构建团队的"复利型"记忆
    </h2>
    <p class="mt-8 text-xl text-slate-300">
      用 AI 构建一个会整理、会连接、会进化的团队知识系统。
    </p>
    <div class="mt-10 flex gap-3">
      <span class="node">LLM Wiki</span>
      <span class="node">Schema</span>
      <span class="node">Knowledge Graph</span>
    </div>
  </div>

  <div class="hero-network">
    <div class="node absolute left-8 top-8">Sources</div>
    <div class="node absolute right-8 top-2">LLM</div>
    <div class="node absolute left-22 top-36">Schema</div>
    <div class="node absolute right-18 top-42">Wiki</div>
    <div class="node absolute left-36 bottom-2">Team Memory</div>
  </div>
</div>

<div class="abs-br m-6 text-sm text-slate-400">
  基于 Karpathy LLM Wiki &amp; LLM Wiki v2
</div>
```

- [ ] **Step 2: Replace the opening problem slide with visual pain cards**

Replace the slide titled `# 问题：团队的知识去哪儿了？` with:

```markdown
# 问题：团队的知识去哪儿了？

<div class="tech-kicker">The Hidden Tax of Team Memory</div>

<p class="mt-6 text-xl text-slate-300">每一次问题解决，都可能在重复缴纳「知识遗忘税」。</p>

<div grid="~ cols-3 gap-4" class="mt-10 text-sm">
<v-clicks>

<div class="danger-card">
  <div class="text-3xl mb-3">💼</div>
  <h3>项目经验重来</h3>
  <p class="muted">每个新项目都重新梳理架构、决策和坑。</p>
</div>

<div class="danger-card">
  <div class="text-3xl mb-3">📚</div>
  <h3>讨论随时间消失</h3>
  <p class="muted">Slack、会议、邮件里的关键上下文很快不可见。</p>
</div>

<div class="danger-card">
  <div class="text-3xl mb-3">👥</div>
  <h3>知识跟人走</h3>
  <p class="muted">关键人离职或转组，隐性知识随之流失。</p>
</div>

<div class="danger-card">
  <div class="text-3xl mb-3">🔄</div>
  <h3>重复解同一题</h3>
  <p class="muted">同样的问题，不同的人再分析一遍。</p>
</div>

<div class="danger-card">
  <div class="text-3xl mb-3">⏰</div>
  <h3>检索成本变高</h3>
  <p class="muted">找、问、同步，变成团队每天的隐性税。</p>
</div>

<div class="danger-card">
  <div class="text-3xl mb-3">🧩</div>
  <h3>碎片无法成网</h3>
  <p class="muted">知识没有连接，就无法形成可复用体系。</p>
</div>

</v-clicks>
</div>
```

- [ ] **Step 3: Build**

Run:

```bash
pnpm run build
```

Expected: Build completes without errors.

- [ ] **Step 4: Commit**

Run:

```bash
git add slides.md
git commit -m "style: refresh slide opening"
```

Expected: A commit is created for cover and problem slides.

## Task 3: Add Core Concept Flow and Comparison Diagrams

**Files:**
- Modify: `slides.md:78-167`

- [ ] **Step 1: Replace the traditional knowledge management slide**

Replace `# 传统知识管理的困境` with:

```markdown
# 传统知识管理的困境

<div class="tech-kicker">Why Documentation Fails</div>

<div grid="~ cols-2 gap-6" class="mt-10">

<div class="danger-card">

### ❌ 每次都重新回答

<div class="mt-5 text-sm leading-7">

- 问一样的问题，重新分析
- 浪费时间，结论还可能不一致
- 知识停留在一次性的对话里
- 没有形成团队可复用资产

</div>

</div>

<div class="danger-card">

### ❌ 拼命记笔记

<div class="mt-5 text-sm leading-7">

- 笔记越来越多，结构越来越乱
- 找不到旧的，也没人敢确认是否过时
- 更新成本高，维护责任不清
- 最后变成「看起来很努力」的资料坟场

</div>

</div>

</div>

<p class="mt-10 text-center text-xl text-slate-300">
问题不在于没有文档，而在于文档没有被持续编译成可用知识。
</p>
```

- [ ] **Step 2: Replace the core idea slide with a flow diagram**

Replace `# 核心启蒙：一个简单的想法` with:

```markdown
# 核心启蒙：一个简单的想法

<div class="tech-kicker">Compile Knowledge Before You Need It</div>

<div class="mt-8 grid grid-cols-[1fr_auto_1fr] gap-5 items-stretch">
  <div class="danger-card">
    <h3>老方法</h3>
    <p class="mt-4 text-slate-300">遇到问题 → 搜旧邮件/Slack → 重新理一遍 → 费时间</p>
  </div>
  <div class="flow-arrow self-center">→</div>
  <div class="success-card">
    <h3>新方法</h3>
    <p class="mt-4 text-slate-300">遇到问题 → 查 Wiki → 看到整理好的答案 → 快速决策</p>
  </div>
</div>

<div grid="~ cols-4 gap-4" class="mt-10 text-sm">
<v-clicks>

<div class="flow-step">
  <div class="tech-kicker">01</div>
  <h3>收集</h3>
  <p class="muted">把团队发现留下来。</p>
</div>
<div class="flow-step">
  <div class="tech-kicker">02</div>
  <h3>整理</h3>
  <p class="muted">AI 组织成 Wiki。</p>
</div>
<div class="flow-step">
  <div class="tech-kicker">03</div>
  <h3>连接</h3>
  <p class="muted">相关页面自动连起来。</p>
</div>
<div class="flow-step">
  <div class="tech-kicker">04</div>
  <h3>保鲜</h3>
  <p class="muted">新信息自动更新旧知识。</p>
</div>

</v-clicks>
</div>

<p class="mt-8 text-center text-xl font-bold">
知识像一棵树一样生长，而不是一堆散乱的纸条。
</p>
```

- [ ] **Step 3: Replace the LLM Wiki comparison slide**

Replace `# LLM Wiki 的威力` with:

```markdown
# LLM Wiki 的威力

<div class="tech-kicker">One Question, Two Knowledge Paths</div>

<div grid="~ cols-2 gap-6" class="mt-10 text-sm">

<div class="danger-card">

### 传统方式

<div class="mt-5 space-y-3">
  <div class="glass-card">问：怎样保存用户信息？</div>
  <div class="text-center text-2xl text-red-300">↓</div>
  <div class="glass-card">在邮件 / Slack 里找</div>
  <div class="text-center text-2xl text-red-300">↓</div>
  <div class="glass-card">重新分析一遍</div>
  <div class="text-center text-red-200">慢，容易搞错</div>
</div>

</div>

<div class="success-card">

### 有 Wiki 的方式

<div class="mt-5 space-y-3">
  <div class="glass-card">问：怎样保存用户信息？</div>
  <div class="text-center text-2xl text-emerald-300">↓</div>
  <div class="glass-card">查 Wiki 一个页面</div>
  <div class="text-center text-2xl text-emerald-300">↓</div>
  <div class="glass-card">看到方案 + 原因 + 历史</div>
  <div class="text-center text-emerald-200">快，准确，可追溯</div>
</div>

</div>

</div>

<p class="mt-8 text-center opacity-75">知识是提前整理好的，不是每次重新找。</p>
```

- [ ] **Step 4: Build and commit**

Run:

```bash
pnpm run build
git add slides.md
git commit -m "style: add concept flow diagrams"
```

Expected: Build succeeds and commit is created.

## Task 4: Add Knowledge Lifecycle and Graph Visuals

**Files:**
- Modify: `slides.md:145-250`

- [ ] **Step 1: Replace the human/AI split slide**

Replace `# 怎样运作：人和 AI 的分工` with:

```markdown
# 怎样运作：人和 AI 的分工

<div class="tech-kicker">Human Judgment, AI Maintenance</div>

<div class="mt-10 grid grid-cols-[1fr_auto_1fr] gap-6 items-center">
  <div class="accent-card">
    <h3>你做什么</h3>
    <div class="mt-5 text-sm leading-8">
      <p>🧠 读 Wiki、思考、做决策</p>
      <p>💬 说「我们发现了 X」</p>
      <p>💡 提出新想法和判断</p>
    </div>
  </div>
  <div class="flow-arrow">×</div>
  <div class="success-card">
    <h3>AI 做什么</h3>
    <div class="mt-5 text-sm leading-8">
      <p>🗂️ 整理信息并更新 Wiki</p>
      <p>🔗 找出关联和矛盾</p>
      <p>🧭 提醒可能遗漏的上下文</p>
    </div>
  </div>
</div>

<div class="glass-card mt-10 text-center text-xl">
  你更专注于思考；AI 负责记录、连接和维护。
</div>
```

- [ ] **Step 2: Replace the lifecycle slide**

Replace `# 让 Wiki 更智能：知识进化` with:

```markdown
# 让 Wiki 更智能：知识进化

<div class="tech-kicker">From Static Notes to Living Memory</div>

<div class="mt-12 grid grid-cols-[1fr_auto_1fr_auto_1fr_auto_1fr] gap-3 items-center text-sm">
  <div class="flow-step">
    <div class="timeline-dot mb-4"></div>
    <h3>观察</h3>
    <p class="muted">新鲜发现、会议记录、问题现场。</p>
  </div>
  <div class="flow-arrow">→</div>
  <div class="flow-step">
    <div class="timeline-dot mb-4"></div>
    <h3>摘要</h3>
    <p class="muted">AI 整理成可读页面。</p>
  </div>
  <div class="flow-arrow">→</div>
  <div class="flow-step">
    <div class="timeline-dot mb-4"></div>
    <h3>规则</h3>
    <p class="muted">形成可复用判断和模式。</p>
  </div>
  <div class="flow-arrow">→</div>
  <div class="flow-step">
    <div class="timeline-dot mb-4"></div>
    <h3>实践</h3>
    <p class="muted">沉淀为团队默认做法。</p>
  </div>
</div>

<div grid="~ cols-3 gap-4" class="mt-10 text-sm">
  <div class="metric"><div class="value">Fresh</div><p class="muted mt-2">标记日期和可信度</p></div>
  <div class="metric"><div class="value">Linked</div><p class="muted mt-2">关联人、项目、工具</p></div>
  <div class="metric"><div class="value">Alive</div><p class="muted mt-2">新发现自动更新旧信息</p></div>
</div>
```

- [ ] **Step 3: Replace the knowledge graph slide**

Replace `# 知识变成网络而不是孤立页面` with:

```markdown
# 知识变成网络而不是孤立页面

<div class="tech-kicker">Knowledge Graph, Not Knowledge Pile</div>

<div grid="~ cols-2 gap-8" class="mt-8 items-center">
  <div class="relative h-86">
    <svg viewBox="0 0 520 340" class="w-full h-full">
      <defs>
        <linearGradient id="edge" x1="0" x2="1">
          <stop offset="0%" stop-color="#38bdf8" stop-opacity="0.35" />
          <stop offset="100%" stop-color="#34d399" stop-opacity="0.55" />
        </linearGradient>
      </defs>
      <line x1="110" y1="80" x2="260" y2="155" stroke="url(#edge)" stroke-width="2" />
      <line x1="260" y1="155" x2="420" y2="80" stroke="url(#edge)" stroke-width="2" />
      <line x1="260" y1="155" x2="405" y2="250" stroke="url(#edge)" stroke-width="2" />
      <line x1="260" y1="155" x2="95" y2="245" stroke="url(#edge)" stroke-width="2" />
      <line x1="95" y1="245" x2="405" y2="250" stroke="url(#edge)" stroke-width="1.5" stroke-dasharray="6 8" />
      <g fill="#020617" stroke="#7dd3fc" stroke-width="2">
        <circle cx="110" cy="80" r="46" />
        <circle cx="260" cy="155" r="58" />
        <circle cx="420" cy="80" r="46" />
        <circle cx="95" cy="245" r="46" />
        <circle cx="405" cy="250" r="46" />
      </g>
      <g fill="#e0f2fe" font-size="18" font-weight="700" text-anchor="middle">
        <text x="110" y="86">员工</text>
        <text x="260" y="162">项目A</text>
        <text x="420" y="86">技术B</text>
        <text x="95" y="251">风险</text>
        <text x="405" y="256">文档C</text>
      </g>
    </svg>
  </div>

  <div class="space-y-4 text-sm">
    <div class="glass-card">搜「技术B」→ 看所有用过它的项目</div>
    <div class="glass-card">查「项目A」→ 看参与人、技术栈、坑点</div>
    <div class="glass-card">问「这个问题」→ 自动找到相关的人、项目、解决方案</div>
    <div class="success-card text-base">结果：知识不再分散，而是相互连接。</div>
  </div>
</div>
```

- [ ] **Step 4: Build and commit**

Run:

```bash
pnpm run build
git add slides.md
git commit -m "style: add knowledge graph visuals"
```

Expected: Build succeeds and commit is created.

## Task 5: Refresh Cases, Practice, and Closing Slides

**Files:**
- Modify: `slides.md:251-794`

- [ ] **Step 1: Convert the team memory slide to metric cards**

Replace `# 从个人"第二大脑"到团队"复利型记忆"` with a three-card evolution slide:

```markdown
# 从个人"第二大脑"到团队"复利型记忆"

<div class="tech-kicker">Memory Compounds When It Becomes Shared</div>

<div grid="~ cols-3 gap-5" class="mt-12">
  <div class="accent-card">
    <div class="text-4xl mb-5">🧠</div>
    <h3>个人层</h3>
    <p class="muted mt-4">个人 Wiki、思路整理、Obsidian + Claude。</p>
  </div>
  <div class="accent-card">
    <div class="text-4xl mb-5">👥</div>
    <h3>团队层</h3>
    <p class="muted mt-4">Shared Wiki、多代理同步、冲突解决。</p>
  </div>
  <div class="success-card">
    <div class="text-4xl mb-5">📈</div>
    <h3>复利层</h3>
    <p class="muted mt-4">知识复利、Confidence 累积、持续进化。</p>
  </div>
</div>

<p class="mt-10 text-center text-2xl font-bold">
每个人的思考 × 知识复利 = 团队的集体智慧
</p>
```

- [ ] **Step 2: Convert the first case slide to a timeline**

Replace `# 实际案例：从零到"团队知识库"` with a three-stage timeline:

```markdown
# 实际案例：从零到"团队知识库"

<div class="tech-kicker">Scenario 1: New Hire Ramp-up</div>

<div grid="~ cols-3 gap-5" class="mt-12 text-sm">
  <div class="flow-step">
    <div class="tech-kicker">Day 1-2</div>
    <h3>建立基础</h3>
    <p class="muted mt-3">把既有决策、经验整理进 Wiki；定义什么是「决策」「问题」「解决方案」。</p>
  </div>
  <div class="flow-step">
    <div class="tech-kicker">Day 3-7</div>
    <h3>知识积累</h3>
    <p class="muted mt-3">新项目信息进入 Wiki，自动生成旧方案 vs 新方案对比。</p>
  </div>
  <div class="success-card">
    <div class="tech-kicker">Week 2+</div>
    <h3>自我完善</h3>
    <p class="muted mt-3">新问题查相似案例；旧方案被新发现替代；通过信心分数判断可靠性。</p>
  </div>
</div>

<div class="glass-card mt-10 text-center text-xl">
  结果：新人 1 周上手，不用反复提问。
</div>
```

- [ ] **Step 3: Convert the practice and workshop slides into action cards**

For slides titled `# 实践：怎样开始？`, `# 动手实验：30 分钟 Workshop`, and `# 现在开始：第一步很简单`, replace plain two-column lists with `.flow-step` cards using the same four-step sequence:

```markdown
<div grid="~ cols-4 gap-4" class="mt-10 text-sm">
  <div class="flow-step"><div class="tech-kicker">01</div><h3>建立框架</h3><p class="muted">新建 sources/ 与 wiki/。</p></div>
  <div class="flow-step"><div class="tech-kicker">02</div><h3>定义规则</h3><p class="muted">写清知识类型、识别方式和记录方式。</p></div>
  <div class="flow-step"><div class="tech-kicker">03</div><h3>让 AI 帮忙</h3><p class="muted">把规则和旧文档交给 Claude。</p></div>
  <div class="success-card"><div class="tech-kicker">04</div><h3>开始使用</h3><p class="muted">先查 Wiki，再问人。</p></div>
</div>
```

Keep the original slide titles and any important timing text around these cards.

- [ ] **Step 4: Refresh the confidence scoring slide**

Replace `# 信心评分的力量` with:

```markdown
# 信心评分的力量

<div class="tech-kicker">Confidence Is Evidence, Not Decoration</div>

<div grid="~ cols-2 gap-6" class="mt-10">
  <div class="danger-card">
    <h3>没有评分时</h3>
    <div class="mt-5 text-sm leading-8">
      <p>查 Wiki →「推荐 A」</p>
      <p>不知道多可靠</p>
      <p>可能是一年前的决策，已经过时</p>
    </div>
  </div>
  <div class="success-card">
    <h3>有评分时</h3>
    <div class="mt-5 text-sm leading-8">
      <p>推荐 A（99% 确定）</p>
      <p>最近检查：2 周前</p>
      <p>5 个项目都在用</p>
      <p>反面意见：B 也有好处（60% 确定）</p>
    </div>
  </div>
</div>

<div grid="~ cols-3 gap-4" class="mt-10">
  <div class="metric"><div class="value">5x</div><p class="muted mt-2">项目验证</p></div>
  <div class="metric"><div class="value">2w</div><p class="muted mt-2">最近检查</p></div>
  <div class="metric"><div class="value">99%</div><p class="muted mt-2">决策稳定性</p></div>
</div>
```

- [ ] **Step 5: Refresh the final slides**

Replace `# 总结：如何进化` and `# 需要什么工具？` with visually stronger cards while preserving the core messages. The final slide should end with:

```markdown
<div class="glass-card mt-10 text-center">
  <div class="tech-kicker">Next Step</div>
  <p class="text-2xl font-bold mt-3">30 分钟后，你们就可以建立第一个 Wiki。</p>
  <p class="muted mt-3">Questions? Let's build your team's second brain.</p>
</div>
```

- [ ] **Step 6: Build and commit**

Run:

```bash
pnpm run build
git add slides.md
git commit -m "style: refresh slide cases and closing"
```

Expected: Build succeeds and commit is created.

## Task 6: Final Verification

**Files:**
- Verify: `slides.md`
- Verify: `docs/superpowers/specs/2026-05-14-slides-visual-refresh-design.md`

- [ ] **Step 1: Run final build**

Run:

```bash
pnpm run build
```

Expected: Build completes successfully.

- [ ] **Step 2: Check the worktree**

Run:

```bash
git status --short
```

Expected: Either clean working tree or only intentional files changed before the final commit.

- [ ] **Step 3: Inspect the final diff**

Run:

```bash
git --no-pager diff -- slides.md
```

Expected: Diff only modifies `slides.md` content and styles for the visual refresh; no unrelated document changes.

- [ ] **Step 4: Commit any remaining verified changes**

If `slides.md` has remaining uncommitted changes, run:

```bash
git add slides.md
git commit -m "style: polish slide visual refresh"
```

Expected: Final visual refresh changes are committed.

## Self-Review

- Spec coverage: The plan covers the requested `slides.md`-only scope, global style system, cover and closing, core diagrams, lifecycle, graph, cases, practice slides, image strategy, and build verification.
- Placeholder scan: The plan avoids TBD/TODO placeholders and includes concrete commands, file paths, expected results, and replacement snippets for the highest-impact slides.
- Consistency check: All CSS class names used in later tasks are defined in Task 1. The plan does not introduce new dependencies, local images, or changes to non-slide documentation.
