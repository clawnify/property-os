---
name: hand-over-a-unit
description: When a person confirms a unit is sold or let, prepare the Property records (tenant, lease, unit status) and show them for confirmation. Use only after a person says the deal is done; never on a stage change you inferred.
---

# Hand over a unit

1. Confirm the trigger came from a person, in words, naming the unit and the
   buyer. A deal moving in the CRM is not a trigger.
2. Read the deal (`GET /api/deals`) and the contact (`GET /api/contacts/:id`)
   in the CRM, and the unit (`GET /api/units/:id`) in Property.
3. Prepare, and show as a table, the records Property will need:
   - tenant: name, email, phone (from the contact);
   - lease: unit, start date (the delivery date the person gave), rent or
     price as the person states it, deposit if any, status;
   - unit status: `occupied` from the delivery date.
4. Ask for one confirmation. Then, and only then, create the tenant
   (`POST /api/tenants`) and the lease (`POST /api/leases`), and set the
   unit status with `PUT /api/units/:id`. Never a payment: the ledger is the
   person's (`POST /api/payments` is not yours).
5. Log the hand-over on the deal timeline (`POST /api/activities`) and tell
   the person what was created, with the ids.
6. If anything in the table was wrong, stop and ask; do not create a partial
   set.
