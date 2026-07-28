# Changelog

All notable changes to **Mad Prompters Real Estate Studio** are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/); versioning follows [SemVer](https://semver.org/).

## [1.5.1] - 2026-06-28
### Changed
- **Engine-aware photo budget.** Hero selection now scales to the chosen engine: **Marketing Studio → 4–6 hero photos**; **Seedance 2.0 → up to 8 images total, storyboard included** (board + up to 7 plates, one `start_image` + one `end_image`, up to ~5 interior `image` plates). Triage, the Seedance medias in Phases 5–6, the engine table, and the cheat sheet all reflect the cap.

## [1.5.0] - 2026-06-27
### Added
- **Floor Plan Lock (optional).** Provide a floor plan and the skill uses it as a spatial map: it labels unlabeled photos by room, orders the walkthrough by real adjacencies, and tags every transition glide-vs-cut. The room-match confirmation folds into the existing hero-approval gate (no new stop), with an opt-in floor-plan "you-are-here" beat (default off).
### Notes
- The plan is a **planning input for the storyboard, not a runtime input for the video model** — the plan image only enters the render if the orientation beat is requested; otherwise it stays a behind-the-scenes planning tool. No plan provided → the skill falls back to the standard best-guess beat order.

## [1.4.0] - 2026-06-26
### Added
- **Viral cut / FX presets (3).** **Viral Cut**, **FX Showcase**, and **Hype Reel** — fast, beat-synced edits rendered as a single 15-second Seedance clip with **internal hard cuts** (no stitching). FX and cuts land only on locked frames, so a fast edit still can't morph.
- **Creator Mode.** A toggle that layers viral pacing — punch-in/out zooms, speed ramps, beat-sync, and 2–4 hard cuts — onto any walkthrough preset **except Story**. Keeps the base look; bumps to 12 beats.
- **On-screen text, rendered in-clip.** When a cut preset or Creator Mode is active, the skill asks whether you want text hooks and offers a menu (Hook+payoff / Stat cards / CTA punches / Custom), confirms the exact lines, and **bakes them into the storyboard panels so they render in the video** (no post pass; post only as a fallback).
- **Family-first style selection.** With 10 presets, intake now selects in two quick taps (Walkthrough vs Viral-Cut vs Recommend → ≤4 curated presets) so it still fits the tappable picker.
- **Phase 5C cut-style prompt template** plus a Creator Mode modifier block.
### Changed
- Storyboard now supports **two board kinds**: a continuous **path board** (9/12 panels) and a **shot-list board** (12 panels) for cut presets.
- Cut presets default to **9:16** and `genre: action`.
### Fixed
- **Twilight Glam NSFW false-trip.** Locked the preset to *warm evening / amber / golden-hour* wording — never "sensual / dusk / glowing / dark," which was tripping Seedance's NSFW filter and refunding jobs.

## [1.3.0] - 2026-06-25
### Added
- **Style Preset Library (7 presets).** Smooth Glide (default), Luxe Cinematic, FPV Rush, Bright & Airy, Twilight Glam, Social Pop, and Story (Narrated) — each a bundle of camera energy, transitions, beat count, color grade/time, genre, and audio default.
- **Style-first intake.** Pick a look at the start; the chosen preset pre-fills the defaults so you only answer what's left.
### Changed
- High-energy presets (FPV Rush, Social Pop) use **12 storyboard beats** (3×4) instead of 9, snapping only on blooms to stay morph-free.

## [1.2.0] - 2026-06-25
### Added
- **Spurious-preset defense.** On Seedance runs, auto-matched Higgsfield presets (e.g. "IN THE DARK") are declined and the literal prompt is generated, unless the user explicitly chose a preset.
- **Tappable intake.** Engine, aspect, and audio are presented as button-select options for faster mobile intake.
- **Property-tier flexibility.** Vibe and copy adapt to any tier — luxury estate to updated starter/character home — with explicit guidance not to force "luxury" framing onto a mid-market listing.
### Changed
- **Storyboard orientation now follows the delivery aspect** (`3:2` for 16:9, `2:3` for 9:16, `1:1` for square) so panels preview the real framing.
### Fixed
- Upload widget capped at **20 files per batch**; triage now runs **before** upload so only the chosen hero shots are uploaded. Filename-based media mapping.

## [1.1.0] - 2026-06-25
### Added
- **Dual-engine support** — Seedance 2.0 (default, single-clip one-take) alongside Marketing Studio.
- **Music on/off** and **voiceover on/off** toggles.
- **Timed 15-second hook/body/CTA script** plus in-pipeline text-to-speech voiceover generation.

## [1.0.0] - 2026-06-25
### Added
- Initial release: morph-free 15-second real-estate walkthrough via Higgsfield Marketing Studio.
- Sequential intake, best-shot triage from up to 30 photos, locked 9-panel storyboard, and positional `@image_N` prompt.
