# Omar's Unreal Engine job radar

Public site: https://mshokry10.github.io/pages/omar-unreal-jobs/

This folder contains a mobile-friendly, zero-build static job board for Omar, an early-career game developer based in Cairo, Egypt. The site uses `index.html` to read `jobs.json` on every load. There are no spreadsheet, server, API key or external JavaScript dependencies.

## Research brief

The goal is Omar's **first professional Unreal Engine / gameplay development role**, including legitimate junior, early-career, graduate-eligible, internship and paid contract positions. Prioritise UE4/UE5 C++, Blueprints, gameplay and AI programming, technical gameplay, XR/VR, simulation, real-time 3D, Unreal technical artist/animator, architectural/automotive visualisation and digital twins. Consider suitable Unity / C# jobs when a credible career bridge, but Unreal comes first. Never recommend customer support or helpdesk.

Omar: BSc Computer Science, graduated in **2024**; no commercial developer experience. Portfolio projects are *independent/personal*, not commercially shipped:
- **Echoes of Annihilation** — UE4, C++, third-person PC shooter, enemy AI, perception, combat, navigation.
- **The Other Side** — UE5 C++, PC/VR, AI-driven NPCs, procedural resources, MetaHuman, Maya.
- **Project Zero Requiem** — UE5, AI, motion capture, animation pipelines, cinematics, traversal.

Additional skills: Unreal C++/Blueprints, Unity/C#, Maya, Blender, SketchUp, JavaScript, Node.js, Python and Git. Prior support employment should not be presented as programming employment.

## Dataset contract

`jobs.json` is the single canonical archive. Its top-level keys are:
- `schema_version`: 1
- `updated_at`: ISO date of last dataset update
- `last_search_at`: ISO date of last daily search attempt (update even with no new jobs)
- `research_note`: short status/context
- `scoring_weights`: stable five-criterion weights
- `jobs`: array of job records (append + update; never erase history)
- `sources_reviewed`: a short list of important websites/sources checked on the last run

Every record needs:
`id` (stable, slug-like string), `first_seen`, `last_verified`, `employer`, `title`, `city`, `country`, `region`, `work_mode`, `employment_type`, `experience`, `skills` (array), `salary` (only genuine advertised salary or "Not disclosed"), `fit_score` (integer 0–100), `status`, `egypt_eligibility`, `egypt_eligibility_status`, `visa_status`, `summary`, `why_fit`, `caveats`, `source_type`, `source_url`, `apply_url`.

Allowed values:
- `region`: `remote` (confirmed work-from-Egypt eligible), `egypt` (Egypt-based), `europe` (UK/Europe with credible confirmed visa/relocation pathway), `stretch` (interesting but geography/authorisation not confirmed or challenging)
- `status`: `open` (recent evidence from live original source), `needs_verification` (listing exists but current vacancy, legitimacy or application path uncertain), `closed` (confirmed ended)
- `egypt_eligibility_status`: `confirmed`, `unknown`, `no`
- `source_type`: `employer` or `third_party`

Score with: realistic hiring probability 30%, direct Unreal relevance 25%, geographical/legal feasibility 20%, salary and progression 15%, mentorship/employer quality 10%. Never let a prestigious but impossible job outrank an accessible junior role. State specific project-fit and gaps, including 2024 graduation restrictions. Mark sponsorship as confirmed only with evidence for **that exact vacancy**.

## Daily-update rules for ChatGPT

1. Search **fresh** official careers pages and diverse sources: LinkedIn, Work With Indies, Hitmarker, GamesJobsDirect, GameJobs.co, DevQuest, thehive.games, employer Greenhouse/Lever/Ashby, remote boards and Egyptian/MENA sites; also XR/VR, archviz, virtual production, automotive and simulation employers. Aim for broad coverage, not 2–3 recycled searches.
2. Check original vacancy pages and ensure applications appear open; prefer direct employer links. Do not treat a search snippet as verification. Don't re-add dead postings. Confirm if remote means *Egypt eligible*; "remote USA" does not count. For international moves verify role-specific sponsorship; otherwise put in `stretch`.
3. Fetch latest `jobs.json` from branch `main` before modifying it. Deduplicate first by normalized original posting URL or ATS job ID, then by employer + title + location. Preserve each existing `id` and `first_seen`.
4. **Append** genuinely new roles. Update details and `last_verified` for existing roles actually rechecked; do not pretend old listings were reverified. If a role is proven closed, set `status:closed` and keep it in history. If unconfirmed, keep `needs_verification` instead of falsely marking closed/open.
5. Maintain all fields, valid HTTPS URLs, JSON syntax, accurate dates, score weights and no duplicate IDs. Never invent salary, visa support or internship eligibility. Do not publish Omar's CV, email or any private data in the repo.
6. Fetch the file's latest blob SHA and update only `omar-unreal-jobs/jobs.json` on `mshokry10/pages` `main` using the GitHub connection's file-update action. If a conflict occurs, re-fetch and merge safely. Do not edit HTML in the daily task.
7. Update `last_search_at`, `sources_reviewed` and `research_note` even when no new role qualifies. Summarise newly found, updated and closed jobs, action priorities and publication success/failure to the ChatGPT user. Do not claim website updated unless the GitHub write succeeds.
8. Never republish roles that require US-only or EU-only residency as "remote from Egypt". Exclude full-time customer support, unrelated internships, volunteer-only work and roles with hard 2025/2026 graduation rules that Omar (2024) fails.

**Publishing:** The repository currently follows a static GitHub Pages pattern where `main` serves `/pages/`. Pushing the JSON file is enough for the site to fetch updated content once GitHub Pages deploys the new commit. No GitHub Actions workflow is required for ChatGPT-led research.

**Manual maintenance:** Edit `jobs.json` in GitHub or through ChatGPT's connected GitHub tool. No Excel/Google Sheet sync is required. The site is public, and saved search filters are not stored server-side.
