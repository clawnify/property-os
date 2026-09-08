# Property OS

**AI property management software: sell the units, run the homes, keep every conversation. One install.**

Five connected apps and one sales agent for a developer, landlord or small
property manager. The agent files, drafts and stages; a person always sends
the message, signs the contract and records the payment.

An open-source bundle provided by [Clawnify.com](https://clawnify.com).

[![Deploy to Clawnify](https://app.clawnify.com/deploy-button.svg)](https://app.clawnify.com/deploy?repo=clawnify/property-os)

## Why property teams use it

A property business is one object seen from many sides: the unit. Before it
is sold it is a deal with a buyer; while it is built it is a folder of
documents and a set of renders; once delivered it is a home with a resident,
a lease, a ledger and work orders. Property management software usually
starts at the lease and a CRM stops at the sale. Property OS keeps both ends
in one workspace, with one agent working across them.

## The loop

1. **List.** Properties and units live in Property with their status. Renders
   and staged photos come out of Renders. The brochure, the floor plans and
   the contract drafts sit in a Data room with tracked links.
2. **Sell.** Buyers are contacts and deals in the CRM, one deal per unit. The
   Sales agent files every enquiry from the Inbox, writes the follow-up as an
   internal comment on the conversation, and a person sends it.
3. **Hand over.** When a unit is sold the agent proposes the unit record for
   Property: the buyer becomes the tenant or owner, the delivery date becomes
   the lease start. A person confirms; nothing is written to the ledger by
   the agent.
4. **Run.** Residents and suppliers write to the Inbox. The Resident agent
   turns a complaint into a work order with the right vendor and priority,
   and a person assigns it.
5. **Stage.** For the next listing, the Studio agent restyles, furnishes and
   declutters the unit photos and packages variants for the listing.

## What's in the box

| App | Who uses it | Key screens |
|---|---|---|
| **Property** | Owner, property manager | Properties and units, tenants, leases, rent ledger, work orders, vendors |
| **CRM** | Sales | Companies, contacts, deals pipeline per unit, activity timeline |
| **Inbox** | Everyone | One inbox for WhatsApp, email and web chat, conversations with internal comments and templates |
| **Data room** | Sales, buyers | Documents, folders, tracked links with email gates and passcodes, visit analytics |
| **Renders** | Marketing, the agent | Virtual staging and directed edits on room photos and renders, packaged per client |
| **Sales agent** | Everyone, via chat | Files enquiries, drafts replies for approval, keeps deals per unit, proposes hand-overs. Never sends |
| **Resident agent** (optional) | Property manager | Triages resident and supplier messages into work orders with vendor and priority |
| **Studio agent** (optional) | Marketing | Stages units from photos and renders, prepares listing visuals |

## One agent on every plan, more when you grow

Sales is required and is hired at install; it works on the smallest paid
plan. Resident and Studio are optional: they show up in your sidebar as "not
hired yet" and hiring them is one click once your plan has room.

## Who it's for

A developer with units to sell and then to run, a landlord with a portfolio,
a small property manager, and hospitality operators whose product is also a
room with a person in it. If your pipeline is a spreadsheet and your
residents write to your personal WhatsApp, this replaces both.

## Connect

- **WhatsApp Business** (through Clawnify) so buyer and resident messages
  land in the Inbox
- **Gmail, Google Calendar** through your Clawnify connections, for emailing
  a buyer and booking a viewing
- **OpenRouter** key for Renders (image and video edits run on your own key)

## Install

Click the button above, pick the workspace, answer four questions. Every
member deploys (or is reused if the workspace already runs it), Sales is
hired and seeded from `agents/sales`, and Resident and Studio wait in the
sidebar as optional hires.

## Members

Members are referenced by repo, never copied here. Each keeps its own button,
its own verification pin, and its own update path; installing Property OS
into an org that already runs one of them reuses it.

`apps/<slug>/` holds each member as a **git submodule** pinned to the commit
Clawnify verified, so one clone gives you the whole workspace to read and
run locally:

```bash
git clone --recurse-submodules https://github.com/clawnify/property-os.git
```

Install reads `clawnify.json`, not these folders: the platform deploys each
member at its own verified commit. The submodule pin is provenance and a
local checkout. A weekly workflow (`.github/workflows/sync-member-pins.yml`)
moves each pin to the member's current verified commit; run it from the
Actions tab to sync sooner.

Changes to a member go upstream to its repo, never into this one. If you fork
this bundle to use it as your own org workspace (where apps are vendored and
synced), replace the submodules with plain folders first.

| Member | Repo | Wired at install |
|---|---|---|
| Property | [clawnify/OpenProperty](https://github.com/clawnify/OpenProperty) | |
| CRM | [clawnify/OpenCRM](https://github.com/clawnify/OpenCRM) | |
| Inbox | [clawnify/OpenChannels](https://github.com/clawnify/OpenChannels) | |
| Data room | [clawnify/OpenDataRoom](https://github.com/clawnify/OpenDataRoom) | |
| Renders | [clawnify/OpenRenderStudio](https://github.com/clawnify/OpenRenderStudio) | |
| Sales, Resident, Studio | this repo, `agents/` | Sales required; Resident and Studio optional |

Not wired yet, and on the list: a deal-to-unit link from the CRM into
Property (the hand-over today is the agent proposing and a person entering
it), a resident portal, and a bookings member for the hospitality side.

## License

MIT, as each member.
