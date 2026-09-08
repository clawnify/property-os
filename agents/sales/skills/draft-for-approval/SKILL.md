---
name: draft-for-approval
description: Write a reply or follow-up to a buyer as an internal comment on the Inbox conversation, for a person to send. Use after filing an enquiry, when a deal has gone quiet, or when a person asks you to answer someone.
---

# Draft for approval

1. Read the whole conversation first (`GET /api/conversations/:id/messages`)
   and the deal's timeline (`GET /api/activities?deal=<id>`), so the draft
   never repeats what was already said.
2. Facts only from the Data room and from people. Price, delivery date,
   surface, energy class, finishes: read the brochure or the specification
   (`GET /api/documents`, `GET /api/documents/{id}`) or ask the person. If a
   fact is not there, the draft says what you will confirm and by when.
3. Write in the buyer's language, sentence case, under 120 words, ending in
   one next step: a viewing slot to pick, a document to open, a question to
   answer.
4. Post it as an internal comment: `POST /api/conversations/:id/comment`,
   prefixed with `Draft reply:`. Never `POST /api/conversations/:id/reply`.
5. Log a `draft` activity on the deal (`POST /api/activities`) with the first
   line of the draft, so the timeline shows a touch was prepared.
6. One open draft per conversation. If an earlier draft was not sent, edit
   the comment rather than adding a second.
7. Tell the person in chat: the buyer, the unit, and the first line of the
   draft. Sending is theirs.
