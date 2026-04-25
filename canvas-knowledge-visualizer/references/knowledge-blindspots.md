# Knowledge Blindspots Feature

## What Are Knowledge Blindspots?

Knowledge blindspots (`#?` tags) represent content that the user **previously did not understand**. These are high-value learning points that should be highlighted in the canvas for easy review and reinforcement.

## When to Use This Feature

Use this enhancement when:

* The source markdown file contains content tagged with `#?`

* User wants to highlight their previous knowledge gaps

* User wants to create a focused review path for learning

* User explicitly requests "标注知识盲区" (mark knowledge blindspots)

## Implementation Steps

### Step 1: Identify Blindspot Content

During content analysis, scan the source file for `#?` tags. Extract:

* The specific content marked with `#?`

* The context around it (sufficient for understanding)

* The topic/category it belongs to

### Step 2: Create Knowledge Blindspots Node

**Node Configuration:**

* **Type**: `text`
* **ID**: `knowledge-blindspots`
* **Position**: Below the "summary" node, centered
* **Color**: Red (1) - highest priority
* **Width**: 800-1000
* **Height**: Dynamic based on content (minimum 400)

**Content Format:**

```markdown
## 知识盲区

### 标签说明
`#?` 标记的内容代表之前完全不懂的知识点，是本次学习的重点。

### 盲区列表

#### [Topic 1]
> Extracted content with #? tag
>
> Context/explanation as needed

#### [Topic 2]
> Extracted content with #? tag
>
> Context/explanation as needed

#知识盲区 #学习重点
```

### Step 3: Create Connections

**Connection Pattern:**

The "knowledge-blindspots" node should connect to **all** topic nodes that contain blindspot content.

**Edge Labels:**

* Use concise labels like "盲区", "盲点", "知识空白", "重点"

**Edge Direction:**

* `toSide`: `top` (blindspots node at bottom)

* `fromSide`: `bottom` (from topic nodes)

**Example Edge:**

```json
{
  "id": "topic-blindspots",
  "fromNode": "topic-id",
  "fromSide": "bottom",
  "toNode": "knowledge-blindspots",
  "toSide": "top",
  "label": "盲区"
}
```

### Step 4: Positioning Strategy

**Default Position:**

```
Knowledge Blindspots: x=400,  y=summary.y + 800
```

**Adjustments:**

* If archive suggestions exist, place blindspots between summary and archive suggestions

* Maintain vertical alignment with center column

* Ensure no overlapping with other nodes

## Examples

### Example 1: Single Blindspot Topic

```markdown
## 知识盲区

### 标签说明
`#?` 标记的内容代表之前完全不懂的知识点，是本次学习的重点。

### 盲区列表

#### VPC（虚拟私有云）
在公有云里给客户围个"小院子"。

> **应用思考**：如何把这些枯燥的基础设施，通过 AI 的包装，变成客户一听就想买的"智能方案"？

#知识盲区 #学习重点 #云计算
```

### Example 2: Multiple Blindspots

```markdown
## 知识盲区

### 标签说明
`#?` 标记的内容代表之前完全不懂的知识点，是本次学习的重点。

### 盲区列表

#### VPC（虚拟私有云）
在公有云里给客户围个"小院子"。如何通过 AI 包装成智能方案。

#### Prompt Caching
重复的背景部分只收 1/10 的钱，RAG 场景下的省钱神器。

#### Gateway 路由机制
OpenClaw 中负责意图识别与需求分发的核心组件。

#知识盲区 #学习重点
```

## Best Practices

### ✅ DO

* Extract **concise** blindspot content (remove redundancy)

* Maintain **context** for understanding

* Use **consistent formatting** across blindspots

* Connect to **all** relevant topic nodes

* Place the node **visually prominently** (red color, centered)

### ❌ DON'T

* Don't copy entire paragraphs blindly

* Don't create blindspots node when source has **no** `#?` tags

* Don't overcomplicate edge labels

* Don't position the node in a way that disrupts main flow

## Integration with Core Workflow

**Where to Insert:**

After **Step 4: Optimization and Refinement** in the main SKILL.md workflow.

**Checklist Addition:**

```
* [ ] If source contains #? tags:
    * [ ] Create knowledge-blindspots node
    * [ ] Extract blindspot content
    * [ ] Create edges to relevant topics
    * [ ] Position below summary node
```

## Visual Impact

**Before:** Standard canvas with topic nodes and connections

**After:** Enhanced canvas with a centralized "Knowledge Blindspots" node that:
* Highlights learning points in red
* Creates a focused review path
* Shows the user's growth trajectory
* Makes blindspots easily accessible for future reference

## User Feedback Integration

When user reviews the canvas, they may want to:
* Add/remove blindspots
* Adjust connections
* Change the position
* Modify the content format

Be prepared to iterate based on their feedback.

---

**Note:** This feature is **optional**. Only use it when the source file contains `#?` tags or the user explicitly requests it. The core canvas generation workflow remains unchanged.
