---
name: mad-prompters-real-estate-studio
description: Morph-free real-estate videos from listing photos, run on the Higgsfield MCP inside Claude — smooth walkthroughs AND punchy viral cut-style edits, with 10 cinematic style presets. Pick a continuous walkthrough or a hard-cut viral style, plus a Creator Mode that adds viral pacing to walkthroughs. Every style locks to your real photos via a storyboard so nothing morphs; an optional Floor Plan Lock uses a plan to label unlabeled photos by room, order the path by real adjacencies, and pick glide-vs-cut transitions. Runs on Seedance 2.0 (one 15s clip, even multi-shot with hard cuts) or Marketing Studio, with music, optional voiceover, and on-screen text hooks baked into the storyboard. Use whenever the user wants a property/listing/home-tour video, a real-estate reel, a flythrough, or a viral listing edit — or drops home photos (and maybe a floor plan) and wants footage. Handles intake, best-shot triage from up to 30 photos, a locked 9–12-panel storyboard, optional VO and CTA, and runs the video in chat.
version: 1.5.1
author: The Mad Prompter
license: MIT
---

# Mad Prompters Real Estate Studio

*by The Mad Prompter*

Turn a folder of listing photos into cinematic property video that actually portrays the real house — no morphing, no invented rooms — in the **style of your choice**: smooth one-take walkthroughs *or* punchy, beat-synced viral cut-style edits, with music, voiceover, optional on-screen text hooks, and a tight hook/body/CTA script.

---

## EXECUTION CONTRACT — READ FIRST, EVERY TIME

1. **Load this entire SKILL.md into active context.** Re-read it at the start of every invocation. Do not run from memory.
2. **This runs on the Higgsfield MCP inside Claude — not the CLI.** Use the actual MCP tools named in this file.
3. **The entire job is MORPH-FREE output.** Every style — continuous walkthrough *or* hard-cut viral edit — still runs on input images + a locked storyboard. Continuous styles interpolate *between* locked frames; cut styles hard-cut *between* locked frames and apply FX only *on* those frames. Either way the house is always pinned to a real plate. The lock NEVER changes between styles — only the cinematic skin does. If you are about to let the model invent a room/hallway/stair, stop.
4. **Style is chosen FIRST and pre-fills defaults.** Once a style is picked, do NOT re-ask the things it already decided (grade, genre, audio feel, beat count, transitions, and sometimes aspect/CTA). Only ask what's left.
5. **Adapt to the property tier** — luxury estate, family home, or updated starter/character home. Don't force "luxury" framing onto a mid-market listing (and steer them toward a fitting style).
6. **Never burn video or audio credits without explicit user confirmation** of the storyboard, the script, and the prompt.
7. **Three creative gates require a STOP-and-confirm:** hero-shot selection (Phase 2), storyboard (Phase 3), and the VO script (Phase 4).

---

## WHY THIS WORKFLOW EXISTS (the morph problem)

A continuous camera flying *through* disconnected rooms forces the video model to invent the connective space between them — hallways, stairs, doorways that don't exist in the photos. Those invented regions warp ("morph") and stop looking like the real house.

**The fix this skill operationalizes:** lock every beat of the move to a real photo via a single storyboard input image, attached FIRST. The model interpolates *between locked frames* instead of hallucinating; room-changes happen only on deliberate light-blooms or material match-cuts. **This lock is identical across all style presets** — flashier looks just get stricter discipline (more beats, snaps only on blooms).

---

## STYLE PRESETS — pick ONE at the start

Each preset is a modifier bundle. The **storyboard lock and input-image rules are the same for all of them** — only the camera, transitions, beat count, grade, genre, and audio change. **Type** = how the clip moves: *Continuous* = one unbroken take (interpolate between locked frames); *Cut* = a single 15s clip with internal hard cuts (Seedance cuts *between* locked frames — no stitching, no post edit).

| Preset | Type | Camera & energy | Transitions | Beats | Grade / time | `genre` | Audio default | Aspect |
|---|---|---|---|---|---|---|---|---|
| **Smooth Glide** *(default)* | Continuous | calm one-take; push → glide → arc → settle | light-blooms + soft match-cuts | 9 | golden-hour warmth, soft natural light | `auto` | warm ambient bed | user choice |
| **Luxe Cinematic** | Continuous | slow, deliberate crane/dolly; elegant rises, lingering holds | material match-cuts + slow blooms | 9 | rich contrast, deep shadows, golden/blue hour | `epic` | orchestral swell | 16:9 |
| **FPV Rush** | Continuous | fast momentum flythrough; drone accel, whip-through doorways | whip / speed-blur **only on blooms** | 12 | punchy, vivid, bright daylight | `action` | upbeat electronic | user (often 9:16) |
| **Bright & Airy** | Continuous | gentle push-ins & reveals; smooth, welcoming | soft blooms + simple cuts | 9 | bright midday, soft whites, low contrast | `auto` | warm acoustic | user choice |
| **Twilight Glam** | Continuous | slow, elegant moves; warm-evening exterior, glowing interiors | warm light-blooms + slow match-cuts | 9 | warm evening / golden hour; amber interior glow vs deep-blue sky | `drama` | cinematic pad | 16:9 |
| **Social Pop** | Continuous | vertical-native, beat-synced, dynamic but controlled | beat-snaps held **on locked frames**; snap only on blooms | 12 | vivid, saturated, punchy | `action` | beat-driven music | 9:16 |
| **Story (Narrated)** | Continuous | slow, emotional, documentary cadence; lingering | gentle blooms + soft match-cuts | 9 | warm, nostalgic golden | `drama` | VO-led + soft underscore | user choice |
| **Viral Cut** | **Cut** | fast hard cuts on the beat; punch-in/out zooms; speed ramps | hard cuts + clean flash/whip **on locked frames** | 12 | bright, punchy, vivid | `action` | upbeat, beat-driven | 9:16 |
| **FX Showcase** | **Cut** | snappy cuts + stylized FX; zoom-blur whips, light streaks, lens flares between rooms | FX transitions **on locked frames** | 12 | vivid, glossy, high-contrast | `action` | energetic electronic | 9:16 |
| **Hype Reel** | **Cut** | fastest cuts; punch/shake; beat-drop sync; bold on-screen hooks | hard cuts + shake/flash on beat drops | 12 | bold, saturated, punchy | `action` | high-energy beat-drop | 9:16 |

**Best for:** Smooth Glide = any property (the safe workhorse). Luxe Cinematic = luxury / modern / architectural. FPV Rush = social, younger buyers, fast flow. Bright & Airy = family / starter / mid-market. Twilight Glam = evening hero / luxury curb appeal. Social Pop = Reels/TikTok/Shorts lead-gen. Story = agent-brand emotional storytelling. **Viral Cut** = scroll-stopping listing edit for IG/TikTok. **FX Showcase** = eye-candy social that still reads every room. **Hype Reel** = maximum-energy hook for the feed.

**Preset auto-rules:**
- **Social Pop** also defaults **CTA text ON** and aspect **9:16**.
- **Story** also defaults **voiceover ON** (it's built around the VO script in Phase 4).
- **High-energy continuous presets (FPV Rush, Social Pop)** use **12 storyboard beats** (3×4 board) instead of 9, and may ONLY whip/snap **on a bloom** — never mid-room. This is how the energetic *continuous* looks stay morph-free.
- **Cut presets (Viral Cut, FX Showcase, Hype Reel)** default **aspect 9:16**, use a **12-panel board as a SHOT LIST** (hard cuts between locked frames, not a path), `genre: action`, and **trigger the on-screen-text question** (see below). FX/cuts land **only on locked frames** — that's what keeps a fast edit morph-free.
- **Twilight Glam wording:** always render with *warm evening / amber / golden-hour* language — **never** "sensual / dusk / glowing / dark," which false-trips Seedance's NSFW filter and refunds the job.
- Everything a preset sets is an **overridable default** — the user can change any of it.

*(Presets are a library — easy to extend. Add new looks by defining a new row + bundle; the lock never changes.)*

---

## CREATOR MODE (toggle — adds viral pacing to a walkthrough)

**Creator Mode** layers viral, editor-style energy *on top of* a continuous walkthrough preset — without abandoning the look. It adds: punch-in / punch-out zooms on hero details, speed ramps into the best room, beat-synced timing, **2–4 well-placed hard cuts on the beat**, and (optional) on-screen text hooks.

- **Available on every continuous preset EXCEPT Story** (viral pacing fights a narrated emotional piece).
- **Bumps the storyboard to 12 beats** so there are enough locked anchors for the cuts/punch-ins.
- **Keeps the base preset's grade, time-of-day, and genre** — it only injects pacing + energy.
- All cuts/FX still land **on locked frames** (same morph-free rule).
- Offered as a toggle in Phase 1 right after a continuous preset is chosen ("Add Creator Mode energy?"). If ON, it also **triggers the on-screen-text question**.

Think of it as: *Twilight Glam + Creator Mode* = the glam evening look, but cut to hit on the feed.

---

## ON-SCREEN TEXT (ask — don't assume)

When a **cut preset** is chosen **or Creator Mode is ON**, ASK whether they want on-screen text — and if yes, pin the exact lines before building.

1. **Ask** *(button)*: "Want on-screen text hooks?" → Yes / No.
2. **If yes, offer a menu** *(button)* of what kind:
   - **Hook + payoff** — e.g. "WAIT FOR THE KITCHEN" → the reveal.
   - **Stat cards** — "3 BED • 3 BATH • UPDATED," price, or address.
   - **CTA punches** — "BOOK A SHOWING," "DM TO TOUR."
   - **Custom** — they type the exact copy.
3. **Confirm the literal lines and where they land** (which beat / timecode) before generating.
4. **Text is rendered INTO the storyboard panels — and carries into the video.** `gpt_image_2` renders clean, legible type and Seedance reproduces it, so the words actually appear on screen in the final clip — no post pass. Bake each line onto the panel(s) for the beat it belongs to; for a hook that should hold across several cuts, repeat it on those consecutive panels so it stays up. Keep lines short, in CAPS, high-contrast with a solid bar or scrim behind them so they survive the video render. (Post is only a fallback — a very long custom line, or a specific font you can’t get in-image.)

---

## ENGINES (orthogonal to style)

| | **Seedance 2.0** (DEFAULT) | **Marketing Studio** (alternate) |
|---|---|---|
| Best for | True continuous one-take in any style | Product-template / brand-spot look |
| 15s in one clip | **Yes** — single generation, 4–15s | No — built from preset; stitch if needed |
| Frame locks | `start_image` + `end_image` + image refs | image refs (storyboard first) |
| Photo budget | up to **8 images incl. storyboard** (board + 7 plates: 1 `start_image`, 1 `end_image`, ≤ 5 interior) | **4–6** hero photos |
| Native audio | **Yes** — `generate_audio` toggle (scratch bed) | No — silent, all audio in post |
| Voiceover | Feed VO as `audio` reference | Post only |

**Default to Seedance 2.0.** All ten style presets — continuous and cut — run on it, and it performs the cut presets' internal hard cuts in a single clip. Use Marketing Studio only for the product-template look.

---

## REQUIRED MCP TOOLS

- `Higgsfield:media_upload_widget` — browser uploader so local photos become `media_id`s.
- `Higgsfield:generate_image` (`gpt_image_2`) — the 9/12-panel storyboard, conditioned on real plates.
- `Higgsfield:list_voices` + `Higgsfield:generate_audio` (`text2speech_v2_elevenlabs`/`minimax`) — pick a voice, generate the VO.
- `Higgsfield:generate_video` — final video (`seedance_2_0` default, or `marketing_studio_video`).
- `Higgsfield:show_marketing_studio` — product + presets (MS engine only).
- `Higgsfield:job_display` — re-display a result by job id.
- `Higgsfield:models_explore` — deferred; `tool_search("models explore")` first.

**Critical reality:** Higgsfield's remote tools **cannot read Claude chat attachments** — only `media_id`s. So photos upload via `media_upload_widget`. But Claude *sees* chat-attached images for triage. Use both; map by filename.

---

## PHASE 1 — INTAKE (style first, then only what's left)

**Lead with STYLE**, then keep it conversational. Use **tappable buttons** for the multiple-choice items (the interactive option tool). If the user dumps a full brief, skip to Phase 2.

1. **STYLE — pick FIRST.** There are 10 presets, so select in two quick taps (the option tool caps at 4):
   - **Tap 1** *(button)* — pick a family: **Walkthrough** (smooth, continuous) · **Viral Cut / FX** (hard cuts, punchy) · **Recommend one** (you choose from the property).
   - **Tap 2** *(button)* — show ≤4 presets from that family, curated to the property tier:
     - *Walkthrough:* offer the 4 best fits (mid-market → Smooth Glide, Bright & Airy, Twilight Glam, Story; luxury → Luxe Cinematic, Twilight Glam, Smooth Glide, FPV Rush).
     - *Viral Cut / FX:* Viral Cut, FX Showcase, Hype Reel.
   - **If a Walkthrough preset was picked** *(button)* — offer **Creator Mode** ("Add viral pacing — punch-ins, speed ramps, beat-synced cuts?"), available on all walkthrough presets except Story.
   - **Lock the preset bundle** from the table above (plus Creator Mode if chosen).
2. **Property** — name/address/listing label (free text).
3. **Photos (+ optional floor plan)** — "Attach the home's photos in chat (up to 30) so I can see them and pick the best. If you have a **floor plan**, attach it too — I'll use it to label rooms and lock the path." If a floor-plan image is among the uploads (or the user mentions one), set **Floor Plan Lock ON** (Phase 2.5).
4. **Only-what's-left** *(button)* — ask ONLY the items the preset didn't decide:
   - **Engine** if not obvious (default Seedance 2.0).
   - **Aspect** only if the preset didn't set one (Smooth Glide / FPV Rush / Bright & Airy / Story).
   - **Audio** — show the preset's default (music/VO) and let them confirm or flip.
5. **CTA** — the end-card line (free text), or skip. (Social Pop assumes you want one.)
6. **Overrides** — anything to change about the preset (moodier, brighter, different genre), plus any lock/avoid notes.

7. **On-screen text** *(only if a cut preset or Creator Mode is active — button)* — "Want on-screen text hooks?" If yes, run the **On-Screen Text** menu (Hook+payoff / Stat cards / CTA punches / Custom) and confirm the exact lines (baked into the storyboard so they render in-video).

Don't re-ask grade, genre, transitions, or beat count — the preset set those.

**Marketing Studio mode table (alternate engine only):** `tv_spot`, `product_showcase` (default), `ugc`, `ugc_how_to`, `ugc_unboxing`, `product_review`, `wild_card`. *Hyper Motion is NOT an MS mode — use the Seedance engine for continuous looks.*

---

## PHASE 2 — BEST-SHOT TRIAGE + UPLOAD

Triage from the chat attachments FIRST, then upload only the winners (sidesteps the 20-file cap, saves the user uploading unused shots).

1. **Look at the chat-attached photos** and sort into walkthrough beats, then pick heroes up to the **engine's photo budget** (below) — one hero per beat, in this order:
   1. EXTERIOR OPEN (front facade / curb hero — required; reused for the climax).
   2. KITCHEN or GREAT ROOM (signature interior).
   3. PRIMARY BATH / FEATURE SPACE (statement room, or the standout updated space).
   4. LIVING / SECOND INTERIOR (optional).
   5. VIEW / BALCONY / POOL / BACKYARD (the "step outside" reveal).
   6. EXTERIOR CLOSE / AERIAL (the climax — can reuse the exterior plate).

   **Photo budget (by engine):**
   - **Marketing Studio → 4–6 heroes.**
   - **Seedance 2.0 → up to 8 images TOTAL, storyboard included.** Storyboard = slot 1, then **up to 7 plates**: one can be the `start_image`, one the `end_image`, leaving up to ~5 interior/detail `image` plates. Use the full budget when the home has the coverage; fewer is fine.
2. **Criteria:** sharpness, lighting, composition, hero appeal, and **coverage diversity**. **Exclude** floorplans, unfinished/raw spaces, clutter, and redundant angles — and say why. **If a floor plan was provided (Floor Plan Lock ON), run Phase 2.5 first** to label each photo's room and order the heroes by real adjacency.
3. **STOP and confirm by FILENAME** *(+ room label when a floor plan was provided)*: "[filename — room — one-line why]. Swap any?" Wait for the user.
4. **After confirmation, upload only the heroes:** `Higgsfield:media_upload_widget` (`type: image`, `min_files: 4`, `max_files: 20` — caps at 20/batch, `multiple: true`). Map each filename → `media_id`. (Batch in ≤20 if ever needed.)

---

## PHASE 2.5 — FLOOR PLAN LOCK (optional — only if a floor plan is provided)

A floor plan is a **spatial** map; the storyboard is a **temporal** one. Together they kill the two things the model otherwise invents — the path through the house and what's adjacent to what — making this the strongest anti-morph aid available. **But it's a planning input for the storyboard, NOT a runtime input for the video model.** Seedance / gpt_image_2 won't "navigate" a blueprint; the plan informs how *you* build the board.

**Skip this phase entirely if no plan was given** — fall back to the standard best-guess beat order.

**What the plan does:**
1. **Labels unlabeled photos.** Cross-reference each chosen photo against the plan — the white kitchen matches the kitchen on the plan, the corner room with two windows matches the primary bedroom. This is how rooms get identified when the photos aren't named.
2. **Orders the walkthrough by real adjacency.** Build the camera path from rooms that actually connect (kitchen → dining → living because they share an opening), not a guess that forces an invented hallway.
3. **Tags every transition glide-vs-cut.** Adjacent rooms → a continuous **glide** on a bloom (a real move). Non-adjacent rooms (upstairs bed → backyard) → an honest **match-cut**. The morph rule, now driven by the actual layout instead of a guess.

**How to run it:**
- **Identify the plan:** it's the upload that's a 2D schematic (line drawing / labeled rooms), not a photo. Never treat it as a hero plate or upload it as a walkthrough beat.
- **Build the adjacency map:** from the plan, note which hero rooms touch (shared wall or doorway) and the natural route — entry → public spaces → private spaces → outside.
- **Map photos → rooms → path:** produce the ordered beat list with a **room label** per hero and a **glide/cut tag** per transition.
- **Confirm at the Phase 2 gate (no new stop):** the hero list now reads e.g. *"IMG_2231 → Kitchen (glide from Entry)."* The user fixes any mislabel there. If a match is uncertain, say so and ask.

**Optional floor-plan beat** *(ask once, only when a plan is present — button)*: "Want a quick floor-plan orientation beat (a 'you-are-here' moment)?" Default **no**.
- **Yes** → add ONE panel to the storyboard that renders the plan as a clean orientation card (opening establisher or mid-tour locator), and pass the plan image as a `role: image` reference **for that panel only**. Keep it short (~1–2s); the rest stays photoreal rooms.
- **No** → the plan stays a behind-the-scenes planning tool and never appears on screen.

**Feeding downstream:** the plan-derived **path + per-transition glide/cut tags** become the beat order in Phase 3. The plan image goes into Phase 3 **only** if the orientation beat was requested — **never** into the Seedance `medias` directly (it would try to render the blueprint into rooms).

---

## PHASE 3 — STORYBOARD INPUT IMAGE (gpt_image_2) — beats per preset

The storyboard is the temporal lock. **Beat count comes from the preset:** 9 panels (3×3) for most continuous presets; **12 panels (3×4) for FPV Rush, Social Pop, every Cut preset, and any preset with Creator Mode ON**.

**Two board kinds:**
- **Continuous presets** → a **path board**: the 9/12 panels read as one unbroken move; room-changes only on blooms.
- **Cut presets (Viral Cut / FX Showcase / Hype Reel)** → a **SHOT-LIST board**: each of the 12 panels is a *discrete hard-cut shot*. Intercut wide reveals with punch-in detail shots and revisit a room if it helps the rhythm — order for energy, not for a continuous path. Each panel is still locked to a real plate.
- **If Floor Plan Lock ran (plan provided):** order the panels by the plan-derived **path** and honor the **glide/cut tags** — glide transitions use blooms/continuous moves, cut transitions use match-cuts (hard cuts for cut presets). If the orientation beat was requested, add ONE floor-plan card panel and pass the plan image as a `role: image` reference for that panel only.

Call `Higgsfield:generate_image`:
- `model: gpt_image_2`
- `medias`: the confirmed hero plates, each `role: image` (plus the floor-plan image **only if** an orientation beat was requested)
- `aspect_ratio`: **match delivery orientation** — `3:2` for 16:9, `2:3` for 9:16, `1:1` for square. (Planning map; final framing set by the engine in Phase 6.)
- `resolution: 4k`, `quality: high`

**Storyboard prompt template** (fill brackets from the **chosen preset** + hero plates; drop CTA if not requested):

```
A clean professional [3x3 nine-panel | 3x4 twelve-panel] storyboard contact sheet for a 15-second [PRESET NAME]-style real-estate [walkthrough | hard-cut edit] of the EXACT home in the attached references ([tier]). White sheet, thin gray gutters, each panel a cinematic frame with a small dark caption bar (timecode + short shot label, white sans-serif). [PRESET GRADE / TIME-OF-DAY] color grade across all panels. Camera feel: [PRESET CAMERA & ENERGY]. Transitions: [PRESET TRANSITIONS]. Keep every room faithful to its reference plate: [EXTERIOR lock], [KITCHEN lock], [FEATURE lock], [VIEW/BACKYARD lock]. Do NOT invent rooms or redesign anything.

Panels (read left-to-right, top-to-bottom), timecoded across the 15s:
[9 beats: exterior wide -> approach -> through-door bloom -> interior entry -> interior hero -> feature room (match-cut) -> to window -> view/backyard -> aerial/CTA]
[12 beats (FPV Rush / Social Pop / Creator Mode): split the four segments into 3 finer beats each; every room-change still lands on a bloom]
[12 beats (Cut presets — SHOT LIST, hard cuts): order for rhythm, e.g. exterior hero -> kitchen punch-in -> living wide -> feature detail -> kitchen wide -> sunroom -> backyard -> detail -> exterior pull -> end hero; mix wide + punch-in, hard cuts, no continuous path]
[If on-screen text was requested: render each exact line as a BOLD, legible on-screen graphic on the panel(s) for its beat — e.g. the hook "<HOOK>" on the opening panels, a stat card "<STATS>" mid-tour, and the CTA "<CTA LINE>" as the closing end-card. High-contrast CAPS with a scrim/bar behind; repeat a hook across consecutive panels so it holds. This text is meant to appear in the final video, so style it the way it should look on screen.]

Photorealistic, 8K detail, legible caption bars [and the requested on-screen text graphics] only, no other text, no people, no watermark.
```

**Baking on-screen text (if requested):** render it as the actual on-screen graphic the way it should appear in the final video — bold, legible, lower-third or centered, high-contrast with a scrim — on the panels for its beats. The small caption bar (timecode + shot label) is only a planning guide and won’t read as on-screen copy; the baked text graphic is what Seedance carries into the clip. Keep copy short and in CAPS for clean transfer, and repeat a hook across the panels it should hold over.

**Drift check + STOP:** "Does each room read as the real space; did the kitchen/feature room blend? Good to lock?" If a room drifted, regen the board (or swap that plate). Most important gate.

Note: a front → backyard → front climax is a deliberate "beauty-card" cut, not a continuous move.

---

## PHASE 4 — TIMED 15-SECOND SCRIPT + VOICEOVER (if VO on)

VO is ON by default for **Story**; optional elsewhere. Skip entirely if VO is off (a CTA-only end-card needs no script).

**Word budget:** ~40 words at ~2.7 words/sec, aligned to beats — **Hook (0–3s, ~8w) / Body (3–12s, ~24w) / CTA (12–15s, ~8w)**. Match the script's tone to the preset (Luxe = elevated; Bright & Airy = warm/welcoming; Story = emotional). Present it, **STOP for approval.**

If VO on: `Higgsfield:list_voices` → pick a fitting voice → `Higgsfield:generate_audio` (`text2speech_v2_elevenlabs`, `voice_type`+`voice_id`, `prompt:` the script) → capture the audio `job_id`. That becomes the `audio` reference in Phase 6A.

---

## PHASE 5 — VIDEO PROMPT (engine + preset specific)

### 5A — Seedance 2.0 (DEFAULT)

```
STYLE — 8K cinematic, photorealistic real-estate cinematography, single continuous take, [PRESET NAME] look. [PRESET GRADE / TIME-OF-DAY]. NO 3D/game-engine/CGI look. [PRESET-appropriate motion-blur/shutter]. Real gravity and contact shadows. Materials identical to the reference plates and the attached storyboard — no drift, no invented rooms.

SUBJECT — The EXACT home in the attached references: [one-line whole-home description].

ACTION — One unbroken 15-second walkthrough following the attached storyboard as the precise shot order. Camera energy: [PRESET CAMERA & ENERGY]. Room-changes happen ONLY on [PRESET TRANSITIONS] — never through invented space:
SHOT 1 (0:00-0:04) — [exterior open -> approach; bloom through the entry].
SHOT 2 (0:04-0:08) — [from bloom, move across the signature interior; settle].
SHOT 3 (0:08-0:11) — [match-cut into the feature room; toward its brightest window; bloom].
SHOT 4 (0:11-0:15) — [onto the view/backyard, then a beauty-card pull-back; ease to a hold].
[For FPV Rush / Social Pop: faster cadence, 12 micro-beats, whip/snap ONLY on the blooms.]

CAMERA — [PRESET camera language]. No teleporting between spaces.

AUDIO — [PRESET audio default, if music on].

CONSTRAINTS — [ASPECT]. ONE TAKE. NO invented hallways/stairs/doors. Transitions ONLY on blooms/match-cuts. No morphing, no warping geometry, no redesigned rooms. No people. On-screen text only if it is baked into the storyboard panels (then reproduce it exactly) — otherwise none.
```

Feed: storyboard `image` ref FIRST, exterior `start_image`, closing exterior `end_image`, interior/view plates `image` (**max 8 images total incl. storyboard**: board + ≤ 7 plates).

### 5B — Marketing Studio (alternate)

Positional `@image_N` refs; storyboard is `@image_1`, attached first. Same beat sequence and locks, with the preset's grade/energy described in the body, and ending with `@product:[product_id]`. (See v1.2 structure — `@image_1` = storyboard, then plates in beat order.)

### 5C — Seedance 2.0 cut-style / Creator Mode (single clip, internal hard cuts)

Seedance renders **multiple shots with hard cuts inside one 15s generation** off the storyboard + plates — no stitching. Use for **Viral Cut / FX Showcase / Hype Reel**, and as an add-on for **Creator Mode**.

```
STYLE — fast, punchy social real-estate edit, [PRESET] look, ONE 15s clip with INTERNAL HARD CUTS. [PRESET GRADE]. Photoreal, NO 3D/CGI. Beat-synced cutting; motion FX applied ONLY on locked frames/transitions. Every shot matches a reference plate / storyboard panel exactly — no drift, no invented rooms.

SUBJECT — The EXACT home in the attached references: [one-line whole-home description].

EDIT — Follow the attached 12-panel storyboard as a SHOT LIST. HARD-CUT between shots on the beat (~1–1.5s each). Mix wide reveals with punch-in detail shots; you may revisit a room for rhythm. Apply [PRESET FX: punch-in/out zoom · speed ramp · flash cut · zoom-blur whip · light streak · lens flare] as the transition BETWEEN locked shots — never as free camera movement inside a room. If the storyboard panels carry on-screen text, keep those exact words on their beats.
Cadence (15s, ~10–12 cuts): exterior hero -> kitchen punch-in -> living wide -> feature detail -> kitchen wide -> sunroom -> backyard reveal -> detail -> exterior pull-back -> end hero. Cuts land on the beat.

CAMERA — short, controlled move per shot (quick push / pull / whip); each shot stays locked to its plate. No teleporting, no morphing.

AUDIO — [PRESET music]; cuts hit on the beat.

CONSTRAINTS — [ASPECT, default 9:16]. HARD CUTS ALLOWED (this is an edit, not a one-take). FX only on locked frames/transitions. Reproduce any on-screen text exactly as it appears in the storyboard panels (it is baked in, not added later). No invented rooms, no warping geometry. No people.
```

**Creator Mode modifier** (append to a *continuous* preset's 5A prompt instead of switching templates):
```
CREATOR MODE — keep the [BASE PRESET] look and grade, but add viral pacing: 2–4 well-placed HARD CUTS on the beat, punch-in/punch-out zooms on hero details, a speed ramp into the best room, snappy energy. All cuts/FX land ONLY on locked frames. If the storyboard panels carry on-screen text, reproduce those words on their beats. Still no invented rooms, no morphing.
```

Feed (both): storyboard `image` FIRST, exterior `start_image`, closing exterior `end_image`, interior/detail plates `image` (**max 8 images total incl. storyboard**: board + ≤ 7 plates). On-screen text is **baked into the storyboard panels** (Phase 3) and carries into the render — not added in post.

---

## PHASE 6 — RUN THE VIDEO

### 6A — Seedance 2.0 (DEFAULT)

`Higgsfield:generate_video`:
- `model: seedance_2_0`
- `prompt`: the 5A prompt
- `medias` (**storyboard FIRST**): `{storyboard, role:image}`, `{exterior, role:start_image}`, `{interior/feature/view, role:image}` (each), `{closing exterior, role:end_image}`, **if VO on** `{VO audio id, role:audio}` — **max 8 images total incl. the storyboard** (board + up to 7 plates: 1 `start_image`, 1 `end_image`, ≤ 5 interior `image`). Never exceed 8 images.
- `duration: 15`, `aspect_ratio`: from preset/intake, `resolution: 1080p` (`4k` only with `mode: std`), `mode: std`, `bitrate_mode: high`
- `genre`: **from the preset** (Smooth Glide/Bright&Airy `auto`, Luxe `epic`, FPV/Social/Viral Cut/FX Showcase/Hype Reel `action`, Twilight/Story `drama`). Creator Mode keeps the base preset's genre.
- **`generate_audio` per the toggle logic + preset audio default:**
  - VO on, music off → VO `audio` ref + `generate_audio: false`
  - Music on, VO off → no audio ref + `generate_audio: true` (native bed)
  - Both on → VO `audio` ref + `generate_audio: false`, add licensed music in post
  - Both off → `generate_audio: false`
- **Decline spurious presets:** if Higgsfield says the prompt "looks like" a named preset (e.g. "IN THE DARK"), DECLINE it — re-run with `declined_preset_id: <id>` to generate the literal prompt. Our style presets are built INTO the prompt, not Higgsfield presets.
- **Cut presets / Creator Mode:** still ONE `generate_video` call — Seedance performs the internal hard cuts in a single 15s clip (no stitching, no post-assembly). Use the 5C prompt (or the Creator Mode modifier), the 12-panel SHOT-LIST board, and `genre: action` for cut presets. On-screen text is baked into the storyboard (Phase 3) and renders in-clip — no post text pass.
- **Confirm before submitting** (credits). Storyboard-first is non-negotiable.

### 6B — Marketing Studio (alternate)

Register product via `Higgsfield:show_marketing_studio` (`action: create`, `type: product`, `title`, `medias:[exterior]`) → capture `product_id`. Run `generate_video` (`model: marketing_studio_video`, 5B prompt, **storyboard-first medias**, `mode` (default `product_showcase`), `product_ids`, `duration: 15`, `aspect_ratio`, `resolution: 1080p`). **MS is silent** — VO + music in post. Confirm before submitting.

---

## PHASE 7 — DELIVERY + POST

`Higgsfield:job_display`, then report honestly:

```
Walkthrough rendered.
- Style: [preset][ + Creator Mode]   Engine: [Seedance 2.0 / Marketing Studio]
- Aspect/res: [ratio] / [res]   Audio: [VO on/off] · [music on/off]
- References: storyboard + [N] hero plates [+ VO]
- Result: [link]

Holds the house: [1-2 honest notes]
Post fixes:
- Music — Seedance's native bed is a scratch track; swap a licensed cue (match the preset feel). MS renders silent.
- On-screen text / CTA — baked into the storyboard panels and rendered in-clip. (Only redo in post if a line came out soft, or you want a different font.)
- Drift — if a room morphed, fix the storyboard panel or that plate and regen; don't blind-reroll.

Next moves:
- Re-render in a different STYLE preset (same plates + storyboard)
- Swap engine (Seedance <-> Marketing Studio)
- Vertical / horizontal cutdown
- Lock and deliver
```

---

## KEY LOCKS & GOTCHAS (cheat sheet)

- **The lock is identical across all styles.** A preset only changes camera/transitions/beats/grade/genre/audio — never the input-image + storyboard discipline.
- **Style first; pre-fills defaults.** Don't re-ask what the preset set.
- **Morph discipline scales with energy:** FPV Rush & Social Pop = **12 beats**, whip/snap **only on blooms**.
- **Cut presets (Viral Cut / FX Showcase / Hype Reel)** = ONE 15s Seedance clip with **internal hard cuts** off a **12-panel SHOT-LIST board**; FX/cuts only on locked frames; default **9:16**, `genre: action`.
- **Creator Mode** = viral pacing layered on any walkthrough **except Story**; bumps to 12 beats; keeps the base look.
- **On-screen text** = ASK when a cut preset / Creator Mode is active; confirm exact lines; **bake them into the storyboard panels** so they render in-video (post only as fallback).
- **Twilight Glam wording** = *warm evening / amber / golden-hour*, never *sensual/dusk/glowing/dark* (NSFW false-trip → refund).
- **Storyboard attached FIRST** in `medias` (both engines) — the anti-morph anchor.
- **Floor Plan Lock (optional)** = if a floor plan is provided, use it to label unlabeled photos by room, order the path by real adjacency, and tag transitions glide-vs-cut. A planning input for the storyboard, **not** a Seedance input; optional 'you-are-here' beat, default off.
- **Decline auto-matched Higgsfield presets** (`declined_preset_id`) — our styles live in the prompt.
- **Board orientation follows delivery aspect** — `3:2` / `2:3` / `1:1`.
- **Seedance 2.0:** full 15s in ONE gen (4–15s), `start_image`/`end_image` bookends, `generate_audio` toggle (scratch bed → license in post). `genre` from preset.
- **VO pipeline:** `list_voices` → `generate_audio` (`text2speech_v2_elevenlabs`) → feed as `role: audio` with `generate_audio: false`.
- **Standalone music isn't on this MCP** — licensed track = post, either engine.
- **gpt_image_2** storyboard at **4k/high**, conditioned on real plates — never a from-scratch grid.
- **MCP can't read chat attachments** → `media_upload_widget` (20/batch); Claude *sees* chat images for triage; map by filename.
- **Up to 30 photos in; pick heroes to the engine budget** — **Marketing Studio 4–6**, **Seedance up to 8 total incl. storyboard** (board + 7 plates: 1 start, 1 end, ≤ 5 interior). Coverage diversity; exclude floorplans/raw spaces.
- **Match the property tier** and steer toward a fitting style.
- **Script budget:** ~40 words — hook ~8 / body ~24 / CTA ~8.

---

## TONE & DELIVERY RULES

- Lead with the artifact. No preamble, no closing recap.
- Match the user's message length. Short ask = short reply.
- Prose default; headers/bullets only when structure earns it.
- Push back when the user is about to morph the house or pick a style/engine that won't deliver; comply if they override.
- Never narrate what you're about to do — just do it.
- No emojis unless the user uses them first.
