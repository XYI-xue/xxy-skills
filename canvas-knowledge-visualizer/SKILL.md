---
name: canvas-knowledge-visualizer
description: Transform messy inbox markdown files into structured, visually clear Obsidian Canvas knowledge maps. Use this skill when the user explicitly wants to create, generate, or build a Canvas from their inbox notes—specifically when they mention "创建canvas", "生成canvas", "做成canvas", "可视化成canvas", "canvas可视化", or provide a specific inbox md file path and request Canvas creation. This skill excels at turning disorganized daily notes into clear, interconnected knowledge visualizations that help users quickly understand content structure and relationships.
---

# Canvas Knowledge Visualizer

Transform messy inbox markdown files into structured, visually clear Obsidian Canvas visualizations that help users quickly understand content structure and relationships.

## When to Use This Skill

Use this skill when:
- User has a messy inbox md file with scattered information
- User wants to visualize their notes as a canvas
- User mentions organizing, structuring, or visualizing content
- User wants to see relationships between different topics
- User has daily notes that feel disorganized or redundant
- User wants to create a knowledge map from their notes

## Core Workflow

### Step 1: Content Analysis

1. **Read the inbox md file** - Start by reading the complete markdown file
2. **Identify core theme** - Find the central topic or main subject
3. **Extract major topics** - Break down content into 5-10 key topics
4. **Identify relationships** - Note how topics connect to each other

**What to look for:**
- Repeated content or themes
- Distinct subject areas
- Natural groupings (e.g., technical vs. conceptual)
- Cause-effect relationships
- Hierarchical structures

### Step 2: Structure Design

**Three-Column Layout:**

| Column | Content Types | Purpose |
|--------|--------------|---------|
| **Left** | Applications, reflections, methodology, interview prep | Applied knowledge and thinking |
| **Center** | Core themes, architecture, comparisons, discussions | Central content flow |
| **Right** | Technical mechanisms, frameworks, tools, concepts | Technical implementation details |

**Layout Principles:**
- **Vertical flow is primary** - Content should flow from top to bottom within each column
- **Cross-column connections are flexible** - Don't restrict relationships between columns
- **Center column anchors the layout** - Core theme and main content go here
- **Visual hierarchy** - Most important content at the top, details below

**Coordinate System:**
```
Source file:    x=400,  y=-1400
Core theme:     x=400,  y=-800
Left column:    x=-1200
Center column:  x=400
Right column:   x=2000
```

**Spacing:**
- Vertical spacing between cards in same column: 500-800
- Horizontal spacing between columns: 1600

### Step 3: Canvas Generation

**Create Nodes:**

1. **Source file node** (type: file)
   - Position: Top center
   - Links to the original md file
   - Label: "原始内容"

2. **Core theme node** (type: text)
   - Position: Below source file
   - Contains: Main topic, keywords, content tags, status
   - Color: Red (1)

3. **Topic nodes** (type: text)
   - Distribute across three columns based on content type
   - Card size: width 800-1100, height 500-900
   - Extract key content for each topic
   - Use appropriate colors

**Color Coding:**
- **Red (1)**: Core theme
- **Blue (2)**: Technical architecture
- **Purple (3)**: Methodology/applications
- **Orange (4)**: Analysis/comparisons
- **Green (5)**: Projects/mechanisms
- **Cyan (6)**: Technical concepts

**Create Edges:**

**Within columns (vertical - primary flow):**
- Connect cards from top to bottom
- Use logical connections (e.g., "深度思考", "架构详解", "实现方式")
- These form the main reading path

**Between columns (cross-column - flexible):**
- Technical support relationships
- Influence relationships
- Comparison relationships
- Containment relationships
- **Don't limit the number** - allow rich interconnections
- Ensure connections have clear logical justification

**Edge Format:**
```json
{
  "id": "unique-edge-id",
  "fromNode": "from-node-id",
  "fromSide": "top/bottom/left/right",
  "toNode": "to-node-id",
  "toSide": "top/bottom/left/right",
  "label": "relationship description"
}
```

### Step 4: Optimization and Refinement

**Checklist:**
- [ ] Canvas file can open without JSON errors
- [ ] Three-column structure is visually clear
- [ ] Main flow is vertical (top to bottom)
- [ ] Cross-column connections are rich but not chaotic
- [ ] Card sizes are appropriate for readability
- [ ] Edge labels describe relationships clearly
- [ ] No vertical line overlaps (same x coordinate conflicts)
- [ ] Logical flow makes sense

**Common Adjustments:**
- Adjust card positions if lines cross awkwardly
- Split overly large cards into multiple smaller ones
- Merge redundant content
- Add missing connections users might expect
- Simplify overly complex edge layouts

## Output Format

**File Location:** Same directory as the source md file

**File Name:** `{date}.canvas` (e.g., `2026-04-24.canvas`)

**File Structure:**
```json
{
  "nodes": [
    {
      "id": "unique-id",
      "type": "text" or "file",
      "text": "markdown content",
      "file": "path/to/file.md",  // for type=file only
      "x": 0,
      "y": 0,
      "width": 800,
      "height": 600,
      "color": "1"
    }
  ],
  "edges": [
    {
      "id": "unique-edge-id",
      "fromNode": "from-node-id",
      "fromSide": "top",
      "toNode": "to-node-id",
      "toSide": "bottom",
      "label": "relationship"
    }
  ]
}
```

## Key Principles

**1. Flexibility Over Rigidity**
- Don't strictly enforce column independence
- Allow rich cross-column connections
- Let the knowledge network be interconnected

**2. Visual Clarity**
- Primary flow should be vertical
- Avoid line crossings when possible
- Use clear visual hierarchy

**3. Extensibility**
- Leave room for adding more nodes
- Design layout to accommodate future content
- Keep structure flexible for modifications

**4. User-Friendly**
- Card sizes should be readable
- Text should be concise but complete
- Labels should describe relationships clearly

**5. Logical Consistency**
- Every connection should have a clear reason
- Avoid arbitrary connections
- Respect the content's inherent structure

## Success Criteria

A successful canvas should:
- ✅ Open without JSON errors in Obsidian
- ✅ Have a clear three-column structure
- ✅ Show logical vertical flow
- ✅ Have meaningful cross-column connections
- ✅ Help users quickly understand content structure
- ✅ Reveal relationships between topics
- ✅ Be visually balanced and readable

## User Interaction Pattern

1. User provides inbox md file path
2. You analyze content and generate canvas
3. User reviews the canvas
4. User provides feedback on:
   - Layout adjustments (move cards, resize, etc.)
   - Missing connections
   - Content organization
   - Card grouping
5. You iterate based on feedback
6. Final canvas is created

**Always ask for user feedback** before considering the task complete. Users may want to adjust:
- Column assignments
- Card positions
- Connection relationships
- Content organization
- Visual hierarchy
