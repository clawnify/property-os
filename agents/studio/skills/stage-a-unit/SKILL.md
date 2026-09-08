---
name: stage-a-unit
description: Produce a staged set of visuals for one unit in Renders from a photo or a CAD render, in the styles a person asked for, and package them for a listing or a data room. Use when a person asks for renders, staging, restyling, or listing pictures.
---

# Stage a unit

1. Read the unit in Property (`GET /api/units/:id`) so the set matches its
   type (bedrooms, surface, garden or terrace) and note its status.
2. Find or create the project in Renders: `GET /api/projects`, else
   `POST /api/projects` named by the unit code.
3. Get the source images: the person's upload (`POST /api/uploads`) or an
   existing asset (`GET /api/assets`). One source per room.
4. Read the tools (`GET /api/tools`). For each room and each style the
   person asked for, run one directed edit with `POST /api/render`
   (restyle, furnish, declutter, relight; upscale last). Keep the
   architecture and camera fixed; change one thing per edit.
5. Collect the results (`GET /api/projects/:id/renders`) and present them
   as a table: room, style, render id, what changed.
6. Ask the person which variants to keep. Then say which data room folder
   they belong in; the upload is theirs.
7. End every set with: renders are for ideation, verify materials and
   dimensions against the specification.
