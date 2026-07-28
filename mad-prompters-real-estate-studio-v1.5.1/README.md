# 🎬 Mad Prompters Real Estate Studio
### by The Mad Prompter

![Version](https://img.shields.io/badge/version-1.5.1-E6B422)
![License](https://img.shields.io/badge/license-MIT-3b82f6)
![Claude Skill](https://img.shields.io/badge/Claude-Skill-8b5cf6)
![Engine](https://img.shields.io/badge/Higgsfield-Seedance%202.0-111111)

> **Turn your listing photos into a 15-second cinematic listing film — inside Claude.**
> *We don't make ads. We make worlds.* — Mad Prompters

A Claude **skill** that turns a folder of ordinary listing photos into a **15-second cinematic property video** — run entirely inside a Claude chat on the Higgsfield engine. Pick a **style** and it renders either a **smooth one-take walkthrough** or a **punchy viral cut-style edit** — and it's **morph-free by design**: the house always stays the house.

Works for **any tier** — luxury estate to updated starter/character home — adapting the vibe and copy automatically.

---

## 🧠 The problem it solves

AI home walkthroughs **morph**: when a camera flies *through* disconnected rooms, the model invents the hallways and stairs in between — and those invented spaces warp, so the video stops looking like the real house.

**The fix:** every beat is locked to a real photo via a **9- or 12-panel storyboard** attached first. Continuous styles only interpolate *between* locked frames; cut styles hard-cut *between* locked frames and apply FX only *on* them. Room-changes happen on deliberate light-blooms or match-cuts. Nothing is left for the AI to invent — even in a fast edit. **Have a floor plan? Even better** — *Floor Plan Lock* turns it into a spatial map: it labels your unlabeled photos by room, orders the path by which rooms actually connect, and marks each transition as a real glide or an honest cut.

---

## ✨ Features

- **10 cinematic style presets** — pick a look first; it pre-fills every setting.
  - *Walkthrough:* Smooth Glide, Luxe Cinematic, FPV Rush, Bright & Airy, Twilight Glam, Social Pop, Story (Narrated).
  - *Viral cut / FX:* **Viral Cut**, **FX Showcase**, **Hype Reel** — hard cuts, punch-ins, and FX in a single clip.
- **Creator Mode** — a toggle that layers viral pacing (punch-ins, speed ramps, beat-sync, hard cuts) onto any walkthrough style.
- **Morph-free lock** — a storyboard pins every shot to your real photos; cuts and FX only ever land on locked frames.
- **Floor Plan Lock (optional)** — hand it a floor plan and it labels your unlabeled photos by room, orders the walkthrough by real adjacencies, and picks glide-vs-cut transitions — the strongest anti-morph aid there is.
- **True one-take *or* internal hard cuts** — Seedance 2.0 renders the full 15 seconds — cuts included — in a single clip.
- **Dual-engine** — Seedance 2.0 (default) or Marketing Studio.
- **Music, voiceover & on-screen text** — music bed on/off, VO on/off with a timed Hook / Body / CTA script, and optional text hooks/stat-cards rendered right in the clip (baked into the storyboard).
- **Any tier** — luxury through starter home; the vibe adapts.
- **Smart triage** — drop up to 30 photos; it picks the strongest to the engine's budget (Marketing Studio 4–6; Seedance up to 8 incl. the storyboard) and tells you why.

---

## 🚀 Install

1. **Get the files** — click **Code → Download ZIP** (or grab the latest [Release](../../releases)), and unzip.
2. In Claude: **Settings → Capabilities → Skills → Add Skill**, then upload the `mad-prompters-real-estate-studio/` folder (it contains `SKILL.md` + `HOW-TO-USE.md`).
3. Enable the **Higgsfield** connector in your chat (every render runs through it).
4. Start a new chat and type **`/mad-prompters-real-estate-studio`** — or just drop your listing photos and ask for a video.

---

## 🎯 Quickstart

```
Style    →  pick a preset (Walkthrough / Viral-Cut / Recommend)   (tappable)
            walkthrough? optional Creator Mode for viral pacing
Photos   →  attach in chat (<=30) for triage
Plan     →  optional floor plan -> locks rooms + path (Floor Plan Lock)
Triage   →  approve heroes (MS 4-6 · Seedance up to 8 w/ storyboard)
Upload   →  winners only, via the Higgsfield widget (<=20/batch)
Options  →  only what the style didn't set (engine - aspect - audio - CTA - text)
Story    →  9- or 12-panel board, locked to real rooms   -> APPROVE
Script   →  (if VO) hook/body/CTA ~40 words               -> APPROVE
Render   →  Seedance 2.0 — one 15s clip (cuts included)
Post     →  licensed music (text renders in-clip)
```

Full walkthrough: [`mad-prompters-real-estate-studio/HOW-TO-USE.md`](mad-prompters-real-estate-studio/HOW-TO-USE.md)

---

## 🎨 Walkthrough vs Viral-Cut styles

| | **Walkthrough styles** | **Viral cut / FX styles** |
|---|---|---|
| Motion | One continuous take | One clip with internal hard cuts |
| Storyboard | Path board (9 or 12 panels) | Shot-list board (12 panels) |
| Energy | Calm → cinematic → fast | Punchy, beat-synced, FX-driven |
| Default aspect | Per style (often your choice) | 9:16 |
| Best for | Listings, luxury, agent brand | TikTok / Reels / Shorts scroll-stop |

> **Creator Mode** bridges them: keep a walkthrough look, add viral pacing on top. (Available on all walkthrough styles except Story.)

---

## ⚙️ Choosing the engine

| Pick **Seedance 2.0** (default) when… | Pick **Marketing Studio** when… |
|---|---|
| You want a true continuous one-take **or** an internal-cut edit | You want a product-template/brand-spot look |
| You want the full 15s (cuts included) in a single render | You already have an MS product flow going |
| You want native audio + VO timing in-engine | You'll handle all audio in post |

> **Hyper Motion** is *not* a Marketing Studio mode — for continuous or hard-cut looks, use Seedance.

---

## 🔊 Audio

- **Music ON** → Seedance lays a native audio bed (scratch track — swap a licensed cue for delivery).
- **Voiceover ON** → a timed script is written and voiced via Higgsfield TTS, and the video is built around it.
- **Both ON** → VO in-engine; add licensed music in post.
- **Both OFF** → silent clip.

> Standalone *music generation* isn't available in this pipeline, so a licensed track is always a post step.

---

## ⚠️ Honest limits

- On-screen text (hooks, stat cards, CTA) is **baked into the storyboard and rendered in the clip** — no post pass. (Very long lines or a specific font are the only reasons to add it in post.)
- Native music is a **scratch bed** → replace with a licensed track for delivery.
- Marketing Studio renders **silent** → all audio is post for that engine.
- Cut styles are still **one clip** — the hard cuts happen inside a single render, not a separate edit.
- A front → backyard → front move isn't a real oner → the closing exterior is a clean **beauty-card cut**.
- A floor plan is a **planning input** (it shapes how the storyboard is built); the video model can't navigate a blueprint, so the plan itself only appears on screen if you opt into the orientation beat.

---

## 📁 Repository structure

```
mad-prompters-real-estate-studio/                <- repo root
├── README.md
├── LICENSE
├── CHANGELOG.md
├── RELEASE_NOTES.md
├── .gitignore
└── mad-prompters-real-estate-studio/            <- the installable skill (add this folder to Claude)
    ├── SKILL.md
    └── HOW-TO-USE.md
```

---

## 🔓 Get the skill — follow The Mad Prompter everywhere

- **Instagram** — https://www.instagram.com/themadprompter/
- **Threads** — https://www.threads.net/@themadprompter
- **X** — https://x.com/TheMadHatterTTV
- **TikTok** — https://www.tiktok.com/@themadprompter
- **YouTube** — https://www.youtube.com/@imthemadprompter
- **Facebook Group** — https://www.facebook.com/groups/1217551523840839
- **Facebook Page** — https://www.facebook.com/profile.php?id=61587989612009
- **LinkedIn** — https://www.linkedin.com/in/themadprompter/
- **Discord** — https://discord.gg/kW6sNSnR75

---

## 📜 License

MIT © 2026 Marco Figueroa-Mitsakos (**The Mad Prompter** / Mad Prompters). See [LICENSE](LICENSE).

Built for **Mad Prompters University** & **Higgsfield** creators.
