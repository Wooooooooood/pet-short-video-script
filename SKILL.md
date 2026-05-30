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
- Verify that the breed/species matches the visual description (e.g., a "golden retriever" should not be described as having short legs and a flat face). If there's a mismatch, gently ask: "你提到品种是[breed]，但外观描述里的[feature]不太像这个品种的典型特征，能确认一下吗？"
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

**Before proceeding to Phase 3, perform a completeness check:**
- Ensure tone and ending type are compatible (e.g., a "prank" tone with a "warm resolution" ending is unusual but possible; note it and proceed unless user clarifies otherwise).
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

**Handling invalid or uncooperative responses:**
- **User refuses to answer** (e.g., "不想说了" / "太麻烦了"): Acknowledge, say "没关系，那我们基于已有信息继续" and proceed to Phase 4 using available info + smart defaults.
- **User gives nonsense/irrelevant answers** (e.g., 问宠物性格答 "今天天气很好"): Gently redirect once: "这个问题是想了解[具体目的]——比如你家[pet name]平时是活泼好动还是懒洋洋的？" If still irrelevant after one retry, mark field as "not specified" and proceed.
- **User says "随便" / "都行"**: Make a confident creative choice based on the pet profile and announce it ("那我帮你选一个温馨日常风，适合[pet name]的性格").

---

## Phase 4: Full Storyboard Generation

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

## Error Handling & Edge Cases

When the user's input deviates from the expected flow, follow these recovery rules:

### User Refuses to Provide Key Information
If the user declines to answer a required field (breed, appearance, personality), do not insist. Use these fallbacks and proceed:

| Missing Field | Fallback Strategy |
|---------------|-------------------|
| Breed/species | Ask once: "不确定品种没关系，看起来像什么？（比如大型犬、短毛猫、长毛猫）" If still declined, use `a cute fluffy pet` and derive from appearance description. |
| Appearance | Use breed-typical features from the breed database in `references/seedance-prompt-guide.md`. If breed is also unknown, ask for a photo or use `mixed-breed with fluffy fur and round eyes`. |
| Personality | Default to `playful and curious` for young pets, `calm and lazy` for senior pets. If age unknown, default to `mischievous and expressive`. |
| Story direction | Auto-suggest 2 templates from `references/story-templates.md` based on pet personality. |

### Contradictory or Nonsensical Input
If the user provides information that is logically inconsistent:
- **Mild contradiction** (e.g., tone and ending mismatch): Note it silently, proceed, and let the combination create an interesting twist.
- **Severe contradiction** (e.g., breed and appearance completely mismatch): Ask one clarifying question with specific examples: "你提到是[breed]，但[feature]一般不是这个品种的特点，它是不是混血的？"
- **Nonsensical input** (e.g., pet species = "微波炉"): Treat as a joke, respond lightly: "哈哈，如果它是微波炉成精那确实很有创意！我们还是先回到现实——它是什么小动物呢？🐱🐶" If user persists with nonsense, exit gracefully: "这个创意太超前了，我目前的专长是现实里的猫猫狗狗。换个真实的宠物我们再继续？"

### Information Too Vague to Proceed
If all user provides is something like "帮我写个宠物脚本" with no details:
- Do not ask 10 questions at once.
- Ask **one** opening question with embedded options: "好呀！先告诉我——是什么宠物？狗狗还是猫咪？大概什么品种或者长什么样？"
- Use their answer to trigger the next most relevant question.

---

## Reference Files

- `references/seedance-prompt-guide.md` - Complete Seedance 2.0 prompt vocabulary, shot types, camera moves, lighting styles, and negative constraint examples. Read when generating Phase 4 prompts.
- `references/story-templates.md` - Proven pet story frameworks (funny contrast, heartwarming, prank, revenge, cozy daily) and template mixing strategies. Read when user needs story ideas in Phase 2.
- `references/shot-techniques.md` - Shot type selection guide, camera vocabulary, and pet-specific filming tips. Read when constructing shot descriptions.

---

## FAQ

**Q: 为什么 Seedance 提示词必须用英文？**  
A: 当前主流 AI 视频模型（Seedance 2.0、Kling、Veo 等）对英文提示词的理解精度和生成稳定性显著高于中文。你的输入和对话完全可以用中文，系统只会在最终的分镜脚本里把画面提示词翻译成英文，不需要你动手。

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
