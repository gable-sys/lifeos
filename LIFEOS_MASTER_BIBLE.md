# Life OS — Master Project Bible
### "Make the good path the easy path."
**Updated: June 2026 · Give this to any new chat to get fully up to speed.**

---

## THE PHILOSOPHY

Life OS is not a productivity app. It is a **rebellion against the attention economy**.

Most software is designed to maximize engagement, to keep you scrolling, to feed you dopamine hits that hollow you out. Life OS does the opposite. Success is measured by **reduced screen dependency**, not more time on the app. It shows you what matters, reminds you of beauty, and gets out of the way.

The aesthetic is the argument: old Penguin paperbacks, Hopper diners, Cartier-Bresson photographs, Arvo Pärt, cork boards with real notes on real paper. These aren't decorations. They're a worldview. The product says: **there is a richer life than the one the algorithm wants for you.** Lean into great books, classical and world music, physical craft, slow cinema, handwritten letters. Not as universal prescription but as an honest expression of taste.

The tagline: **Make the good path the easy path.** The dashboard surfaces the things you actually want to do — work out, read, write, call your people — so they're always one tap away and never buried under notifications.

This is what "vibe coding" should be: not just AI-assisted code generation, but **AI helping humans build digital spaces that have genuine soul**. The world is flooded with efficient, soulless, optimized software. Life OS is the counter-argument built in code.

---

## WHO GABE IS (context for the AI)

- Lives between **Brooklyn/Dumbo** (subletting from Nikolaj, a Danish landlord, ~$2,200/mo with roommates Leo and Gus contributing) and **La Crosse, WI** (works with brother Connor at Health Benefits 360)
- Musician: guitar, piano, banjo — practices guitar in Wisconsin, piano resumes in NYC
- Writer: **Zen Gun** creative brand — short stories, MiniDV film (*The Drinker*, shot in Denmark/Bornholm), songwriting project *Slumber Dance*
- Early in coding — learning through building this, treats Claude as a proactive handler not just a tool
- Sober streak started May 31, 2026
- Physical goals: V-taper, June 21 solstice peak target, Bryan Johnson protocol reference
- Financial: Discover it Secured card to rebuild credit, Roth IRA at Fidelity (FXAIX) once stable
- Denmark trip Jun 12-16, back to Brooklyn Jun 14-15

---

## CURRENT TECHNICAL INFRASTRUCTURE

### Frontend
- **Live site**: `stupendous-concha-2d70be.netlify.app`
- **Repo**: `github.com/gable-sys/lifeos` — file is `index.html`
- **Deploy**: Upload new `index.html` to GitHub → Netlify auto-deploys in ~30s
- **Netlify Pro**: Upgraded June 2026 — no build minute limit, no file size ceiling
- **Working file**: `/mnt/user-data/outputs/lifeos_v4.html` — the current version as of this session

### Backend
- **Render service**: `https://lifeos-backend-nf15.onrender.com` (Python/Flask, free tier, ~50s cold start)
- **Repo**: `github.com/gable-sys/lifeos-backend` — edit `app.py` via GitHub pencil
- **Env vars on Render**: `PLAID_CLIENT_ID`, `PLAID_SECRET` (production), `PLAID_ENV=production`
- **Endpoints**: `/create_link_token`, `/finish_link`, `/balance`, `/transactions`

### Database
- **Supabase**: project `lifeos`, table `lifeos_data`
- **Supabase URL**: `https://gruebngputtvwbhroswc.supabase.co`
- **Rows**: calendar, dating, stories, wiki, checks, finance, plaid_state
- **Status**: Not fully wired into app — persistence is the next big infrastructure push

### Bank Integration (Plaid)
- **Production approved** ~June 2026
- **Client ID**: `6a00fbf3ef2ece000e243a6c`
- **BofA will work** once Full Production + OAuth registration complete (no code changes needed)
- **Library**: `plaid-python v39.2.0` — only Sandbox and Production environments exist

### AI Advisors
- **Not live yet** — architecture planned, `CLAUDE_ENDPOINT` in frontend still points to `api.anthropic.com`
- **Plan**: add `/advisor` route to Render backend, proxy to Claude API
- **Model**: Sonnet for advisors, Haiku for Mr. Greg (high volume ACA)
- **Memory**: Must be built ourselves in Supabase — Claude API has no memory between calls

### Google/Apple Integrations
- **Personal Google Calendar**: `lonningb10@gmail.com` (use this, NOT the HB360 workspace)
- **Apple Reminders**: iCloud list ID `C0E2978F-28C5-4867-BC76-94F35F3DA362` (write-only)
- **Calendar event format**: `"start": {"date": "YYYY-MM-DD"}` for all-day; popup reminders 480-540 min; color ID 11 = financial, 3 = travel

---

## THE DASHBOARD — CURRENT STATE (v4)

### Visual Identity
- **Palette**: Cream/paper background (`#f4ecd6`), deep ink text, terracotta (`#bd441f`) and forest green (`#255637`) accents, gold (`#8f6219`)
- **Typography**: Fraunces (display/headings), Spectral (body serif), IBM Plex Mono (labels/code)
- **Aesthetic reference**: Old Penguin paperbacks, alchemical manuscripts, vintage dashboards, 8-bit pixel art for decorative elements

### Sections (top to bottom)
1. **Header** — "Life OS" masthead, night/day toggle, date
2. **Motograph Zipper Ticker** — dot-matrix pixel font, scrolling headlines (world news + personal life stats), amber on black
3. **Cork Board** — pinboard with scattered cards at varied positions:
   - Tarot card (rotates daily)
   - Paintings (Hopper, Magritte, Vermeer) — click opens Wikipedia
   - Photographs (Cartier-Bresson, Eisenstaedt) — click opens Wikipedia
   - Quote strip (Hemingway, Nietzsche, Dylan Thomas, Flaubert, Camus, Wilde)
   - Setlist card (rotating daily listening recommendations)
   - Oblique Strategy card (Brian Eno, rotating daily)
   - Radiator diagram (8-bit pixel art, click opens "The Radiator Plan" poem modal)
   - Guitar (8-bit SVG)
   - La Crosse Tribune newspaper clipping
   - Wanted poster (G. LONNING, $500 reward, dead or alive)
   - Zen Gun concert ticket (THE DRINKER · BORNHOLM)
   - Fortune slip (rotating daily wisdom)
   - Bornholm postcard
   - Filmstrip (The Drinker, MiniDV)
   - Todo/reminder cards (categorized: THIS WEEK, BUY NOW, ADMIN, DEPOP, ZEN GUN)
   - **Click board background** → opens La Crosse river scene modal
   - **Double-tap any card** → crumple/dismiss animation
   - **Ctrl+scroll** → zoom
4. **Three Portal Icons** (bottom):
   - **Celestial (moon icon)** → Moon/Planets/Phenomena/Sun tabbed modal with myth, astronomy, phenomena
   - **Wander (compass icon)** → Explorer/writer quotes, NYC event recommendations
   - **Time (clock icon)** → Countdowns, memento mori, week/day of year
5. **Departments** (modals behind the portals):
   - Finance (Plaid bank connection, ledger, advisor Constance)
   - Calendar/Schedule
   - Workout (Viktor advisor, weekly plan)
   - Music (Marguerite advisor)
   - Reading/Library (Aldous advisor)
   - Creative/Zen Gun (Flora advisor, 9 story projects)
   - Body (Dr. August advisor)
   - Lab/Odin Project (Mr. Greg advisor)
   - Wiki
   - Fridge
   - Closet
6. **Visiting Scholar** (floating) — 8-bit character, chat interface (Hemingway, Twain, Napoleon, Marcus Aurelius, Beauvoir)

### The River Scene Modal (La Crosse)
Opens when clicking cork board background. Canvas-based animated scene:
- Iowa bluffs, treeline, wide Mississippi River
- Steel truss bridge (above waterline, X-diagonals, lit at night)
- Casino Queen paddle wheel steamboat (animated paddle wheel, "CASINO QUEEN" text, smokestacks)
- Barge with cargo containers
- Coffee mug with steam on windowsill
- Cigarette (click to light, smoke wisps)
- Full board below the scene for easier reading
- **Add note input** — type and pin directly to board
- Day/night/sunset aware

When back in Brooklyn: swap to Dumbo/Manhattan Bridge scene.

---

## QUEUED FEATURES — PRIORITIZED ROADMAP

### Priority 1: Core Usability (build first)
**In-app editing** — the single most important missing feature. Right now everything requires redeployment. Users need to:
- Add/edit/delete reminders and todo cards directly from the board
- Edit workout plans, diet logs, schedule
- Add to advisor memory
- Change department layouts
All persisted via Supabase multi-tenant config layer. This is what makes it a real product vs a static dashboard.

**Smart reminders with full text** — cards show truncated version, click opens full note. Already partially implemented. Needs:
- Proper truncation at ~30 chars on card face
- Full text in modal on click
- Import/sync from Apple Reminders and Google Calendar
- Location/time triggered notifications

**Supabase persistence** — wire all state to Supabase so it syncs across devices and survives page refreshes. This unlocks multi-user.

### Priority 2: The Scene (next build session)
**Dumbo warehouse scene** for Brooklyn mode:
- Manhattan Bridge from the Dumbo side — Beaux-Arts granite towers, suspension cables, lit at night
- Brooklyn Bridge visible to the right
- Downtown Manhattan skyline — One WTC, Empire State Building
- East River, ferry crossing
- Warehouse window frame in foreground
- Sill: gin & tonic (condensation, lime, orange straw), shortwave radio with dial and antenna, ashtray

**Scene toggle** — when in La Crosse show Mississippi scene, when in Brooklyn show Dumbo scene. Auto-detect from IP or manual toggle.

### Priority 3: Media & Sound (high delight, medium effort)
**Shortwave Radio widget** — already designed, needs wiring:
- Streaming: BBC Radio 3, Danmarks Radio P8, Radio Classique, NRK Klassisk, Estonian public radio
- 8-bit radio on the windowsill, click antenna to tune

**Record Player / Gramophone** — 8-bit spinning platter on dashboard:
- Click to play recommended listening (the daily setlist card)
- Could play actual audio via embed
- Old jazz, Bach, whatever's cued that day
- Vinyl crackle sound effect

**Morning Radio Brief** (big feature, later):
- ElevenLabs voice, 1940s radio filter (bandpass EQ, vinyl crackle, slight distortion)
- Daily script auto-generated: real news headlines + your life stats + weather + sobriety day
- Hemingway or Cronkite voice style
- Could run at 8am automatically
- Voice clones via ElevenLabs Creator plan (sourced from YouTube/archive audio)

**Sound design throughout** — vintage/retro foley:
- Typewriter click on card open
- Paper shuffle on dismiss
- Old radio static on scene modal open
- Film projector on filmstrip click

### Priority 4: Creative Tools (Zen Gun integration)
**Creative Collage** per project:
- Pins: images, paintings, photos, tunes, color palettes, text scraps
- Céline/Henry Miller 1920s Paris poets' attic aesthetic
- Small per-project AI collaboration box (Flora advisor)
- Image repository sidebar, always visible

**Céline's Room** — writing desk modal redesign:
- Twine-strung papers, garret light
- Full-screen writing mode
- Links to actual story files

**Dream Journal** — Cocteau-style:
- Surreal door/mirror entry
- Type a dream → generates visual collage (AI image generation or assembled from PNGs/cutouts)
- Vision board energy
- Always present on dashboard

**Visiting Scholar voice clones** — ElevenLabs Creator:
- Hemingway, Mark Twain, Napoleon, Marcus Aurelius, Simone de Beauvoir
- 8-bit character appears, speaks in voice
- Conversations that persist in Supabase

**Book of the Day** — full public domain PDF in flippable format:
- Chuang Tzu, the Iliad, Arabian Nights, Marcus Aurelius
- Chapman and Pope translations of Homer

### Priority 5: Dashboard Surface (information architecture)
Currently all content is behind modals. Need key items visible inline:
- Book cover of current read (visible on dashboard, click to open Library modal)
- Workout preview (today's session, click to open full plan)
- Odin Project / CS50 link visible
- Finance balance visible (not behind modal)
- Partial content below headers with modal link

**Scrollable department pages** inside modals rather than fixed-height boxes.

**WIKI** — top-of-page link:
- Long-form articles growing over time like Wikipedia
- Personal knowledge base
- Possible Obsidian round-trip (export/reimport)

**FRIDGE widget** — food/grocery orders

**CLOSET widget** — links to Depop, clothing order triggers:
- Three looks: Americana/Workwear, Rocker/Poet, Hipster Hollywood 90s
- Buy order tracking

**MAP / Wander portal** (big feature):
- Daily auto-generated old/fantastical "mood maps" of current location + recurring places
- NYC Dumbo, East/West Village, NJ/Essex County, Decorah Iowa, Denmark + Bornholm, Belize
- Mariner/fantastical style with beasts, side quests, local treasures, café book recs
- Oracle/spirit/crystal ball energy advisor responding in limericks, riddles, oracular pronouncements

### Priority 6: Body & Looksmaxxing Department Overhaul
- AM/PM routine tally
- Daily checklist with completion tracking
- **Looksmaxxing score calculator** (weighted system):
  - Skincare (tret cadence, SPF, castor oil)
  - Workout (consistency, V-taper progress)
  - Diet (co-op food, creatine, collagen, beta carotene)
  - Sleep (mouth tape, back sleeping, 8hrs)
  - Grooming (brow gel, dye cadence, hair routine)
  - Hair protocol (finasteride, minoxidil, derma rolling, Olaplex)
  - Teeth (Whitestrips, Invisalign progress, composite bonding match)
  - Posture, mewing, gum work
- Bryan Johnson protocol reference
- Progress photo tracker (monthly, same lighting, same spot)
- Goals: V-taper by summer, neck size, cardio/lift combo days

### Priority 7: 8-bit Pixel Art & Decorative Elements
- **8-bit compass icon** in masthead
- **Calendar tiny icon** in masthead
- **Soul OS** — dark cinematic alternate skin
- **Alchemical sun/moon hero** — full-width illustration, day/night aware
- **8-bit pixel decorative elements** throughout: small icons for each department
- Fan blowing papers on cork board (animation)
- Vine growing on side of board
- Studio lamp (click on/off, night-aware)

---

## THE CELESTIAL MODULE — FULL VISION

Currently has 4 tabs: Moon / Planets / Phenomena / Sun

### Moon tab
- Current phase with emoji + name
- Today's date, diurnal/nocturnal arc label
- Myth from rotating traditions: Islamic, Greek, Hindu, Alchemical, Norse, Egyptian, Chinese, Babylonian
- Astronomy fact (tonight's sky, ISS passes, visible planets)
- Links: Stellarium, NASA APOD, La Crosse sky

### Planets tab
- Which planets are visible tonight
- 8-bit pixel art for each (Jupiter, Saturn, Mars, Venus)
- Visibility notes (what to look for, where in sky)
- Mythology and alchemy (Jupiter/Zeus/tin, Saturn/Kronos/lead, Mars/Ares/iron, Venus/Aphrodite/copper)

### Phenomena tab
- Summer Solstice (June 21 — your peak day, ancient significance)
- Perseid meteor shower (Aug 11-13 peak, 100/hour, Comet Swift-Tuttle debris)
- Great Comet Hale-Bopp (18 months naked eye, returns in 2,520 years)
- Aurora Borealis (solar maximum now, Wisconsin sightings, Kp index)
- Transit of Venus (next one 2117 — you will never see it)
- Historical context for each

### Sun tab
- June solstice — solar maximum, day length in La Crosse (~15hrs 20min)
- Sun's current constellation (Gemini → Cancer June 21)
- Solar altitude at noon (~68° in La Crosse in June vs 22° in December)
- Alchemical Sol/Luna mythology (Gold/Sulfur, active masculine principle)
- Greek: Helios, Apollo; Egyptian: Ra; Hindu: Surya; Roman: Sol Invictus

**Future additions**:
- Northern Lights alert integration (NOAA Kp index API)
- ISS pass times (NASA Spot the Station API)
- Daily astronomical picture (NASA APOD embed)
- Toggling between current phenomena and "this day in astronomical history"
- Deep space objects visible this month
- Astrology sidebar (purely as mythos/culture, clearly framed)

---

## THE TICKER — MOTOGRAPH ZIPPER

Dot-matrix pixel font (4px dots), amber on black, wrapping around the building like the original 1928 Times Square zipper. Each letter is a matrix of lit "bulbs."

**Format**: `[CATEGORY STAMP] HEADLINE TEXT ◆ [CATEGORY] NEXT HEADLINE ◆`

**Categories** (colored stamps):
- WORLD (gold) — real world news
- CULTURE (blue) — books, film, music, art
- SPORT (gold)
- MARKETS (orange)
- LIFE OS (green) — sobriety streak, body stats
- BODY (purple) — training, skin, health
- CASH (orange) — rent, payday, financial
- ZEN GUN (green) — creative project reminders

**Real news**: Currently static text. Future: pull from RSS feeds (AP, Reuters) via Render backend. Backend fetches headlines on a schedule, stores in Supabase, frontend pulls them.

---

## AI ADVISORS — PLANNED ARCHITECTURE

Seven personas, each with a distinct voice and domain:

| Advisor | Domain | Voice Style | Model |
|---------|--------|-------------|-------|
| Constance | Finance/ledger | Calm, precise, Swiss banker | Sonnet |
| Viktor | Workout/body | Terse, Eastern European coach | Sonnet |
| Marguerite | Music | French, romantic, opinionated | Sonnet |
| Aldous | Reading/library | Dry wit, very well-read | Sonnet |
| Flora | Zen Gun/creative | Encourages, asks hard questions | Sonnet |
| Dr. August | Body/looksmaxxing | Evidence-based, no nonsense | Sonnet |
| Mr. Greg | ACA lead qualifying | Warm, practical, HB360 voice | Haiku |

**Implementation**:
1. Get Anthropic API key at `console.anthropic.com`, add ~$5 billing
2. Add `anthropic` to `requirements.txt` on Render, add `ANTHROPIC_API_KEY` env var
3. Add `/advisor` route to `app.py` (draft exists as `advisor_route.py`)
4. Frontend: update `CLAUDE_ENDPOINT` to point to Render `/advisor`
5. Memory: store conversation history in Supabase per user per advisor

**Mr. Greg specifically** — eventually ships as a standalone ACA lead-qualifying chat widget for Health Benefits 360. Same advisor architecture, different persona, deployed on HB360 website. This is the revenue application of what we're building.

---

## BUZZARDS TRADING COMPANY — THE BIG IDEA

**The concept**: A service that sits inside Life OS (and eventually standalone) that lets users connect with each other and with people they care about through old-world, physical, charming means. Old world meets new world.

**Services**:
- **Snail mail letters** — user types a letter, Buzzards formats it beautifully (typewriter font, aged paper aesthetic), prints and mails it via a fulfillment service. Could use an API like Lob.com for programmatic mail.
- **Typewritten letters** — actual typewriter aesthetic, maybe printed on real aged/textured paper
- **Life OS Dispatches** — weekly or monthly printed newsletter sent to subscribers: your week in Life OS data, quotes, music recommendations, astronomical events, a Zen Gun excerpt. Physical artifact.
- **Music for the day** — curated daily listening recommendation sent as a physical card? Or just a dispatch
- **Radio dispatches** — audio companion to the newsletter (ties into Morning Radio Brief idea)
- **User-to-user** — Life OS users can send dispatches to other users: share a quote, a book recommendation, a recipe, a note from the cork board. Old postal system energy.

**The aesthetic**: Genuine vintage/handmade feel. Wax seals. Quality paper. The name "Buzzards Trading Company" evokes old frontier trading posts, Pony Express, the romance of physical commerce before the internet. Nothing ironic — played completely straight.

**Community vision**: Life OS as the hub, Buzzards as the connective tissue between members. The antithesis of social media engagement farming — slow, intentional, physical, real.

**Revenue model**:
- Subscription tier: $5-15/mo for Buzzards dispatch service
- Per-send: $3-8 per typewritten letter
- Gift subscriptions: "Send someone a Life OS dispatch for 3 months"
- Corporate gifting: businesses sending thoughtful mail to clients via Life OS aesthetic

---

## MULTI-USER VISION — SHIPPING TO OTHERS

**Timeline**: Next month (July 2026) — begin shipping to friends as guinea pigs.

**Architecture needed**:
- Supabase auth (email/password or OAuth)
- Per-user config stored in Supabase
- Each user has their own: departments data, card content, advisor history, reminders
- Shared: global ticker (world news), celestial data, oblique strategies, curated content

**Onboarding flow**:
1. Create account
2. Choose your location (city scene changes: NYC, La Crosse, Copenhagen, London, etc.)
3. Set up 3 departments (choose from list)
4. Set your first reminder (board gets first card)
5. Choose a scholar (advisor persona)
6. Land on your personal dashboard

**Pricing**:
- Free: core dashboard, 3 departments, cork board
- Pro ($8-15/mo): all departments, AI advisors, Buzzards dispatch, unlimited board
- Team: for studios, small companies (Life OS for your creative team)

**The pitch**: Not a productivity app. A personal OS with soul. For people who are tired of feeling empty after scrolling. For people who want their digital tools to reflect who they actually want to be.

---

## HEALTH BENEFITS 360 / MR. GREG

HB360 is the insurance brokerage Gabe runs with his brother Connor. Mr. Greg is the AI version of a benefits counselor — helps people understand their ACA options, qualify leads, answer questions.

**The play**: Everything built in Life OS (the advisor architecture, the chat interface, the memory system) directly serves Mr. Greg. When Life OS advisors are working, Mr. Greg is 80% done.

**Deployment**: Chat widget embedded on hb360website.com. Haiku model for cost efficiency at volume.

**Connor's role**: Manages payroll, occasional pay advance via Zelle. The HB360 business pays for the infrastructure that Life OS is built on.

---

## CURRENT TECH DEBT & KNOWN ISSUES

- **File size ceiling** (RESOLVED — Netlify Pro) — was limiting to ~210KB, now unlimited
- **buildTicker IIFE scope** — was getting trapped in anonymous function closures during minification. Fixed by keeping board_and_ticker.js as a standalone file, inserted before boot.
- **Cork board click** — fragile, uses `_sceneListenerAdded` flag to prevent duplicate listeners. Should eventually use proper event delegation.
- **Portal backgrounds too dark** — bumped from rgba(8,4,26) to rgba(22,14,55). Keep an eye on this after deploy.
- **No Supabase persistence** — everything resets on refresh. Top infrastructure priority.
- **Plaid OAuth** — BofA still requires OAuth registration completion in Plaid Compliance Center.
- **Scene canvas sizing** — canvas needs `cv.width = cv.offsetWidth` on resize. Can jitter on mobile.

---

## WORKING RULES FOR FUTURE CLAUDE SESSIONS

**What Gabe likes**:
- One step at a time. Confirm before big changes.
- Plain language, no walls of text, warmth.
- Be honest when something is broken — don't pretend or stall.
- Point to verifiable evidence when making claims about the code.
- Proactive handler — hold context, organize, anticipate next steps.

**Technical rules learned the hard way**:
- **IBM Plex Mono in cssText**: Must be unquoted (`font-family:IBM Plex Mono,monospace`) — quoted version inside single-quoted JS strings causes silent SyntaxError breaking all tab navigation.
- **Never wrap buildTicker (or any boot-called function) in an IIFE** — it becomes private scope and `is not defined` at boot.
- **Always run `node --check` on extracted JS** before deploying.
- **File over 210KB breaks Claude preview** (but not Netlify anymore — deploy freely).
- **Netlify drag-and-drop** bypasses build minutes but GitHub upload is cleaner for tracking.
- **Start from `/tmp/github_index.html` (the clean base)** when in doubt — it's the confirmed working version without our additions.
- **Plaid**: only `Sandbox` and `Production` in plaid-python v39+ — `Development` was removed.
- **Denmark rent**: MobilePay requires Danish residency. Use Wise (need Nikolaj's IBAN) or hand-delivery via friend Giri.

**Dashboard architecture**:
- Compact department boxes on main view → open to full laid-out modal pages
- Polished workout-week HTML (dark lime/orange accordion) is the reference model for a department's full view
- Cork board: absolute positioned cards with width 1320px inner div, overflow-x scroll on outer
- Ticker: standalone JS file, NOT wrapped in IIFE, called at boot

---

## NEXT CHAT PRIORITIES (start here)

1. **Deploy lifeos_v4.html** as `index.html` to GitHub — confirm Netlify picks it up
2. **In-app note adding** to cork board (already wired in scene modal, need to wire on main board too)
3. **Reminders import** — Gabe has exported full Reminders PDF; import all into board cards with proper truncation
4. **Supabase persistence** — wire card dismissals and additions to persist
5. **Dumbo scene** — now that La Crosse works, build the Brooklyn version
6. **Shortwave radio** — wire the streaming widget
7. **Morning Radio Brief** — ElevenLabs integration

---

## FILE LOCATIONS & REPOS

| What | Where |
|------|-------|
| Live site | `stupendous-concha-2d70be.netlify.app` |
| Frontend repo | `github.com/gable-sys/lifeos` |
| Backend repo | `github.com/gable-sys/lifeos-backend` |
| Backend live | `https://lifeos-backend-nf15.onrender.com` |
| Supabase | `https://gruebngputtvwbhroswc.supabase.co` |
| Working file | `/mnt/user-data/outputs/lifeos_v4.html` |
| Clean base | `/tmp/github_index.html` (confirmed working, no additions) |
| Project bible | `/mnt/project/LIFEOS_PROJECT_BIBLE.html` |
| Transcripts | `/mnt/transcripts/` |

---

*"This is what vibe coding should be: not just AI-assisted code generation, but AI helping humans build digital spaces that have genuine soul. The world is flooded with efficient, soulless, optimized software. Life OS is the counter-argument built in code."*

---

**End of brief · Life OS · v4 · June 2026**
