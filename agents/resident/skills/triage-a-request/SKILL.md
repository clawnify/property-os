---
name: triage-a-request
description: Turn a resident or supplier message in the Inbox into a work order in Property with a priority and a suggested vendor category, plus a drafted acknowledgement. Use when a conversation is about something broken, missing, noisy, or due.
---

# Triage a request

1. Read the conversation (`GET /api/conversations/:id/messages`). Identify
   the unit from the sender: `GET /api/tenants?search=<phone or name>` in
   Property, then the tenant's unit. If no tenant matches, tag the
   conversation `unknown-unit` and ask the person; do not create a work order.
2. Classify: category (plumber, electrician, HVAC, handyman, cleaning,
   landscaping, general) and priority (`urgent` for water, gas, electricity,
   no heating in winter, security; `high` for anything that stops a room
   being used; `normal` otherwise; `low` for cosmetic).
3. Check for an open work order on the same unit and topic
   (`GET /api/work-orders?status=open`). If one exists, add the new message
   to it as context in the chat summary instead of creating a duplicate.
4. Create the work order: `POST /api/work-orders` with property, unit,
   title (`<unit> · <what>`), description (the resident's words plus your
   classification), priority, status `open`. Suggested vendors go in the
   description, from `GET /api/vendors` filtered by category. Do not set the
   vendor field.
5. Tag the conversation (`PATCH /api/conversations/:id`) with `resident` or
   `supplier`, the unit code, and the work order id.
6. Draft the acknowledgement as an internal comment
   (`POST /api/conversations/:id/comment`, prefixed `Draft reply:`): what you
   understood, that it has been logged, and that someone will confirm the
   visit. No date.
7. Tell the person: unit, issue, priority, suggested vendor, work order id,
   and that a draft is waiting.
