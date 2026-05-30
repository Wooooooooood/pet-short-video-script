---
name: pet-short-video-script
description: Generate structured short video scripts for cute/funny pet content optimized for AI video generation tools like Seedance 2.0. Use when the user wants to create pet short videos, cute animal clips, funny pet skits, heartwarming pet stories, pet vlogs, or any short-form video content featuring animals/pets. Core triggers (萌宠视频, 宠物短视频, 萌宠脚本, pet video script, cute pet video, funny pet short, 搞笑萌宠, 治愈系宠物, AI pet video, Seedance pet). Also responds to requests to write/direct pet-focused short videos with shot breakdowns. Supports multi-round dialogue to refine story completeness and outputs production-ready storyboards with English prompts for Seedance 2.0, Kling, Veo, and other T2V/I2V models.
---

# Pet Short Video Script Generator

Generate complete, production-ready short video scripts for cute and funny pet content. Output includes full storyboard with English prompts optimized for Seedance 2.0 and other AI video generation models.

## Workflow Overview

The process follows 4 phases. Guide the user through each sequentially. Do not skip phases unless the user provides all information upfront.

```
Phase 1: Collect pet character profile
Phase 2: Gather story concept & direction
Phase 3: Ask clarifying questions to fill gaps
Phase 4: Generate full storyboard with Seedance prompts
```

## Quick Start

New users may not know how to begin. Here's a typical interaction flow:

**User says:** "我想给我家柯基拍个搞笑短视频" / "帮我写一个宠物视频脚本" / "pet video script for my cat"

**System response:** Enter Phase 1. Ask 1-2 conversational questions to collect the pet profile (breed, name, appearance, personality). Do not dump the entire requirement list at once.

**Example first reply:**
> 好呀！给柯基拍搞笑短视频一定超可爱 🐶 先跟我聊聊你家毛孩子——它叫什么名字？毛色和外观有什么特别的地方吗（比如围脖、配色）？性格是戏精型还是呆萌型？

---

## Phase 1: Pet Character Profile Collection

Collect the following information. Ask in a conversational way (not as a questionnaire). Group related items into 2-3 natural questions.

**Required fields:**
- **Pet species/breed** (e.g., golden retriever, British shorthair, corgi)
- **Pet name**
- **Visual appearance** (colors, markings, distinctive features, size)
- **Personality traits** (e.g., mischievous, lazy, dramatic, clingy, bossy)
- **Signature behaviors** (habitual actions that define the character)

**Optional but helpful:**
- **Reference photo** (uploaded image for I2V character consistency)
- **Wardrobe/props** (collar, costume, favorite toy, accessories)
- **Age** (puppy/kitten vs adult affects energy and story options)

Store collected info in a character profile block. Confirm with user before proceeding.

**Before proceeding to Phase 2, perform a consistency check:**
- Verify that the breed/species matches the visual description (e.g., a "golden retriever" should not be described as having short legs and a flat face). If there's a mismatch, use this exact message format:
  > ⚠️ **信息确认**：你提到品种是 **[breed]**，但外观描述里的 **[feature]** 不太像这个品种的典型特征（比如金毛通常是长腿、垂耳）。它是不是混血的？我们以哪个描述为准？
- If the user says "I don't know the breed" or "it's a mix," use `mixed-breed` with their visual description as the primary subject lock.

---

## Phase 2: Story Concept Collection

Collect the story concept through natural conversation. Cover:

1. **Story premise** - What happens? One sentence summary.
2. **Tone/style** - Funny/contrast? Heartwarming? Prank? Revenge? Cozy daily?
3. **Target platform** - TikTok/Reels (vertical 9:16) vs YouTube Shorts (9:16) vs Xiaohongshu (varies)
4. **Target duration** - 15s, 30s, or 60s (default 30s if unspecified)
5. **Any specific scenes or moments** the user already envisions
6. **Ending type** - Twist? Warm resolution? Punchline? Cliffhanger?

If the user only has a vague idea, reference `references/story-templates.md` for proven pet story frameworks and suggest 2-3 template options that fit their direction.

**If the user says "I don't know" or "you decide":**
- Skip detailed questioning. Based on the pet's personality from Phase 1, auto-select 2 recommended templates (one funny, one heartwarming).
- Present brief summaries and ask: "这两个方向你觉得哪个更有趣？或者我们可以融合一下。"
- **System message template when making the choice for user:**
  > ✅ **帮你拍板**：基于 **[pet name]** **[personality trait]** 的性格，我选了 **"[Template Name]"** 方向——[one-sentence summary]。如果你另有想法，随时告诉我！

**Before proceeding to Phase 3, perform a completeness check:**
- Ensure tone and ending type are compatible. If there's a mismatch, use this message:
  > ℹ️ **小提醒**：你选了 **[tone]** 风格 + **[ending]** 结局，这个组合比较特别，可能会产生有趣的反差效果。如果想调整，告诉我；没问题的话我们就继续！
- Flag any contradictions in platform vs duration (e.g., 60s on TikTok is less common). Suggest but do not block.

---

## Phase 3: Clarifying Questions (Gap-Filling)

Analyze the character profile + story concept for missing or weak elements. Ask **2-4 targeted questions** to strengthen the narrative before writing.

**Common gaps to check:**

| Gap Type | Example Question |
|----------|-----------------|
| Motivation | "Why does [pet name] want to do X? What's the trigger?" |
| Conflict stakes | "What happens if the pet fails? What's at risk?" |
| Human role | "Is there an owner involved? How do they react?" |
| Setting | "Where does this take place? Living room? Park? Kitchen?" |
| Emotional beat | "Should the audience laugh, go 'aww', or be surprised at the end?" |
| Visual hook | "What's the first thing viewers see? What stops the scroll?" |

**Rules for this phase:**
- Maximum 4 questions per round
- Group related questions together
- If user answers create new gaps, do one follow-up round (max 2 rounds total)
- Acknowledge user answers and confirm story direction before proceeding

**Handling invalid or uncooperative responses — use these exact message templates:**

| Situation | System Response |
|-----------|----------------|
| **User refuses to answer** (e.g., "不想说了" / "太麻烦了") | "没关系，那我们基于已有信息继续 🐾 我先用 **[默认值]** 来填补，生成后你随时可以再调整。" |
| **User gives nonsense/irrelevant answer** (first time) | "这个问题是想了解 **[具体目的]** ——比如你家 **[pet name]** 平时是活泼好动还是懒洋洋的？简单说说就好 😊" |
| **User gives nonsense/irrelevant answer** (second time) | "好的，这个字段我先标记为未指定，用默认值继续。后面如果想补充，随时告诉我！" |
| **User says "随便" / "都行"** | "那我帮你选 **[具体选择]**，适合 **[pet name]** **[性格特征]** 的特点。选好了，我们继续！" |

**Key rule:** Always announce what default value or creative choice you are using, so the user knows what happened and can correct it later.

---

## Phase 4: Full Storyboard Generation

> 💡 **给用户的话（在输出分镜前主动展示）**：
> 接下来我将为你生成完整的分镜脚本。每个镜头会附带一段 **英文画面提示词** ——这些提示词会自动翻译好，你**不需要理解每个单词**，直接复制粘贴到 Seedance 2.0、Kling、Veo 等 AI 视频工具即可生成画面。如果你想了解某句提示词的中文意思，随时问我！

Generate a complete storyboard with the following structure. Always output in this format.

### Output Structure

```markdown
# 《[Video Title]》 — 萌宠短视频分镜脚本

## Project Info
- **Pet Character**: [Name] ([Breed])
- **Duration**: [X]s
- **Format**: [9:16 / 16:9 / 1:1]
- **Tone**: [Funny / Heartwarming / Contrast / etc.]
- **Total Shots**: [N]

## Character Consistency Lock
```
[Subject description block - identical across all Seedance prompts]
```

## Storyboard

### Shot [N] | [Scene Name]
- **Timestamp**: 00:00 - 00:XX
- **Duration**: Xs
- **Shot Type**: [景别]
- **Camera**: [运镜方式]

**画面描述**: [中文场景描述]

**台词/字幕**: [如有]
**音效提示**: [BGM/音效]

**Seedance Prompt** (EN):
```
[Shot type], [subject with visual details], [primary action], [environment], [camera movement], [lighting], [visual style], [aspect ratio]
```
---
```

### Shot Template Details

Each shot MUST include:

1. **Timestamp** - Cumulative timeline
2. **Duration** - Per shot (sum = target duration)
3. **Shot Type** - Choose from: 特写/近景/中景/全景/远景
4. **Camera** - Movement + framing. See `references/shot-techniques.md` for full options
5. **画面描述** - Chinese visual description for human reference
6. **台词/字幕** - On-screen text or dialogue (if applicable)
7. **音效提示** - Sound/BGM direction
8. **Seedance Prompt** - English prompt following the formula below

### Seedance Prompt Formula

Follow this structure for every Seedance prompt. Keep each prompt **40-80 words**:

```
[Shot type], [subject description with character consistency], [primary action], [secondary motion], [environment/scene], [camera movement], [lighting], [visual style], [aspect ratio]
```

**Character Consistency Rule:**
- Create one master subject description from Phase 1 profile
- Repeat it identically (or with minimal variation) in every shot prompt
- Add "maintain exact appearance across shots, preserve character design" for character-locked sequences

**Timing Guidelines by Duration:**

| Duration | Shots | Structure |
|----------|-------|-----------|
| 15s | 3-4 | Hook(3s) → Action(7s) → Punchline(5s) |
| 30s | 5-7 | Hook(3s) → Setup(8s) → Build-up(10s) → Climax(5s) → Outro(4s) |
| 60s | 7-10 | Full 4-act structure (see story-templates.md) |

**Seedance prompt requirements:**
- Start with shot type (critical for Seedance interpretation)
- One primary action per prompt; add one secondary motion max
- Describe motion concretely: "tail wagging slowly" not "happy tail"
- Include negative constraints when needed: `no human hands visible, no text overlay`
- Aspect ratio must match target platform (9:16 for TikTok/Reels)

**Phase 4 Error Detection — during generation, watch for these issues and alert the user:**

| Issue Type | Detection | System Message |
|------------|-----------|----------------|
| **Character drift** | Subject description varies by >20% between shots | ⚠️ **角色一致性警告**：检测到第 [N] 个镜头的宠物描述与其他镜头不一致。已自动修正为统一描述。 |
| **Prompt too long** | Seedance prompt exceeds 80 words | ⚠️ **提示词过长**：第 [N] 个镜头的提示词超出 80 词，Seedance 可能理解不全。已精简为：[shortened version] |
| **Missing sound direction** | Any shot lacks 音效提示 | ⚠️ **音效缺失**：第 [N] 个镜头缺少音效提示。已补充：[suggestion] |
| **Timing mismatch** | Sum of shot durations ≠ target duration | ⚠️ **时长不匹配**：各镜头时长总和为 [X]s，与目标 [Y]s 不符。已调整为：[corrected breakdown] |
| **Platform ratio error** | Aspect ratio doesn't match platform | ⚠️ **比例错误**：目标平台是 [platform]，应使用 [ratio]。已修正。 |

---

## Critical Rules

1. **Always write Seedance prompts in English** - even if all other content is Chinese. AI video models interpret English prompts more reliably.
2. **Maintain character consistency** - the subject description must be identical across all shot prompts. Vary only shot type, action, and camera.
3. **One camera move per shot** - never combine multiple camera movements in one Seedance prompt.
4. **Iterate one variable per shot** - if changing perspective, keep lighting/style constant.
5. **Max 2 rounds of clarifying questions** - don't over-question; fill critical gaps and proceed.
6. **Default to 30s duration** if user doesn't specify; use 5-7 shots.
7. **Include sound direction** for every shot - Seedance 2.0 supports audio generation cues.

---

## Troubleshooting & FAQ

All problem-solving guidance in one place. When something goes wrong, refer to this section.

### FAQ — Common Questions

**Q: 为什么 Seedance 提示词必须用英文？**  
A: 当前主流 AI 视频模型（Seedance 2.0、Kling、Veo 等）对英文提示词的理解精度和生成稳定性显著高于中文。你的**输入和对话完全可以用中文**，系统只会在最终的分镜脚本里把画面提示词自动翻译成英文，你不需要动手翻译，也不需要看懂每个单词。

**Q: 我看不懂英文提示词怎么办？**  
A: 提示词是写给 AI 视频模型看的，不是写给你看的。你只需要复制粘贴到 Seedance 等工具即可。如果你好奇某句的意思，随时问我，我会逐句翻译给你。

**Q: 我没有宠物照片，还能用吗？**  
A: 完全可以。照片仅用于 I2V（图生视频）角色一致性锁定，是可选的。用文字详细描述宠物的外观（毛色、花纹、体型、五官特征）同样能生成高质量的脚本。

**Q: 可以生成猫狗以外宠物的脚本吗？（兔子、仓鼠、鹦鹉等）**  
A: 可以。系统支持所有常见宠物。对于小众宠物，会在镜头技巧中自动调用对应的拍摄建议（如仓鼠用宏观特写+超大比例道具，鸟类用飞行追踪等）。

**Q: 生成的脚本不满意，怎么修改？**  
A: 你可以要求：① 调整单个镜头的景别或运镜；② 修改故事走向或结局；③ 更换故事模板；④ 调整时长和节奏。提出具体修改点，系统会保留已有设定并局部更新。

**Q: 必须走完 4 个阶段吗？可以快速生成吗？**  
A: 如果你一次性提供了宠物的完整信息+故事方向，系统会直接跳到 Phase 4 生成分镜，不需要逐步问答。你也可以随时说"直接生成"，系统会用默认值补齐缺失信息。

**Q: 同一个宠物可以生成多个不同故事的脚本吗？**  
A: 当然可以。Phase 1 的宠物档案会被保留，你可以基于同一个角色连续生成多个不同故事，保持角色外观一致的同时尝试各种剧情。

---

### Input Problems — When User Input Goes Wrong

**User refuses to provide key information**

| Missing Field | Fallback Value | Message to User |
|---------------|----------------|-----------------|
| Breed/species | `a cute fluffy pet` (derived from appearance) | "不确定品种没关系，看起来像什么？（比如大型犬、短毛猫、长毛猫）" → 仍不回答则用 fallback 并告知："好的，我先按 **[描述]** 来设定，后面可以再改。" |
| Appearance | Breed-typical features from `references/seedance-prompt-guide.md` | "没有外观描述的话，我先用 **[品种]** 的典型特征来写。如果你想补充特别的花纹或标记，随时说！" |
| Personality | Young=`playful and curious`; Senior=`calm and lazy`; Unknown=`mischievous and expressive` | "还没了解性格的话，我先用 **[默认值]** 来推进。生成后如果感觉不对，告诉我真实的性格，我立刻调整！" |
| Story direction | Auto-select 2 templates based on pet personality | "故事方向我来帮你选——基于 **[pet name]** 的性格，推荐 **[模板A]** 和 **[模板B]**。喜欢哪个？" |

**Contradictory or nonsensical input**

| Severity | Example | System Response |
|----------|---------|-----------------|
| Mild | Tone + ending mismatch | "ℹ️ 你选了 **[tone]** + **[ending]**，这个组合会产生有趣的反差效果。如果想调整告诉我，没问题的话我们继续！" |
| Severe | Breed ≠ appearance | "⚠️ **信息确认**：你提到品种是 **[breed]**，但 **[feature]** 一般不是这个品种的特点。它是不是混血的？我们以哪个为准？" |
| Nonsense | Pet = "微波炉" | "哈哈，微波炉成精确实很有创意 🎛️ 我们还是先回到现实——它是什么小动物呢？🐱🐶" → 仍坚持则退出："这个创意太超前了，我目前只擅长现实里的宠物。换个真实的毛孩子我们再继续？" |

**Information too vague**
- Do not ask 10 questions at once.
- Use this opening: "好呀！先告诉我——是什么宠物？狗狗还是猫咪？大概什么品种或者长什么样？"
- Extract one piece of information per reply.

---

### Generation Problems — When Output Goes Wrong

**Detect and auto-fix these issues during Phase 4, with clear user alerts:**

| Issue | Detection Rule | Auto-Fix | Alert Message |
|-------|---------------|----------|---------------|
| **Character description drift** | Subject text differs by >20 words between any two shots | Replace with the Phase 1 master description | ⚠️ **角色一致性修正**：第 **[N]** 镜头的宠物描述与其他镜头不一致，已统一为初始设定。 |
| **Prompt too long** | >80 English words in any Seedance prompt | Trim secondary motions / environment details | ⚠️ **提示词精简**：第 **[N]** 镜头提示词过长，已精简为 **[X]** 词，不影响核心画面。 |
| **Timing mismatch** | Sum of shot durations ≠ target duration | Redistribute ±1s to nearest shots | ⚠️ **时长校准**：镜头总时长 **[X]s** 与目标 **[Y]s** 不符，已自动调整为正确分配。 |
| **Missing sound cue** | Any shot lacks 音效提示 | Add platform-appropriate default BGM/sfx | ⚠️ **音效补充**：第 **[N]** 镜头已补充 **[BGM/sfx 建议]**。 |
| **Wrong aspect ratio** | Ratio doesn't match platform default | Replace with correct ratio tag | ⚠️ **画幅修正**：**[platform]** 应用 **[ratio]**，已调整。 |

---

## Reference Files

- `references/seedance-prompt-guide.md` - Complete Seedance 2.0 prompt vocabulary, shot types, camera moves, lighting styles, and negative constraint examples. Read when generating Phase 4 prompts.
- `references/story-templates.md` - Proven pet story frameworks (funny contrast, heartwarming, prank, revenge, cozy daily) and template mixing strategies. Read when user needs story ideas in Phase 2.
- `references/shot-techniques.md` - Shot type selection guide, camera vocabulary, and pet-specific filming tips. Read when constructing shot descriptions.
