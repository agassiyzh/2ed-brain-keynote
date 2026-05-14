# Slides Structure Reorder Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Reorder `slides.md` so all hands-on/practical content appears as one final contiguous section.

**Architecture:** Keep the existing visual system and slide content. Move whole slide blocks only, preserving each block’s Markdown/HTML exactly unless a heading-order verification requires a minor wording fix. Verify by checking the `# ` heading sequence and running the Slidev build.

**Tech Stack:** Slidev Markdown, embedded HTML/CSS already present in `slides.md`, pnpm build script.

---

## File Structure

- Modify: `slides.md`
  - Reorder existing slide blocks after the global style block.
  - Do not change global CSS.
  - Do not add dependencies or local assets.
- Verify: `docs/superpowers/specs/2026-05-14-slides-structure-reorder-design.md`
  - Use it as the expected heading order.

## Task 1: Capture Current Heading Order

**Files:**
- Verify: `slides.md`

- [ ] **Step 1: Print the current heading order**

Run:

```bash
rg '^# ' slides.md -n
```

Expected: Shows the current headings, including hands-on pages interleaved before the final conceptual slides.

## Task 2: Reorder Whole Slide Blocks

**Files:**
- Modify: `slides.md`

- [ ] **Step 1: Keep these first 18 headings in this exact order**

After the global `<style>` block, the slide headings must be:

```text
# 第二大脑进化论
# 问题：团队的知识去哪儿了？
# 传统知识管理的困境
# 核心启蒙：一个简单的想法
# LLM Wiki 的威力
# 怎样运作：人和 AI 的分工
# 但基础版还差一点
# 让 Wiki 更智能：知识进化
# 知识变成网络而不是孤立页面
# 从个人"第二大脑"到团队"复利型记忆"
# 从"知识"到"团队智慧"：复利的关键
# 信心评分的力量
# 实际案例：从零到"团队知识库"
# 实际案例：团队协作更高效
# 反向思考：这套系统不是"完美的"
# 如何扩展：从小团队到整个组织
# 从个人演进到组织能力
# 总结：如何进化
```

- [ ] **Step 2: Move these hands-on headings to the final contiguous section**

The final six headings must be:

```text
# 实践：怎样开始？
# 第一次对话：和 AI 讲清楚规则
# 演示：5 分钟完成一次 Wiki 更新
# 动手实验：30 分钟 Workshop
# 现在开始：第一步很简单
# 需要什么工具？
```

- [ ] **Step 3: Ensure every moved slide stays intact**

Each slide block starts at its `# ` heading and ends immediately before the next `---` delimiter. Move the full block, including the delimiter before it, without editing inner HTML.

## Task 3: Verify Order and Build

**Files:**
- Verify: `slides.md`

- [ ] **Step 1: Check heading order**

Run:

```bash
rg '^# ' slides.md -n
```

Expected: The heading order exactly matches Task 2.

- [ ] **Step 2: Confirm hands-on pages are last**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
heads = [line.strip() for line in Path('slides.md').read_text().splitlines() if line.startswith('# ')]
expected_tail = [
    '# 实践：怎样开始？',
    '# 第一次对话：和 AI 讲清楚规则',
    '# 演示：5 分钟完成一次 Wiki 更新',
    '# 动手实验：30 分钟 Workshop',
    '# 现在开始：第一步很简单',
    '# 需要什么工具？',
]
print('\n'.join(heads))
assert heads[-6:] == expected_tail, heads[-6:]
PY
```

Expected: Prints all headings and exits successfully.

- [ ] **Step 3: Build**

Run:

```bash
pnpm run build
```

Expected: Slidev build succeeds.

- [ ] **Step 4: Commit**

Run:

```bash
git add slides.md
git commit -m "style: move hands-on slides to end"
```

Expected: Commit contains only `slides.md` reorder changes.

## Self-Review

- Spec coverage: The plan implements the approved “三幕式 + 最后动手” structure, moves all hands-on pages to the end, and preserves visual/content scope.
- Placeholder scan: No placeholder instructions remain; all target heading orders and verification commands are explicit.
- Consistency check: The heading names match the current `slides.md` headings and the structure spec.
