---
theme: seriph
background: https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=1920&q=80
info: |
  ## 第二大脑进化论
  赋能个体，沉淀集体，构建团队的"复利型"记忆

  基于 Karpathy LLM Wiki 和 LLM Wiki v2 的思想分享
class: text-center
drawings:
  persist: false
transition: slide-left
duration: 60min
---

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
.image-panel {
  min-height: 16rem;
  border-radius: 1.5rem;
  border: 1px solid rgba(125, 211, 252, 0.25);
  background:
    linear-gradient(135deg, rgba(2, 6, 23, 0.2), rgba(2, 6, 23, 0.84)),
    url("https://images.unsplash.com/photo-1518770660439-4636190af475?w=1200&q=80") center/cover;
  box-shadow: 0 24px 70px rgba(2, 6, 23, 0.45);
}
</style>

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

---

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

---

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

---

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

---

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

---

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

---

# 但基础版还差一点

<div class="tech-kicker">What Makes a Wiki Trustworthy</div>

<div grid="~ cols-2 gap-5" class="mt-8 text-sm">
<v-clicks>

<div class="accent-card">
  <h3>旧信息和新信息混在一起</h3>
  <p class="muted mt-3">解决：给每条信息标记日期和可信度。</p>
</div>

<div class="accent-card">
  <h3>无法判断信息多可靠</h3>
  <p class="muted mt-3">解决：标注「非常确定」「可能对」「需要验证」。</p>
</div>

<div class="accent-card">
  <h3>不知道哪些信息连接</h3>
  <p class="muted mt-3">解决：建立关联：哪个人、哪个项目、哪个工具。</p>
</div>

<div class="accent-card">
  <h3>需要自己手工维护</h3>
  <p class="muted mt-3">解决：AI 自动检查、更新、整理。</p>
</div>

</v-clicks>
</div>

---

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

---

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

---

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

---

# 从"知识"到"团队智慧"：复利的关键

<div class="tech-kicker">Compounding Starts With Reuse</div>

<div grid="~ cols-2 gap-6" class="mt-10">

<div class="danger-card">

### ❌ 没有 Wiki 的工作流

<div class="mt-5 text-sm leading-8">
  <p>Q:「之前怎样解决这个问题？」</p>
  <p>→ Slack 搜索（乱）</p>
  <p>→ 找不到</p>
  <p>→ 再问人</p>
  <p>→ 每次都重复</p>
</div>

</div>

<div class="success-card">

### ✅ 有 Wiki 的工作流

<div class="mt-5 text-sm leading-8">
  <p>Q:「之前怎样解决这个问题？」</p>
  <p>→ Wiki 查询（有结构）</p>
  <p>→ 找到历史决策 + 权衡</p>
  <p>→ 看到 5 个类似案例</p>
  <p>→ 复用知识，节省时间</p>
</div>

</div>

</div>

<p class="mt-8 text-lg">
<strong>复利的秘密</strong>：每一次知识的查询和验证，都会强化这个知识在 Wiki 中的地位。
</p>

---

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

---

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

---

# 实际案例：团队协作更高效

<div class="tech-kicker">Scenario 2: Avoid Duplicate Work</div>

<div grid="~ cols-2 gap-6" class="mt-10 text-sm">

<div class="danger-card">

### 没有 Wiki 时

<div class="mt-5 space-y-3">
  <div class="glass-card">员工 A 做了项目 X</div>
  <div class="glass-card">员工 B 也在做项目 Y</div>
  <div class="glass-card">互相不知道进展</div>
  <div class="text-red-200 text-center">重复工作，冲突无人发现</div>
</div>

</div>

<div class="success-card">

### 有 Wiki 时

<div class="mt-5 space-y-3">
  <div class="glass-card">员工 A 的发现 → Wiki</div>
  <div class="glass-card">员工 B 立刻看到</div>
  <div class="glass-card">自动发现冲突和重复</div>
  <div class="text-emerald-200 text-center">不用开会，也能同步上下文</div>
</div>

</div>

</div>

---

# 反向思考：这套系统不是"完美的"

<div class="tech-kicker">Reality Check</div>

<div grid="~ cols-2 gap-5" class="mt-10 text-sm">
<v-clicks>

<div class="glass-card"><strong>LLM 不完美</strong><p class="muted mt-2">需要 Human-in-the-loop 审查、定期 lint。</p></div>
<div class="glass-card"><strong>信心评分很难</strong><p class="muted mt-2">用证据链，而不是只看数字。</p></div>
<div class="glass-card"><strong>需要纪律</strong><p class="muted mt-2">前期投入时间磨 Schema。</p></div>
<div class="glass-card"><strong>不是即插即用</strong><p class="muted mt-2">从小规模开始，逐步演进。</p></div>

</v-clicks>
</div>

---

# 如何扩展：从小团队到整个组织

<div class="tech-kicker">Scaling Path</div>

<div grid="~ cols-3 gap-5" class="mt-12 text-sm">
  <div class="flow-step">
    <div class="tech-kicker">Phase 1</div>
    <h3>刚开始</h3>
    <p class="muted mt-3">建立 Wiki、记录决策、手工整理。</p>
    <p class="mt-4 text-slate-300">2-4 周</p>
  </div>
  <div class="flow-step">
    <div class="tech-kicker">Phase 2</div>
    <h3>Wiki 成熟</h3>
    <p class="muted mt-3">用信心评分、自动连接、AI 维护。</p>
    <p class="mt-4 text-slate-300">1-2 个月</p>
  </div>
  <div class="success-card">
    <div class="tech-kicker">Phase 3</div>
    <h3>复利阶段</h3>
    <p class="muted mt-3">多个团队同步、自动更新、自我完善。</p>
    <p class="mt-4 text-slate-300">持续进行</p>
  </div>
</div>

<p class="mt-8 text-center text-xl">
从「我有个 Wiki」→「Wiki 在进化」→「Wiki 在增强团队」
</p>

---

# 从个人演进到组织能力

<div class="tech-kicker">Culture Shift</div>

<div grid="~ cols-2 gap-6" class="mt-10 text-sm">
  <div class="accent-card">
    <h3>关键转变</h3>
    <div class="mt-5 leading-8">
      <p>「我知道」→「我们知道」</p>
      <p>「搜索过去」→「学习未来」</p>
      <p>「个人笔记」→「团队资产」</p>
      <p>「遗忘曲线」→「复利曲线」</p>
    </div>
  </div>
  <div grid="~ cols-2 gap-4">
    <div class="metric"><div class="value">50%</div><p class="muted mt-2">新人上手更快</p></div>
    <div class="metric"><div class="value">60%</div><p class="muted mt-2">重复工作减少</p></div>
    <div class="metric"><div class="value">↑</div><p class="muted mt-2">决策质量更高</p></div>
    <div class="metric"><div class="value">↔</div><p class="muted mt-2">团队流动性提升</p></div>
  </div>
</div>

---

# 总结：如何进化

<div class="tech-kicker">Evolution Path</div>

<div class="mt-12 grid grid-cols-[1fr_auto_1fr_auto_1fr_auto_1fr] gap-3 items-center text-sm">
  <div class="flow-step"><div class="tech-kicker">01</div><h3>有 Wiki</h3><p class="muted">邮件、Slack 讨论能被找到。</p></div>
  <div class="flow-arrow">→</div>
  <div class="flow-step"><div class="tech-kicker">02</div><h3>AI 维护</h3><p class="muted">AI 读新文档，自动整理。</p></div>
  <div class="flow-arrow">→</div>
  <div class="flow-step"><div class="tech-kicker">03</div><h3>建立联系</h3><p class="muted">知识之间互相连接。</p></div>
  <div class="flow-arrow">→</div>
  <div class="success-card"><div class="tech-kicker">04</div><h3>团队共赢</h3><p class="muted">知识流动和增长。</p></div>
</div>

<p class="mt-10 text-center text-2xl font-bold">
赋能个体，沉淀集体，构建团队的"复利型"记忆
</p>

---

# 实践：怎样开始？

<div class="tech-kicker">Four Moves to Start</div>

<div grid="~ cols-4 gap-4" class="mt-10 text-sm">
  <div class="flow-step"><div class="tech-kicker">01</div><h3>建立框架</h3><p class="muted">新建 `sources/` 与 `wiki/`。</p></div>
  <div class="flow-step"><div class="tech-kicker">02</div><h3>定义规则</h3><p class="muted">写清知识类型、识别方式和记录方式。</p></div>
  <div class="flow-step"><div class="tech-kicker">03</div><h3>让 AI 帮忙</h3><p class="muted">把规则和旧文档交给 Claude。</p></div>
  <div class="success-card"><div class="tech-kicker">04</div><h3>开始使用</h3><p class="muted">先查 Wiki，再问人。</p></div>
</div>

<div class="glass-card mt-10 text-center">
  有问题？先查 Wiki。Wiki 不完整？让 AI 补上。
</div>

---

# 第一次对话：和 AI 讲清楚规则

<div class="tech-kicker">Schema Is the Operating Manual</div>

<div grid="~ cols-2 gap-6" class="mt-8 text-sm">
  <div class="accent-card">
    <h3>你要写一份「指导手册」给 AI</h3>
    <p class="muted mt-4">它定义什么是决策、坑点、工具，也定义怎样更新和连接页面。</p>
    <div class="image-panel mt-6"></div>
  </div>

  <div class="glass-card text-left leading-6">
    <div class="tech-kicker mb-3">Prompt Skeleton</div>
    <div class="space-y-3 text-sm">
      <p><strong>你的名字是 Wiki 助手。</strong></p>
      <p>你的工作：把新文档整合到我们的 wiki 里。</p>
      <div>
        <p class="text-sky-200 font-bold">步骤</p>
        <p>1. 读新文档，找关键信息</p>
        <p>2. 查看现有 wiki，找相关页面</p>
        <p>3. 更新或新建页面</p>
        <p>4. 更新目录和相关链接</p>
      </div>
      <div>
        <p class="text-sky-200 font-bold">规则</p>
        <p>决策页面：问题、选项、选择、原因</p>
        <p>坑点页面：问题、原因、解决方案、验证</p>
        <p>工具页面：用途、优缺点、何时用</p>
      </div>
    </div>
  </div>
</div>

---

# 演示：5 分钟完成一次 Wiki 更新

<div class="tech-kicker">A Tiny Ingest Pipeline</div>

<div class="mt-10 grid grid-cols-[1fr_auto_1fr_auto_1fr] gap-4 items-stretch text-sm">
  <div class="flow-step">
    <h3>3 份散乱文档</h3>
    <p class="muted mt-3">技术选择总结、Bug 修复记录、新工作流程。</p>
  </div>
  <div class="flow-arrow self-center">→</div>
  <div class="flow-step">
    <h3>AI 整理连接</h3>
    <p class="muted mt-3">找出技术、坑、流程，生成页面并发现矛盾。</p>
  </div>
  <div class="flow-arrow self-center">→</div>
  <div class="success-card">
    <h3>5 个有序页面</h3>
    <p class="muted mt-3">相关页面互相连接，目录自动更新。</p>
  </div>
</div>

<p class="mt-10 text-center text-xl font-bold">
下次你问相关问题，AI 能直接基于 Wiki 回答。
</p>

---

# 动手实验：30 分钟 Workshop

<div class="tech-kicker">Build a Working Prototype</div>

<div grid="~ cols-3 gap-5" class="mt-10 text-sm">
  <div class="flow-step">
    <div class="tech-kicker">Phase 0 · 5min</div>
    <h3>设定 Schema</h3>
    <p class="muted mt-3">你们的知识是什么？关键 entity 有哪些？</p>
  </div>
  <div class="flow-step">
    <div class="tech-kicker">Phase 1 · 15min</div>
    <h3>初始 ingest</h3>
    <p class="muted mt-3">选择 3-5 份既有文档，让 Claude 生成 Wiki 页面。</p>
  </div>
  <div class="success-card">
    <div class="tech-kicker">Phase 2 · 10min</div>
    <h3>尝试查询</h3>
    <p class="muted mt-3">问 Wiki 一个你之前解决过的问题，看它能回答多深。</p>
  </div>
</div>

<div class="glass-card mt-10 text-center text-xl">
  收获：一个可工作的、活的知识库原型。
</div>

---

# 现在开始：第一步很简单

<div class="tech-kicker">Start Small, Start Today</div>

<div grid="~ cols-4 gap-4" class="mt-10 text-sm">
  <div class="flow-step"><div class="tech-kicker">01</div><h3>新建文件夹</h3><p class="muted">`my-wiki` 或 `team-knowledge`。</p></div>
  <div class="flow-step"><div class="tech-kicker">02</div><h3>写下规则</h3><p class="muted">什么是好决策？怎样记录坑？</p></div>
  <div class="flow-step"><div class="tech-kicker">03</div><h3>邀请 AI</h3><p class="muted">告诉 Claude 规则，并给它一份旧文档。</p></div>
  <div class="success-card"><div class="tech-kicker">04</div><h3>检查结果</h3><p class="muted">调整、完善、开始用它。</p></div>
</div>

<p class="mt-8 text-center text-xl font-bold">
就这样，你的 Wiki 启动了。
</p>

---

# 需要什么工具？

<div class="tech-kicker">Keep the Tooling Simple</div>

<div grid="~ cols-2 gap-6" class="mt-10 text-sm">
  <div class="accent-card">
    <h3>必需</h3>
    <div class="mt-5 leading-8">
      <p><strong>记事本或 Word</strong> — 写 Wiki 页面</p>
      <p><strong>Claude 或 ChatGPT</strong> — AI 帮手</p>
      <p><strong>Google Drive 或电脑文件夹</strong> — 保存 Wiki</p>
    </div>
  </div>
  <div class="glass-card">
    <h3>可选（高级用法）</h3>
    <div class="mt-5 leading-8">
      <p><strong>Obsidian</strong> — 更漂亮的 Wiki 编辑器</p>
      <p><strong>Git</strong> — 多人协作时的版本控制</p>
      <p><strong>Notion</strong> — 如果团队已经在用</p>
    </div>
  </div>
</div>

<div class="glass-card mt-10 text-center">
  <div class="tech-kicker">Next Step</div>
  <p class="text-2xl font-bold mt-3">30 分钟后，你们就可以建立第一个 Wiki。</p>
  <p class="muted mt-3">Questions? Let's build your team's second brain.</p>
</div>



layout: full
---

<div class="h-full box-border flex items-center justify-center px-8 py-[50px]">
  <img
    src="/反馈.jpeg"
    class="max-h-full max-w-full h-auto w-auto rounded-2xl shadow-2xl object-contain"
  />
</div>
