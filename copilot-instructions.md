# Chronicles of the Sovereign Door
## VS Code + GitHub Copilot — Complete Setup & Prompt Guide

---

## ✅ Yes — Fully Portable to VS Code + GitHub Copilot

Everything built in this session transfers directly. Your GDD and Story Scripts are HTML documents — they can be placed in your project repo, read by Copilot via `#file` references, and used as context for every writing and coding task. Copilot Chat, Copilot Edits, and Agent Mode all work with this project.

**What Copilot can do for this project:**
- Continue writing Vol. III arcs and heroine routes in the established style
- Generate game engine code (Next.js visual novel engine, dialogue system, save/load)
- Build relationship tracker, choice flag system, CG gallery
- Write JSON scene schemas from your existing script format
- Draft issue templates, PR descriptions, and arc planning docs
- Refactor and expand any existing arc or heroine profile

---

## 📥 All Project Documents

Download these and place them in your repo under `/docs/`:

| Document | URL | Description |
|---|---|---|
| **GDD v0.3** | https://www.genspark.ai/api/files/s/pno41Bhh | Full Game Design Document — all 20 heroine profiles, world lore, systems |
| **Story Script Vol. II** | https://www.genspark.ai/api/files/s/n3LzNkWc | Complete script — Arcs 2–8, all route confirmations, Vol. II finale |

---

## 📁 Recommended Repository Structure

```
chronicles-sovereign-door/
│
├── .github/
│   ├── copilot-instructions.md        ← CRITICAL: paste full content below
│   ├── ISSUE_TEMPLATE/
│   │   ├── arc-tracking.md
│   │   ├── heroine-route.md
│   │   └── bug-report.md
│   └── workflows/
│       └── ci.yml
│
├── docs/
│   ├── gdd-v03.html                   ← GDD download
│   ├── script-vol2-complete.html      ← Story Script Vol. II
│   ├── arc-status.md                  ← Arc completion tracker
│   └── heroine-route-tracker.md       ← Route status per heroine
│
├── writing/
│   ├── vol3-the-war/
│   │   ├── arc9-outline.md
│   │   ├── arc9-script.md
│   │   └── arc10-script.md
│   ├── heroine-deep-routes/
│   │   ├── stella-deep-arc.md
│   │   ├── yuna-seiran-arc.md
│   │   ├── saki-shrine-arc.md
│   │   ├── tsuki-possession-arc.md
│   │   └── rabbit-personal-arc.md
│   ├── late-heroines/
│   │   ├── aria-intro.md
│   │   ├── lyra-intro.md
│   │   ├── nora-intro.md
│   │   ├── vera-intro.md
│   │   ├── xiaomei-intro.md
│   │   └── isolde-intro.md
│   └── bond-events/
│       └── [heroine]-bond-[arc].md
│
├── src/
│   ├── app/                           ← Next.js app router
│   │   ├── page.tsx                   ← Title screen
│   │   ├── game/
│   │   │   └── page.tsx               ← Main game view
│   │   └── gallery/
│   │       └── page.tsx               ← CG gallery
│   ├── components/
│   │   ├── DialogueBox.tsx
│   │   ├── ChoiceMenu.tsx
│   │   ├── RelationshipTracker.tsx
│   │   ├── SceneRenderer.tsx
│   │   ├── BGLayer.tsx
│   │   ├── CharacterSprite.tsx
│   │   └── CGViewer.tsx
│   ├── engine/
│   │   ├── sceneEngine.ts
│   │   ├── flagEngine.ts
│   │   ├── saveSystem.ts
│   │   └── audioEngine.ts
│   ├── data/
│   │   ├── scenes/
│   │   │   ├── arc1/
│   │   │   ├── arc2/
│   │   │   └── arc3/
│   │   ├── heroines.ts
│   │   └── flags.ts
│   └── types/
│       ├── scene.ts
│       ├── heroine.ts
│       └── gameState.ts
│
├── public/
│   ├── backgrounds/
│   ├── sprites/
│   ├── cg/
│   └── audio/
│
├── package.json
├── tsconfig.json
├── tailwind.config.ts
└── README.md
```

---

## 🤖 `.github/copilot-instructions.md`

**Create this file exactly as shown. This is the most important file — Copilot reads it automatically for every chat and edit session.**

```markdown
# Chronicles of the Sovereign Door — Copilot Instructions

## Project Overview
- **Title:** Chronicles of the Sovereign Door
- **Genre:** Visual Novel / RPG hybrid — Japanese contemporary setting + isekai fantasy world
- **Studio:** Internal (confidential)
- **Version:** Vol. II complete (Arcs 1–8), Vol. III in progress
- **Engine Target:** Next.js + React web-based VN engine, TypeScript throughout

---

## Protagonist

**KAITO AMANE** — Male, 17, Seiran Academy Year 2 transfer student.

- Personality: Gentle, formal speech register, oblivious to romance as self-protection
- Core trait: Cooking as an act of trust; never abandons someone in danger
- Anger: Rare — only 3 instances across all arcs; when it appears, it is quiet and absolute
- Background: Inherited house from grandfather Hiroshi; discovered the Door (a portal to Argena)
- Skills: Argena Cheat Skills (physical enhancement, Taming), wire-class combat training (from Shira)
- Narrator voice: First-person, dry observational humor, precise emotional honesty, never melodramatic
- Key quote style: "I find that I am not afraid. I find that this is what it feels like when you are not alone in something enormous."

---

## The Two Worlds

### Earth — Tokyo, Seiran Ward
- Seiran Academy: elite private high school, primary social hub
- Amane House: inherited from grandfather; the Door is in the basement
- Key locations: Hayashi Restaurant, Haruno Estate, Star Agency, Bureau Satellite Office

### Argena — The Other World
- Accessed through the Door (glows gold when stable, red during Convergence/war)
- Great Weald: ancient iron-wood forest adjacent to the Door
- Red Moon Desert: southeast of the Weald; rock formations that glow like embers at dusk
- Kingdom of Astraea: Elia's home nation; currently at war with the Evil Trio
- Kingdom of Soleil: Stella Edgeblade's domain; Saint Order headquarters
- Argena sky runs red at dusk; the world has its own magnetic system and navigation script

---

## All 20 Heroines

### CORE TIER (Earth)
1. **Airi Haruno** — Chairman's daughter; reorganizes Kaito's life with quiet precision; route confirmed Arc 8
2. **Sora Mizuki** — Top model; never truly seen beyond her fame; route confirmed Arc 4
3. **Hana Kazato** — Track star; childhood wound around body image; route confirmed Arc 5
4. **Yui Shinohara** (Morishita in some refs) — Analyst/teaser; notebook of observations; route confirmed Arc 7
5. **Natsume Aoyagi** — 28yo teacher; drunk proposal Arc 3; route confirmed Arc 8 (7-month arc pending)

### CORE TIER (Argena/Cross-world)
6. **Shira (Shirogane Seira)** — Wire-class assassin; former Guild; route deepened Arc 6/8; Vol. III payoff
7. **Elia Von Astraea** — Princess; proposed in Arc 1; now coordinating Argena war; route milestone Arc 8
8. **Reina Kurohane** — Half-demon heir; reads residual intent in spaces; route confirmed Arc 7
9. **Nito** — Desert scout; guilt over friend Emma's injury; route confirmed Arc 6; Emma arc pending
10. **Akemi Kuroda** — Bureau Director; off-protocol from Arc 7; route confirmed Arc 7; Bureau reform arc pending

### MID TIER
11. **Stella Edgeblade** — Sword Saint; proposed in Arc 3; deep route unwritten
12. **Yuna** — Former Fallen Saint; Seiran Junior High; deep route unwritten
13. **Saki Miyashiro** — Shrine maiden; accidentally summoned to Argena; zero script written
14. **Tsuki Shiroiwa** — Occult club; gradual possession arc with Saki; zero script written
15. **Rabbit** — Kick Saint; group coach; ships everyone; personal route unwritten

### LATE TIER
16. **Aria** — Lost arm protecting beast-children; one-arm warrior; no script
17. **Lyra de Soleil** — Mage Princess of Soleil; no script
18. **Nora Frosia** — Ice/cold archetype; no script
19. **Vera** — Alien engineer; crash-lands at Amane House; confesses after 73 days; no script
20. **Isolde Fairhaven** — Island Seer; protects Halwa Island; meets Kaito at shoreline; no script

**Also: Xiaomei** (Dragon Princess; curse removed during Lianxi succession arc) — Late tier, no script

---

## Key Factions

- **Guild of Darkness:** Shira's former employer; Wire-class assassins; fractured after Shira's severance; Vael now allied
- **Evil Trio:** Three corrupted humans wielding Void energy; collect Saints; have made direct Earth move; core members unnamed
- **Special Infrastructure Monitoring Bureau:** Japanese government anomaly agency; Akemi Kuroda is Director; now partnered with Kaito
- **Saint Order:** Rabbit, Stella, Yuna, Bow Saint (deceased/captured); fighting the Evil Trio
- **Kingdom of Astraea:** Elia's nation; eastern provinces fallen; King aware of Kaito

---

## Support Characters

- **Ryuusei Hayashi** — Best friend; confidant maxed Arc 5; knows everything
- **Saya Amane** — Sister, 13; small hurricane; has filled 3 notebooks about Argena; Ryou must be told eventually
- **Ryou Amane** — Brother, 12; careful watcher; does the dishes so Kaito doesn't worry
- **Kage** — Black Fenrir wolf-cub (now large); tamed Arc 1; approves of everyone eventually; resolves conversations by sitting on feet
- **Togashi Ken** — Recovered from Trio Arc 7; logistics; hasn't left the house
- **Vael** — Former Guild unit lead; Allied after Arc 6; in Red Moon Desert
- **Haruto Fujishima** — "Prince of Patisserie"; Kaito's first civilian friend; comic relief
- **General Marat** — Astraea war commander; calibrating his assessment of Kaito

---

## Narrative Style Guide — CRITICAL

### Tone
- Grounded emotional realism with fantasy elements
- Never melodramatic; weight is communicated through restraint
- Comedy through character, never situation humor
- Every character has a want that has nothing to do with Kaito

### Narrator Voice (Kaito)
- First-person; dry, precise, occasionally self-aware
- Uses LOG: entries for Shira observations
- Notices things others don't; files them without comment
- Never over-explains emotions; shows through action/detail
- Example: "This is Shira's version of 'I'm worried about you.' I have learned to translate."

### Dialogue Conventions
- Shira: minimal words, precise, logs everything, self-correction in real-time
- Airi: calibrated, unreadable smiles, acts through logistics
- Yui: analytical framing for everything, jokes that don't land when she's nervous
- Elia: formal register, enthusiastic about Earth culture, uses Argena dialect with Shira
- Sora: professional composure cracking in layers, reverses questions
- Hana: recalculates; never finishes the sentence until she's ready
- Akemi: Bureau-precise, rounding errors she won't admit to, pauses of exact length
- Nito: desert-economy speech; says what she means; silences are meaningful
- Reina: reads rooms; surprised by people who ask about her, not her power
- Natsume: professional armor over genuine warmth; deflects with logistics

### Choice Point Format
Every choice has:
- Three options (A, B, C)
- Each option has a stat outcome (AFFECTION/TRUST +X or BOND +X)
- Each option may set a FLAG: "Name"
- Best response clearly marked
- Route confirmation choices unlock CGs and major flags
- Outcomes should be specific and character-consistent, not generic

### Script Formatting Conventions
```
[BG: Location description] [BGM: "Track Name" — mood descriptor]
[SFX: sound description]
[CG: image description]
[SCENE BREAK: New location]

NARRATOR (KAITO): Italicized internal narration block with class="narrator"

SPEAKER NAME: "Dialogue in quotes."

(Stage directions in italics inside em tags)

CHOICE POINT: Title
A) Option text → STAT +X. Outcome description. FLAG: "Name."
B) Option text → STAT +X. Outcome description.
C) Option text → STAT +X. Outcome description. Best response.
```

### Scene Break Symbol: ⬡
### Arc status indicator: ✦ marks signature/key scenes

---

## Arc Completion Status

| Arc | Title | Status |
|-----|-------|--------|
| Arc 1 | The Door | ✅ Complete (GDD Vol. I) |
| Arc 2 | The Academy | ✅ Complete |
| Arc 3 | The Saints | ✅ Complete |
| Arc 4 | The Model and the Mission | ✅ Complete |
| Arc 5 | Blood and School | ✅ Complete |
| Arc 6 | The Deep Weald | ✅ Complete |
| Arc 7 | The Face You Know | ✅ Complete |
| Arc 8 | Home and War | ✅ Complete — Vol. II Finale |
| Arc 9+ | Vol. III: The War | ❌ Not started |

---

## What Is NOT Written Yet
- Vol. III: The War (Evil Trio full arc, Argena war resolution, Door's true purpose)
- Evil Trio: core members unnamed, no defeat scenes
- Stella deep route, Yuna Seiran arc, Saki arc, Tsuki arc, Rabbit personal route
- Late heroines: Aria, Lyra, Nora, Vera, Xiaomei, Isolde (profiles only, no scripts)
- Heroine endgame routes (all confirmed routes need resolution chapters)
- Nito's Emma reconciliation arc
- Natsume's 7-month arc (graduation → relationship)
- Akemi's Bureau reformation arc
- Shira's full Guild closure arc

---

## Writing Rules
1. Ask "What does this heroine want that has nothing to do with Kaito?" before every scene
2. Kaito's kindness is specific and observed, never performed
3. Kage resolves conversations. This is a rule.
4. Every arc has a Saturday morning kitchen scene or equivalent
5. Choice C is always the best response and always costs something real
6. Shira keeps a LOG. Always in the format: LOG ENTRY [number]: [content]
7. Akemi keeps FIELD NOTEs. Always: FIELD NOTE [number] — [CATEGORY]: [content]
8. Yui's notebook entries are numbered. Entry 78 is the current high-water mark
9. Nobody cries easily. Substitute: "eyes very bright," "voice rougher than intended," "something behind the eyes is very full"
10. The Door shows you where you are already going — not where you want to be
```

---

## ✍️ Writing Prompts — Ready to Paste into Copilot Chat

### Vol. III — The War Arc

```
#file:docs/gdd-v03.html #file:docs/script-vol2-complete.html

I am writing Arc 9 of Chronicles of the Sovereign Door — the opening arc of Vol. III "The War."

Context:
- Arcs 1-8 are complete. Vol. II ended with Kaito stepping through the Door into Argena with his full group.
- The Evil Trio has made their direct move known. Their core three members are not yet named or shown.
- General Marat commands Astraea's forces; he is calibrating his trust in Kaito.
- Elia is coordinating between Astraea's capital and the front line.
- Shira, Nito, Reina, Akemi all crossed through the Door.

Write Arc 9 "The War Arrives" — 8 chapters — following the established script format:
- [BG:] [BGM:] stage directions
- NARRATOR (KAITO) blocks in italic style
- Full dialogue with character voice consistency (see copilot-instructions.md)
- 3-option CHOICE POINT per chapter with stat outcomes and flags
- Signature scene in Ch 4 or 5 (marked ✦)
- One of the Evil Trio named and revealed in Ch 6-7
- Arc complete box with rewards at end

Begin with Chapter 1.
```

---

### Stella Edgeblade — Deep Route Arc

```
#file:docs/gdd-v03.html #file:docs/script-vol2-complete.html

Write the deep route arc for Stella Edgeblade — "The Sword That Wants to Rest."

Character context from GDD:
- Stella is 26, The Sword Saint, trained from age 9, abandoned femininity for mastery
- Emotional wound: fears dying alone; too sharp to be loved normally
- She proposed to Kaito in Arc 3, has been his sword teacher since
- She respects Airi's command presence; views Earth heroines as "competition, but interesting"
- Signature scene already written: "The Declaration"

Write a 6-chapter deep route arc covering:
- Ch 1: Stella's first moment of vulnerability (not about the sword)
- Ch 2: A sparring session where she deliberately loses to test something
- Ch 3: The question she's been carrying since Arc 3 (what does she want beyond mastery?)
- Ch 4 ✦: Signature scene — "The Sword at Rest" — she puts the sword down for one hour
- Ch 5: Crisis — the Evil Trio targets her as a Saint
- Ch 6: Resolution — what she decides her life is for

Match voice: formal, direct, zero metaphor, physically expressive (sword as emotional shorthand).
```

---

### Yuna — Seiran Junior High Arc

```
#file:docs/script-vol2-complete.html

Write Yuna's Earth adaptation arc — "What Is Normal?"

Character context:
- Yuna is a former Fallen Saint; rescued in Arc 3; master was the Bow Saint (captured by Evil Trio)
- Now enrolled at Seiran Junior High
- She is still processing grief and vengeance; Kaito redirected her
- Yui has been explaining Earth customs to her; they are an unexpected pair
- Signature scene: "What Is Friends?" (roof conversation about the meaning of friendship)

Write a 6-chapter arc:
- Ch 1: First week of school; air conditioning confuses her; she tries to hunt in the garden
- Ch 2: Yui's tutoring sessions on Earth culture (calendar, money, pop culture)
- Ch 3: Yuna tries to protect a classmate the Argena way (escalation)
- Ch 4 ✦: Signature scene — she asks Kaito what friends are and why they hurt when they leave
- Ch 5: News about her master's location (Trio holding her); Yuna's choice to trust the group
- Ch 6: Resolution — she decides what she is now that she is not the Fallen Saint

Yuna's voice: clipped, declarative, literal. No idiom. "I do not understand why this is called a test if no one will die."
```

---

### Saki Miyashiro — Shrine Maiden Arc

```
#file:docs/gdd-v03.html

Write Saki Miyashiro's introduction and arc — "The Accidental Holy Maiden."

Character context from GDD:
- Shrine maiden; accidentally summoned to Argena while performing a ritual
- Aids Kaito in Argena; has genuine spiritual ability that works differently in Argena
- Signature scene: "The Accidental Holy Maiden" — she purifies something she wasn't supposed to

Write:
- A 2-page introduction scene (Earth side: at the shrine, the summoning goes wrong)
- 4-chapter Argena arc (she lands, assesses, helps, chooses to understand rather than flee)
- Ch 4 ✦: Signature scene
- A CHOICE POINT in each chapter
- Her route begins at end of Ch 4

Saki's voice: careful, observational, grounded in ritual logic. Surprised by Argena but not afraid of it. "If something called me here, it had a reason. I would like to understand the reason before I leave."
```

---

### Tsuki Shiroiwa — The Possession Arc

```
#file:docs/gdd-v03.html

Write Tsuki Shiroiwa's arc — "The Possession."

Character context from GDD:
- Occult club member; Heroine #6 MID tier
- Arc: gradual evil possession, exorcism with Saki
- Signature scene: "Everything Is Very Loud" — during the possession, the world is overwhelming

Write a 5-chapter arc:
- Ch 1: Tsuki's introduction — she notices things others don't; she is already slightly wrong
- Ch 2: The possession accelerates; she tries to hide it from Kaito
- Ch 3: Kaito notices (he always notices); confrontation
- Ch 4 ✦: Signature scene — the exorcism attempt with Saki; Tsuki's POV during possession
- Ch 5: Recovery; what she remembers; the route begins

Tsuki's voice: dry, observational, slightly removed from her own experience. "I've been noticing some anomalies in my perception. I don't think they're mine."
```

---

### Late-Tier Heroine Introduction — Vera

```
#file:docs/gdd-v03.html

Write Vera's introduction arc — "The Engineer from Elsewhere."

Character context from GDD:
- Alien engineer; her planet is at war with an AI
- She crash-lands at Amane House
- Confesses love after exactly 73 days (she has been counting)
- Late tier

Write a 3-chapter introduction:
- Ch 1: The crash; Vera emerges from wreckage in the backyard; Saya's response vs. Ryou's response
- Ch 2: Vera assessing Earth technology (horrified by inefficiency); she fixes something in the house that wasn't broken
- Ch 3 ✦: Signature scene — Day 1 of the 73. She explains to Kaito what her counting means in her culture.

A CHOICE POINT in each chapter. Her route begins when the count reaches 73.

Vera's voice: technical, precise, slightly alien cadence. "Your infrastructure is charming in its inefficiency. I will not fix all of it. I will fix the seven most dangerous problems."
```

---

### Bond Event — Heroine Side Story

```
#file:docs/script-vol2-complete.html

Write a Confidant-tier bond event for [HEROINE NAME].

This is a standalone optional scene unlocked after route confirmation. It should:
- Take place in a low-stakes setting (no plot pressure)
- Reveal one thing about the heroine that has nothing to do with Kaito or the main plot
- Have exactly one CHOICE POINT (Kaito's response)
- End with something small that means something large
- Be 3-4 pages in the established script format
- Include stage directions, BGM, and a narrator reflection

Format matches the established Vol. II script style exactly.
```

---

### Argena War Chapter — General Use

```
#file:docs/gdd-v03.html #file:docs/script-vol2-complete.html

Write an Argena war chapter for Vol. III.

Setting: Great Weald / Astraea front line / Red Moon Desert (specify which)
Characters present: [list]
Objective: [tactical / emotional / both]

Requirements:
- Opens with a NARRATOR (KAITO) block establishing the war's current state
- One tactical scene (combat, strategy, or reconnaissance)
- One quiet scene (character moment between major beats)
- CHOICE POINT with three options — tactical choice affects battle outcome, emotional choice affects bond
- Ends with a war-state update (what changed, what it costs)
- No single-note heroism; show the cost of every victory

Tone reference: "The war has a sound here. Distant. Present." — Arc 8 Ch 7
```

---

## 💻 Game Development Prompts

### Scaffold the Visual Novel Engine

```
Create a Next.js 14 visual novel engine for "Chronicles of the Sovereign Door."

Requirements:
- App router (not pages router)
- TypeScript throughout
- Tailwind CSS for styling
- Dark theme matching: bg #0b0d17, accent gold #c5a059, accent crimson #a62639

Core components needed:
1. SceneRenderer — renders background, character sprites, dialogue box
2. DialogueBox — speaker name + text with typewriter effect
3. ChoiceMenu — 3-option choice with flag tracking
4. BGLayer — handles background transitions with fade
5. CharacterSprite — positioned sprite with expression variants

The game state should track:
- currentSceneId: string
- flags: Record<string, boolean>
- affinityScores: Record<string, number> (one per heroine)
- unlockedCGs: string[]
- currentBGM: string
- saveSlots: SaveState[]

Start with the SceneRenderer and DialogueBox components.
```

---

### Scene JSON Schema

```
Design a TypeScript JSON schema for visual novel scenes in Chronicles of the Sovereign Door.

A scene contains a sequence of "beats" which can be:
- dialogue: speaker + text + optional emotion tag
- narration: text (no speaker, italic style)
- stageDirection: text (gold color, small caps)
- background: id + transition type
- music: track id + fade in/out
- sfx: sound id
- choice: array of 3 options, each with text, outcomes (stat changes, flags), and nextSceneId
- cgDisplay: cg id
- sceneBreak: label text

Include TypeScript interfaces for:
- Scene
- Beat (union type of all beat types)
- ChoiceOption
- StatChange
- GameFlag

Also write a parser function that takes a Scene JSON and returns an ordered array of executable beats.
```

---

### Save System

```
Build a save system for the Chronicles VN engine.

Requirements:
- 10 save slots + 1 auto-save slot
- Each save slot stores:
  - timestamp
  - currentSceneId
  - currentChapterTitle
  - screenshotDataUrl (base64 thumbnail)
  - flags: Record<string, boolean>
  - affinityScores: Record<string, number>
  - unlockedCGs: string[]
  - playtime: number (seconds)
- Storage: localStorage for web, with JSON serialization
- Functions: saveGame(slot), loadGame(slot), deleteSave(slot), listSaves(), autoSave()
- Export/import save data as JSON file for backup

Write the full TypeScript implementation with proper error handling.
```

---

### Relationship Tracker Component

```
Build a RelationshipTracker React component for Chronicles of the Sovereign Door.

Display a sidebar or overlay showing:
- All 20 heroines grouped by tier (CORE / MID / LATE)
- Each heroine shows: name, affinity score (0-100), route status badge
- Route status badges: LOCKED / MET / DEVELOPING / CONFIRMED / MAX
- Affinity bar with gold fill color (#c5a059) on dark background (#15192b)
- Clicking a heroine shows: last flag set, last CG unlocked, current arc

Data shape:
interface HeroineStatus {
  id: string
  name: string
  tier: 'CORE' | 'MID' | 'LATE'
  affinity: number
  trust: number
  routeStatus: 'LOCKED' | 'MET' | 'DEVELOPING' | 'CONFIRMED' | 'MAX'
  lastFlag: string | null
  unlockedCGs: string[]
  currentArc: number
}

Make it collapsible. Dark theme. Uses Tailwind. Show a "?" sprite for LOCKED heroines.
```

---

### Combat System — Turn-Based Grid

```
Design and implement the turn-based combat system for Chronicles of the Sovereign Door.

From the GDD:
- 4v4 grid combat (party of 4 vs up to 4 enemies)
- Speed-based initiative (fastest unit acts first)
- Chain-attack detection (adjacent allies can chain)
- MC (Kaito) command set: Attack, Skill, Support, Item, Defend
- 3 playable heroines in combat: Airi (support/buff), Kage (tank/melee), Elia (ranged/magic)

Build:
1. CombatGrid component (4x4 grid, unit placement)
2. InitiativeQueue (speed-sorted turn order)
3. ActionMenu (MC's 5 commands)
4. ChainDetection (checks adjacency, triggers chain animation flag)
5. CombatState (HP, MP, status effects, turn count)
6. 3 sample enemies with basic AI (aggressive, defensive, healer)

TypeScript + React. No external game libraries. Use CSS grid for the battlefield.
```

---

### CG Gallery System

```
Build a CG Gallery system for Chronicles of the Sovereign Door.

Requirements:
- Grid display of all CG slots (locked = dark placeholder with "???" text)
- CGs unlocked via flag: unlockedCGs array in game state
- Each CG has: id, title, heroineId, arcUnlocked, description
- Clicking unlocked CG opens fullscreen viewer with:
  - Previous/Next navigation
  - CG title and heroine name
  - Arc where unlocked
  - Close button (ESC key also closes)
- Filter by heroine (dropdown)
- Count: "X / Y CGs Unlocked"
- Dark theme; gold border on unlocked CGs; crimson border on newly unlocked

Known CGs to pre-populate (from the script):
- "Not the Camera" (Sora, Arc 4)
- "The Garden at Night" (Sora, Arc 4)
- "The Kitchen on Saturday" (All, Arc 5)
- "The Rooftop Declaration" (Shira, Arc 6)
- "The Desert at Dusk" (Nito, Arc 6)
- "The Garden Question" (Reina, Arc 7)
- "The Rooftop Researcher" (Yui, Arc 7)
- "The Wagashi Meeting" (Akemi, Arc 7)
- "The Basement at Dawn" (All, Arc 7)
- "The Garden Lights" (Airi, Arc 8)
- "The Classroom After Hours" (Natsume, Arc 8)
- "The Letter" (Elia, Arc 8)
- "The Saturday of Everything" (All, Arc 8)
- "The Boy Who Kept the Door" (Kaito, Arc 8)

TypeScript + React + Tailwind. Implement with useReducer for gallery state.
```

---

### Choice Engine with Flag Tracking

```
Build the choice engine for Chronicles of the Sovereign Door.

The engine must:
1. Display 3 choice options with fade-in animation
2. On selection: apply all StatChanges (affinity/trust/bond delta per heroine ID)
3. Set all flags listed in the choice outcome
4. Check if any ROUTE CONFIRMATION conditions are met:
   - A route confirms when: affinityScore >= threshold AND specific flag set
   - On confirmation: set routeStatus to 'CONFIRMED', trigger CG unlock, show notification
5. Determine nextSceneId (each option can route differently)
6. Log choice history: choiceId + optionSelected + timestamp

Types needed:
- ChoiceOption: { text, statChanges, flags, nextSceneId, cgUnlock? }
- StatChange: { heroineId, stat: 'affinity'|'trust'|'bond', delta: number }
- RouteConfirmCondition: { heroineId, minAffinity, requiredFlag, cgUnlock, title }

Include a ChoiceHistory log that persists to localStorage so players can review past decisions.

Write the engine as a custom React hook: useChoiceEngine(gameState, dispatch)
```

---

## 🤖 Copilot Agent Mode Tasks

Use these in **Copilot Chat with Agent Mode** (`@workspace`):

```
@workspace Create a new arc script file for Arc 9 in /writing/vol3-the-war/arc9-script.md
following the format established in /docs/script-vol2-complete.html.
Start with the arc header, callout box (focus/heroines/location), and Chapter 1.
```

```
@workspace Convert the Arc 2 script from /docs/script-vol2-complete.html
into JSON scene format matching the schema in /src/types/scene.ts.
Output to /src/data/scenes/arc2/arc2-ch1.json through arc2-ch8.json.
```

```
@workspace Generate a heroine-route-tracker.md in /docs/ listing all 20 heroines,
their tier, route status, arcs they appear in, unwritten arcs, and next steps.
Base data from /docs/gdd-v03.html and /docs/script-vol2-complete.html.
```

```
@workspace Write TypeScript types for all 20 heroines in /src/data/heroines.ts
including: id, name, tier, arcIntroduced, routeStatus, signatureScene, emotionalWound.
Pull data from /docs/gdd-v03.html.
```

```
@workspace Create GitHub issue templates in /.github/ISSUE_TEMPLATE/ for:
1. arc-tracking.md (new arc planning)
2. heroine-route.md (heroine arc development)
3. continuity-check.md (cross-arc flag consistency)
```

```
@workspace Scan /docs/script-vol2-complete.html and extract all FLAG: entries
into a flags-reference.md file in /docs/. Format as a table:
Flag Name | Set In | Effect | Route Implications.
```

---

## 🔧 Recommended VS Code Extensions

Install these for the best experience:

| Extension | ID | Purpose |
|---|---|---|
| **GitHub Copilot** | `GitHub.copilot` | AI completions |
| **GitHub Copilot Chat** | `GitHub.copilot-chat` | Chat + Agent mode |
| **ESLint** | `dbaeumer.vscode-eslint` | TypeScript linting |
| **Prettier** | `esbenp.prettier-vscode` | Code formatting |
| **Tailwind CSS IntelliSense** | `bradlc.vscode-tailwindcss` | Class autocomplete |
| **TypeScript + JavaScript** | `ms-vscode.vscode-typescript-next` | Enhanced TS support |
| **Markdown All in One** | `yzhang.markdown-all-in-one` | Writing in markdown |
| **Word Count** | `ms-vscode.wordcount` | Track scene length |
| **Color Highlight** | `naumovs.color-highlight` | See hex colors in CSS |
| **GitLens** | `eamodio.gitlens` | Branch/blame history |
| **Todo Tree** | `Gruntfuggly.todo-tree` | Track TODO/FIXME in scripts |
| **Spell Right** | `ban.spellright` | Typo check in writing files |

**Workspace settings** — add to `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "github.copilot.enable": {
    "*": true,
    "markdown": true,
    "plaintext": true
  },
  "markdown.validate.enabled": true,
  "[markdown]": {
    "editor.wordWrap": "on",
    "editor.lineNumbers": "off"
  },
  "files.associations": {
    "*.md": "markdown"
  },
  "todo-tree.highlights.defaultHighlight": {
    "foreground": "#c5a059"
  }
}
```

---

## 🌿 GitHub Repository Setup

### Branch Strategy

```
main                    ← stable/released content only
│
├── dev                 ← integration branch
│   ├── writing/vol3    ← all new arc scripts
│   ├── writing/routes  ← heroine deep route scripts
│   ├── engine/core     ← VN engine development
│   ├── engine/combat   ← combat system
│   └── engine/ui       ← UI components
```

**Branch naming convention:**
- `writing/arc9-the-war`
- `writing/stella-deep-route`
- `writing/vera-intro`
- `engine/dialogue-box`
- `engine/save-system`
- `fix/arc5-continuity`

---

### Issue Template — Arc Tracking

Save as `.github/ISSUE_TEMPLATE/arc-tracking.md`:

```markdown
---
name: New Arc
about: Plan and track a new story arc
title: "[ARC] Arc X: Title"
labels: writing, arc
---

## Arc Overview
- **Arc Number:**
- **Title:**
- **Volume:**
- **Primary Heroine Focus:**
- **Secondary Heroines:**
- **Location (Earth/Argena/Both):**

## Chapter Plan
- [ ] Ch 1:
- [ ] Ch 2:
- [ ] Ch 3:
- [ ] Ch 4 ✦ (Signature Scene):
- [ ] Ch 5:
- [ ] Ch 6:
- [ ] Ch 7:
- [ ] Ch 8:

## Route Confirmations This Arc
- Heroine:
- Heroine:

## CGs Planned
- CG Name (Heroine, Chapter):

## Flags Set This Arc
- FLAG: "Name" — set in Ch X — effect

## Continuity Checks Required
- [ ] Check previous flags that affect this arc
- [ ] Verify Kage's current size and location
- [ ] Confirm Shira LOG entry number
- [ ] Confirm Yui notebook entry number
- [ ] Confirm Akemi FIELD NOTE number

## Completion Rewards
- Routes:
- CGs:
- Titles:
- Stats:
```

---

### Issue Template — Heroine Route

Save as `.github/ISSUE_TEMPLATE/heroine-route.md`:

```markdown
---
name: Heroine Route Arc
about: Track a heroine's unwritten deep route arc
title: "[ROUTE] Heroine Name — Arc Title"
labels: writing, heroine-route
---

## Heroine
- **Name:**
- **Tier:** CORE / MID / LATE
- **Current Status:** MET / DEVELOPING / CONFIRMED / MAX
- **Confirmed in Arc:**

## Emotional Wound (from GDD)
> Quote from copilot-instructions.md

## What She Wants That Has Nothing to Do With Kaito

## Arc Plan
- **Arc Title:**
- **Setting:**
- **Chapters:** 6 / 8
- **Signature Scene (Ch ✦):**
- **Crisis point:**
- **Resolution:**

## Voice Reference
> Key dialogue sample establishing her voice

## Checklist
- [ ] Arc outline complete
- [ ] Chapter 1 drafted
- [ ] Signature scene drafted
- [ ] All CHOICE POINTs written
- [ ] CG moments identified
- [ ] Flags documented
- [ ] Cross-heroine dynamics checked
- [ ] Continuity reviewed
```

---

## ✅ Quick-Start Checklist

Work through this in order:

**Day 1 — Setup**
- [ ] Create GitHub repo: `chronicles-sovereign-door`
- [ ] Set up folder structure (copy from above)
- [ ] Download GDD → `/docs/gdd-v03.html`
- [ ] Download Script Vol. II → `/docs/script-vol2-complete.html`
- [ ] Create `.github/copilot-instructions.md` (paste full content above)
- [ ] Install all VS Code extensions
- [ ] Add `.vscode/settings.json`
- [ ] Create initial branches: `main`, `dev`, `writing/vol3`, `engine/core`

**Day 2 — Writing Setup**
- [ ] Create `/docs/arc-status.md` (use arc table from copilot-instructions.md)
- [ ] Create `/docs/heroine-route-tracker.md` (all 20 heroines, status, next steps)
- [ ] Create `/docs/flags-reference.md` (all flags from Vol. II)
- [ ] Create issue templates (arc-tracking.md, heroine-route.md)
- [ ] Open Copilot Chat → paste Vol. III prompt → begin Arc 9

**Day 3 — Engine Setup**
- [ ] `npx create-next-app chronicles-vn --typescript --tailwind --app`
- [ ] Create `/src/types/` — paste scene.ts and heroine.ts type definitions
- [ ] Build `DialogueBox.tsx` using Copilot engine scaffold prompt
- [ ] Build `ChoiceMenu.tsx` using choice engine prompt
- [ ] Connect a test scene JSON

**Week 1 Goals**
- [ ] Arc 9 Chapter 1-4 drafted
- [ ] Stella deep route outline complete
- [ ] DialogueBox + ChoiceMenu components functional
- [ ] One test scene playable in browser

**Ongoing**
- [ ] One arc chapter per session
- [ ] One engine component per session
- [ ] Flag reference updated after each arc
- [ ] Heroine route tracker updated after each confirmation

---

*Chronicles of the Sovereign Door — VS Code Setup Guide v1.0*
*Generated from Genspark session — April 2026*
*All document URLs valid as of generation date*
