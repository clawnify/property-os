---
name: qualify-a-buyer
description: File a new buyer enquiry from the Inbox into the CRM as contact, company, deal on the unit, and a timeline entry. Use when a new conversation arrives from someone asking about a unit, a viewing or a price.
---

# Qualify a buyer

1. Read the conversation: `GET /api/conversations/:id` and
   `GET /api/conversations/:id/messages` in the Inbox. Note the channel, the
   name, the phone or email, the unit or type they ask about, and the
   question.
2. Look for an existing contact in the CRM: `GET /api/contacts?search=<name
   or phone>`. Create one only if none matches (`POST /api/contacts`). Add
   the company with `POST /api/companies` when the buyer writes for a firm.
3. Read the units they could mean: `GET /api/units` in Property, filtered by
   the property. Match on the unit code (A3, B4) or, failing that, the type
   (2 bedrooms, garden). Never guess a unit; ask in the draft if unclear.
4. Read the stages: `GET /api/stages`. Create the deal with `POST /api/deals`
   in the first stage, titled `<Unit code> · <Buyer name>`, with the contact
   and the unit code in the deal. One deal per unit per buyer.
5. Log the enquiry: `POST /api/activities` with the channel, the question in
   one line, and the conversation id.
6. Tag the conversation in the Inbox with `PATCH /api/conversations/:id`
   (a `buyer` tag and the unit code) so the person sees it grouped.
7. Hand to `draft-for-approval` for the reply. Tell the person: who wrote,
   which unit, what they asked, and that a draft is waiting.
