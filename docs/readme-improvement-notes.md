# README redesign — improvement notes for handoff

**Purpose:** Levi is undecided on the `readme-redesign` branch. This document captures what's wrong, what's working, and specific next steps another agent (or human) can take **without pushing the profile further into badge/widget overload.**

**Repo:** `levimackay/levimackay` (GitHub profile README repo)  
**Branch with redesign:** `readme-redesign`  
**Default branch (live profile):** `main`  
**Local path:** `/Users/levimackay/Developer/levimackay`

---

## 1. Executive summary

The redesign went from "clean editorial" → "maxed out employer pitch." Levi likes parts of it but isn't sure overall. The core tension:

| Original `main` README | Current `readme-redesign` |
|---|---|
| Terminal aesthetic, compact, ~125 lines | Same terminal aesthetic + many widgets, ~252 lines |
| 3–4 third-party services | 12+ third-party services |
| Self-hosted streak SVG (reliable) | Streak + 6 other contribution visualizations |
| Content-first | Metrics-first, Lydia repeated 6× |

**Likely best direction:** Keep the **custom banner**, **employer copy**, and **Lydia spotlight** — trim redundant stats/widgets back toward `main`'s restraint. Think "impressive above the fold, collapsible proof below," not "every GitHub profile widget ever made."

---

## 2. Current file inventory (branch `readme-redesign`)

| File | Role |
|---|---|
| `README.md` | Profile content — primary edit target |
| `profile/banner.svg` | Custom animated header (hardcoded metrics) |
| `profile/streak.svg` | Self-hosted streak stats (updated daily by Actions) |
| `.github/workflows/streak-stats.yml` | Renders streak to `profile/streak.svg` — **exists on main, keep** |
| `.github/workflows/snake.yml` | Generates contribution snake → `output` branch — **only on redesign branch, not merged** |

---

## 3. Verified facts (use these; do not invent)

Source: GitHub API + [levimackay.com](https://levimackay.com) as of 2026-08-17.

| Fact | Value | Notes |
|---|---|---|
| GitHub username | `levimackay` | |
| GPA | 3.98 | Stated in README and portfolio |
| Graduation | December 2027 | |
| Internship target | Summer 2027 SWE | |
| Lydia repo | `levimackay/lydia-cli` | 36 stars, 8 forks |
| PreCheck AI repo | `levimackay/PrecheckAI` | 0 public stars |
| Commit contributions (current year) | ~2,125 | From GraphQL `contributionsCollection` |
| Total owned repos (GraphQL) | 52 | Includes private; 30 public per REST |
| Portfolio URL | `https://levimackay.com` | Contact section: `/#contact` |
| LinkedIn | `linkedin.com/in/levi-mackay-217380396` | |

**Portfolio projects not on public GitHub (link to portfolio, not invented repos):**
- RexNest — student housing comparison for BYU-Idaho renters
- canvas-risk — Canvas LMS API risk scoring
- Main Street Sites — live web design studio (Sandbox accelerator)

**Do NOT add without verification:**
- Email address (portfolio uses terminal UI, no public mailto confirmed)
- Response-time promises ("I reply in 24h")
- Client names, revenue, download counts, testimonial quotes
- Star counts rounded up — Lydia is 36, not "40+"

---

## 4. Known bugs and broken elements

### 4.1 Contribution snake (broken until merged + workflow runs)

- `README.md` lines 210–214 reference:
  - `https://raw.githubusercontent.com/levimackay/levimackay/output/github-contribution-grid-snake.svg`
  - `...snake-dark.svg`
- `snake.yml` only exists on `readme-redesign`. GitHub Actions schedules run from **default branch** (`main`).
- **Fix:** Merge `snake.yml` to `main`, run workflow manually (`workflow_dispatch`), confirm `output` branch exists with both SVGs.
- **Until fixed:** Broken image icons in README — looks worse than no snake.

### 4.2 Hardcoded metrics in `profile/banner.svg`

Lines 60–67 bake in `2,100+ commits`, `36★ Lydia`, `52 repos`. These go stale.

- **Fix option A (recommended):** Remove metrics from banner; keep name + "OPEN TO WORK" + tagline only. Let dynamic shields below handle numbers.
- **Fix option B:** Add GitHub Actions workflow (like streak) that regenerates banner SVG or a companion `profile/metrics.json` — higher effort, probably overkill.

### 4.3 Possible SVG encoding corruption

`profile/banner.svg` line 65 may render as `36 Lydia` instead of `36★ Lydia` (encoding issue in source). Verify rendered output on GitHub after merge.

### 4.4 PreCheck "Try it — live demo" badge (line 115)

Links to GitHub repo, not a hosted demo. Misleading to recruiters.

- **Fix:** Change to `View on GitHub` or link to actual demo URL if one exists on portfolio.

### 4.5 Third-party rate limits (historical)

`CHANGELOG.md` documents streak-stats.demolab.com failure → migrated to self-hosted `profile/streak.svg`. Same risk applies to:
- `github-readme-stats.vercel.app`
- `github-profile-summary-cards.vercel.app`
- `github-profile-3d-contrib.vercel.app`
- `github-readme-activity-graph.vercel.app`
- `github-profile-trophy.vercel.app`
- `readme-typing-svg.demolab.com`
- `quotes-github-readme.vercel.app`
- `komarev.com/ghpvc`
- `skillicons.dev`

**If any show broken images:** Prefer self-hosted SVG via Actions (pattern already established in `streak-stats.yml`) or remove the widget.

---

## 5. What's working — keep these

1. **Custom `profile/banner.svg`** — Differentiates from generic profile READMEs. Animated but self-hosted (no third-party rate limit). Just trim hardcoded stats.
2. **`> cat /dev/why_hire_me` diff block** — Strong employer copy; leads with Lydia + shipped work. Best section in the redesign.
3. **`> currently.building()` JSON** — Compact status; matches original terminal voice.
4. **Lydia two-column spotlight** (lines 82–121) — "Why it matters to employers" is the right framing. Keep one Lydia deep-dive, not three.
5. **Repo pin cards for Lydia / PreCheck / FORGE** — Good visual proof. Consider 2 cards (Lydia + FORGE) if width is tight on mobile.
6. **Projects table with RexNest, canvas-risk, Main Street Sites** — Aligns README with portfolio; fills gap original README had.
7. **Self-hosted `./profile/streak.svg`** — Proven pattern; keep over remote streak widget.
8. **Green/black brand (`#00FF9D` on `#000000`)** — Consistent with portfolio terminal aesthetic.

---

## 6. What's too much — trim these (priority order)

### Tier 1 — Remove or collapse first (high noise, low employer value)

| Element | Lines | Why trim |
|---|---|---|
| Random dev quote | 241 | Generic quote unrelated to Levi; interrupts contact CTA |
| Profile views (komarev) | 16 | Vanity metric; employers don't care; external dep |
| 3D contribution graph | 168–171 | Redundant with activity graph + streak + snake; slow to load |
| Trophy grid (7 columns) | 164 | Generic gamification; clutters; many profiles have identical trophies |
| Summary cards row (3 cards) | 157–161 | Overlaps with stats cards directly above; different theme (monokai) |
| Duplicate animated GIF dividers | 29, 64, 123, 143, 191, 216 | Same GitHub-hosted GIF used 6× — feels templated, adds scroll length |

### Tier 2 — Keep one, remove the others (pick your favorite contribution viz)

Current README has **five** contribution visualizations:
1. Stats card (commits total) — line 153
2. Activity graph — line 199
3. Streak SVG — line 204
4. Snake — lines 210–214
5. 3D graph — line 170

**Recommendation:** Keep **streak SVG** (self-hosted) + **activity graph** OR **snake** (one remote). Drop the rest.

### Tier 3 — Reduce repetition

Lydia 36★ / 8 forks appears in:
- Typing SVG line 9
- Impact badges line 23
- `why_hire_me` line 39
- Repo pin card line 74
- Spotlight section lines 86–99
- Projects table line 137

**Recommendation:** Full treatment once (spotlight section). Elsewhere, link without repeating star count.

Static impact badges (lines 20–27) duplicate banner + dynamic Lydia shield. **Keep dynamic shields only** (`img.shields.io/github/stars/...`) so numbers stay current.

---

## 7. Specific improvement proposals (actionable for next agent)

Each item: **effort** (S/M/L), **impact** (1–5), **risk of "too much"** if added badly.

### 7.1 Structure: above-the-fold / below-the-fold split

**Effort:** S · **Impact:** 5 · **Risk:** Low

Wrap everything from `> github.metrics` (line 147) through snake in a single collapsible:

```markdown
<details>
<summary><code>> github.metrics</code> — click to expand</summary>
... stats, trophies, graphs, snake ...
</details>
```

Recruiter sees: banner → typing → links → why_hire_me → currently → spotlight → projects → contact.  
Developer/hiring manager can expand proof. Matches Levi's "not sure how I feel" — likely wants impressiveness without scroll fatigue.

### 7.2 Unify visual theme

**Effort:** S · **Impact:** 3 · **Risk:** Low

Current themes mixed: `synthwave`, `monokai`, `onedark`, `neon`, `react-dark`.

Standardize all `github-readme-stats` and activity graph URLs to:
```
theme=synthwave&bg_color=000000&title_color=00FF9D&icon_color=00FF9D&text_color=ffffff&hide_border=true
```

Remove summary cards entirely OR regenerate all three with a custom theme param if supported — don't leave monokai next to synthwave.

### 7.3 Replace GIF dividers with one custom element

**Effort:** M · **Impact:** 3 · **Risk:** Low

Create `profile/divider.svg` — thin green line + optional subtle pulse. Use 2× max (after hero, before contact). Removes dependency on `user-images.githubusercontent.com/74038190/...` (not Levi's asset; common template tell).

### 7.4 Auto-update dynamic metrics; static banner stays clean

**Effort:** S · **Impact:** 4 · **Risk:** Low

In `profile/banner.svg`, delete the metrics `<text>` block (lines 59–68). Keep OPEN TO WORK pill + name + tagline + cursor.

Add one row of **dynamic** shields below typing SVG:
```markdown
<img src="https://img.shields.io/github/stars/levimackay/lydia-cli?style=flat-square&label=lydia&color=000000&labelColor=000000"/>
<img src="https://img.shields.io/github/followers/levimackay?style=flat-square&label=followers&color=000000&labelColor=000000"/>
```

Do NOT workflow-automate commit counts unless willing to maintain another Action.

### 7.5 Add Lydia CI badge (if tests exist)

**Effort:** S · **Impact:** 4 · **Risk:** Low

Portfolio mentions "Tests passing in CI on Python 3.11 to 3.13." Verify badge exists:
```
https://github.com/levimackay/lydia-cli/actions/workflows/<workflow>/badge.svg
```
Add next to Lydia star/fork badges in spotlight. Stronger employer signal than trophies.

### 7.6 Middle-ground README variant (recommended merge target)

**Effort:** M · **Impact:** 5 · **Risk:** Low

Compose a `readme-redesign-v2` by **merging**:

| From `main` | From `readme-redesign` |
|---|---|
| Terminal section headers (`> whoami` style) | Custom banner.svg |
| Compact projects table (no emoji column if preferred) | `why_hire_me` + portfolio projects |
| Single streak SVG | Lydia spotlight (shortened) |
| Typing SVG (original 4 lines, less "Hire me") | 2 repo pin cards (Lydia + FORGE) |
| Skill icons row | Contact CTA badges |

| Drop from redesign |
|---|
| 3D graph, trophies, summary cards, random quote, komarev, capsule footer (or keep footer only) |

Target length: **~160 lines** (between main's 125 and redesign's 252).

### 7.7 Typing SVG tone adjustment

**Effort:** S · **Impact:** 2 · **Risk:** Low

Current line 9 includes `Hire+me+for+Summer+2027` — may read eager vs confident.

Suggested lines:
```
I+build+tools+developers+actually+use
36%E2%98%85+open+source+AI+coding+agent
Startup+founder+%C2%B7+CS+TA+%C2%B7+3.98+GPA
Open+to+Summer+2027+SWE+internships
```

Swap last line from imperative "Hire me" to declarative "Open to."

### 7.8 Mobile layout fixes

**Effort:** M · **Impact:** 3 · **Risk:** Low

GitHub README tables and side-by-side `<img>` tags don't stack on mobile.

- Repo pin cards (3× `height="180"`): reduce to 2, or stack vertically with `width="100%"` instead of side-by-side center.
- Lydia/PreCheck two-column `<table>`: acceptable on mobile (GitHub stacks `<td>`).
- Trophy 7-column: remove entirely (see Tier 1).

Test by viewing profile on phone or narrow browser.

### 7.9 Link hygiene

**Effort:** S · **Impact:** 3 · **Risk:** Low

| Link | Issue | Fix |
|---|---|---|
| RexNest, canvas-risk → `levimackay.com/` | Generic | Point to `levimackay.com/#work` or specific anchor if portfolio has one |
| PreCheck demo badge | Misleading | Rename badge or add real demo URL |
| Sandbox accelerator | Missing link in `why_hire_me` | Add `https://www.byui.edu/sandbox` where mentioned |

When/if RexNest and canvas-risk go public on GitHub, swap portfolio links for repo links and add pin cards.

### 7.10 Merge checklist (before shipping to `main`)

```
[ ] snake.yml merged to main; workflow run; output branch SVGs exist
[ ] No broken image placeholders visible on profile
[ ] banner.svg renders correctly (star character, animations)
[ ] All stats match API (Lydia stars, commit count wording)
[ ] No invented contact info or promises
[ ] CHANGELOG.md entry added (repo convention)
[ ] Levi approves above-the-fold in GitHub preview (not just local markdown)
[ ] Light mode check — snake <picture> sources swap correctly
```

---

## 8. Things NOT to add (will cross into "too much")

- WakaTime / Spotify now-playing — no evidence Levi uses these publicly
- Fake testimonials or "used by X companies"
- More emoji in table first column — already 9 rows with emoji; original had none
- Second typing SVG or marquee text
- Blog/RSS embed — no public blog URL found
- Canvas animation, Lottie, embedded video — GitHub sanitizes most of this
- Additional capsule-render headers (already have custom banner + optional footer)
- `github-readme-streak-stats` remote widget — revert risk after 2026-07-17 fix
- More than 3 repo pin cards
- Auto-playing audio (obviously)

---

## 9. Comparison: section-by-section map

| Section | `main` (live) | `readme-redesign` | Suggested v2 |
|---|---|---|---|
| Header | Typing SVG only | banner.svg + typing + badges + metrics | banner.svg + typing + 3 link badges |
| About | `> whoami` bullets | `> cat /dev/why_hire_me` diff | Keep diff (stronger) |
| Status | `> currently.working_on()` | `> currently.building()` | Keep (rename either is fine) |
| Featured | PreCheck only | Pin cards + Lydia/PreCheck table | Pin Lydia + FORGE; PreCheck in table |
| Projects | 6-row table | 9-row table + portfolio projects | 9-row table (good addition) |
| Stack | skillicons + 3 badges | same + 2 more badges | same as main |
| Stats | streak SVG only | 7 widgets | `<details>`: activity graph + streak + snake |
| Contact | JSON block | JSON + 3 CTA badges | JSON + 2 badges |
| Footer | "Let's build something real." | quote + capsule footer | text tagline only (match main voice) |

---

## 10. Git workflow for next agent

```bash
cd /Users/levimackay/Developer/levimackay
git fetch origin
git checkout readme-redesign   # or create readme-redesign-v2 from here

# Preview without merging to profile:
# GitHub → Settings → Profile → "Link to repository" already points here
# Profile README always renders from default branch (main) unless testing via branch view

# To merge when Levi approves:
git checkout main
git merge readme-redesign
git push origin main
```

**Note:** Profile README displays from **`main` only**. Branch preview URL:  
`https://github.com/levimackay/levimackay/tree/readme-redesign`  
Raw README preview won't show on github.com/levimackay until merged.

---

## 11. Levi's stated preference signals (from conversation)

1. Liked the animated/max direction more than the minimal editorial pass — **keep motion and personality**.
2. Felt redesign is **"pretty similar to what I already have"** — needs clearer differentiation; custom banner + employer copy + portfolio projects are the real upgrades over main.
3. **Uncertain overall** — suggests offering A/B choice rather than more widgets:
   - **Option A:** Merge middle-ground v2 (section 7.6)
   - **Option B:** Keep main, cherry-pick only banner + why_hire_me
   - **Option C:** Stay on redesign, only execute Tier 1 trims

Ask Levi which option before merging to `main`.

---

## 12. Reference URLs (widget templates)

Replace `levimackay` / colors as needed.

```text
# Typing
https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1200&color=00FF9D&center=true&width=620&lines=LINE1;LINE2;LINE3

# Stats
https://github-readme-stats.vercel.app/api?username=levimackay&show_icons=true&theme=synthwave&hide_border=true&bg_color=000000&title_color=00FF9D

# Top langs
https://github-readme-stats.vercel.app/api/top-langs/?username=levimackay&layout=compact&theme=synthwave&hide_border=true&bg_color=000000&title_color=00FF9D

# Repo pin
https://github-readme-stats.vercel.app/api/pin/?username=levimackay&repo=lydia-cli&theme=synthwave&hide_border=true&bg_color=000000&title_color=00FF9D

# Activity graph
https://github-readme-activity-graph.vercel.app/graph?username=levimackay&theme=react-dark&hide_border=true&bg_color=000000&color=00FF9D&line=00FF9D

# Dynamic star badge
https://img.shields.io/github/stars/levimackay/lydia-cli?style=for-the-badge&color=00FF9D&labelColor=000000
```

---

## 13. CHANGELOG entry template (when shipping)

```markdown
## 2026-08-XX
- README redesign v2: custom banner, employer-focused copy, portfolio projects (RexNest, canvas-risk, Main Street Sites).
- Added snake workflow (`.github/workflows/snake.yml`) for contribution animation on `output` branch.
- Trimmed redundant stats widgets; collapsed metrics section into `<details>`.
- Kept self-hosted streak SVG pattern (no third-party streak dependency).
```

---

*Last updated: 2026-08-17 · Author: Cursor session on `readme-redesign` branch*
