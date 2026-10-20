# CFH PT

Block deadlines for CFH personal training clients: https://cfh-rotterdam.github.io/cfh-pt/

Built the same way as [CFH Events](https://github.com/cfh-rotterdam/cfh-events): one `index.html`, no build step, served by GitHub Pages. No sign-in.

- Read-only. Shows first names, location and block dates: who has run out, who is ending in the next 14 days, who has no block, and a timeline.
- Data comes from the Supabase function `public_schedule()` (project `cfh-pt`). It returns only first names, site and block dates. Notes, goals, maxes, health information and documents are not exposed: the tables stay behind Row Level Security.
- Full client records are edited with Claude in chat, not on this page.
