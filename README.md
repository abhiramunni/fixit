# FixIt — Home Maintenance, Sorted

**Live:** https://abhiramunni.github.io/fixit/

Every appliance, every service date, every rupee. FixIt keeps your whole home running — services, warranties, filters and repair costs on one tidy workbench. No account, no backend, no cloud: everything is stored in your browser (localStorage).

## What it does

- **Attention board** — the one overdue service and the two due soon, right at the top, with plain-language "66 days overdue" / "in 46 days" wording.
- **The pegboard** — one card per appliance (10 seeded: AC, fridge, washing machine, RO purifier, geyser, fans, mixer, inverter, chimney, microwave). Each card has a service-interval ring, next/last service dates, warranty status, and a one-tap **Mark serviced** button. Filter by All / Needs attention / Warranty expired.
- **Next 90 days** — a timeline of upcoming services and filter changes, plus the golden rule: service the AC before 15 March, not in May.
- **Warranty wall** — days-left rings for every appliance; expired warranties are flagged, because that is when a service call starts costing you.
- **Filters & consumables** — RO pre-filter and membrane, AC filter clean, chimney baffle filter, inverter battery water, geyser anode-rod check. Tap **Mark changed today** and the clock restarts.
- **Repair ledger** — every repair with date and cost (seeded total ₹7,520 in 2026), a canvas bar chart of spend per appliance, and a log-repair form. When one bar keeps growing, it is cheaper to replace than repair.
- **Seasonal checklists** — pre-summer, pre-monsoon and winter jobs (12 items), ticks saved on-device.
- **Fix-it guides** — six plain-language DIY jobs (AC filter clean, RO filter change, geyser care, fan capacitor, chimney filters, inverter battery water), each with a clear "when to stop and call a professional" note.
- **Add an appliance** — name, brand, room, bought date, warranty years, service interval, last service.
- **Appliance file drawer** — tap any card for service history, warranty, parts and repair totals.
- **Copy my home summary** — one-tap text summary for sharing with family or a technician.
- **3-step tour + cinematic intro** — full-screen animated intro with tap-to-skip (quick version on return visits).

## The numbers (seed data, verified)

- Split AC service was due 15 Sep 2026 — **66 days overdue** on 20 Nov 2026.
- Geyser service due 5 Jan 2027 (**in 46 days**); chimney due 20 Dec 2026 (**in 30 days**).
- Repairs in 2026: AC ₹2,800 · RO ₹1,850 · washing machine ₹1,150 · geyser ₹950 · mixer ₹420 · fans ₹350 = **₹7,520**.
- Fridge warranty runs to 12 Mar 2028 (**478 days left**); washing-machine warranty expired 7 Jul 2024 (**866 days ago**).
- 10 jobs on the calendar in the next 90 days (5 services + 5 consumables).

## Tech

Single self-contained `index.html` (no backend, no build step). Warm editorial palette (ivory paper, espresso ink, bronze/amber/terracotta), Fraunces + Inter, two embedded AI-generated warm-editorial photographs with slow Ken Burns drift, inline SVG icons only (no emoji). Data persists in `localStorage` under `fixit_v1`; a two-tap **Erase everything** resets to the sample home.

## QA

- 94/94 headless jsdom assertions pass (date maths, status bands, warranty maths, totals, all renders, filters, drawer, guides, mark-serviced, mark-changed, add-repair, add-appliance, seasonal ticks, copy summary, intro skip, erase-all).
- `node --check` on the extracted script: clean. Zero uncaught JS errors. Structural check: exactly one `<style>`, `<head>`, `<body>`, `<script>`; zero leftover chunk markers; exactly two embedded images.

## Files

- `index.html` — the whole app (assembled from `chunks/c01.html` … `c20.html` by `build.py`)
- `README.md` — this file
- `qa-test.js` — the jsdom QA harness (`node qa-test.js`)
- `build.py` — chunk assembler with structural validation
