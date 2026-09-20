# Marketing Hook Writer

Writes the creative bank — hooks, body skeletons, proof modules and calls to action — as separable units built on verbatim customer language, so one shoot recombines into many variants and a test can move one variable at a time.

A hook is the first three seconds and it has exactly one job: earn the next ten. It is not the claim restated and it is not a headline. Each is written as three parts kept apart — what is said, what is on screen in a handful of words, and what is happening — because the on-screen line is what carries the ad in a muted feed, which is most of it.

The raw material is the customer's own phrasing, quoted exactly. A tidied quote has had the thing that made it work removed. Where a second language is in play it says plainly whether the quotes survive translation, and recommends writing that market from its own quotes instead.

Every hook carries a compliance check against the landing page's claims and the campaign's banned list, so a line that cannot ship is caught at writing time rather than at review. It writes language and structure only — no shot lists, no camera directions, no timing.

## What this is, precisely

A FindAgent **`mcp-tool`** agent. Each of its 6 tools is a
`prompt-template` action: the tool renders an instruction and hands it back to the
model that called it.

Two consequences worth being blunt about, because they decide whether this is useful to you:

- **It calls no model and reaches no network.** A tool call costs nothing and returns
  the same text for the same input, every time. There is no API key, no credential
  slot and no egress.
- **It observes nothing.** It has no access to your repository, your logs, your
  analytics or your devices. Every template is written so that supplying nothing
  produces an honest statement of what is missing rather than a confident-looking
  answer about data nobody provided. If you ask for a report and give it no findings,
  it will tell you the work has not been done — not invent it.

## Tools

| Tool | What it returns | Required input |
|---|---|---|
| `build_verbatim_pool` | Pull the exact customer phrases that will be the raw material for every hook, kept word for word with their sources, and judge whether they survive the campaign's creative language. | `customer_voice` |
| `write_hooks` | Write the hooks for one angle as three separable parts — spoken, on-screen, and what is happening — covering distinct archetypes rather than rephrasing one idea. | `angle`, `verbatim_pool` |
| `write_body_and_proof` | Write the body skeletons, proof modules and calls to action for an angle as separable units, each proof module naming the asset it needs and whether it exists. | `angle` |
| `check_hook_compliance` | Check written hooks against the claims boundary, the banned list and the angle's do-not-say, flagging each line that cannot ship and why. | `hooks`, `claims_boundary` |
| `plan_recombination_matrix` | Lay out how the modules combine into testable variants, so each cell differs from its neighbour by exactly one variable and the result can be attributed. | `modules` |
| `draft_creative_bank` | Assemble the creative bank for the script stage — hooks, bodies, proofs, CTAs, the matrix and the rejected lines — refusing to produce one when no modules were written. | `campaign_context` |

Optional inputs render as empty when omitted. Every template names that case and says
what it could not determine, so an empty slot degrades into a stated gap rather than a
dangling clause.

## Part of a department

This agent is one member of the **marketing video ad** department, a
hub-orchestrator team of 7. The hub is `marketing-campaign-scoper`, which locks the brief every later
stage reads; the other members are
reached through it or called directly as `<alias>__<tool>`.

| Agent | Stage in the pipeline |
|---|---|
| `marketing-campaign-scoper` | 1 — interviews for the brief and freezes it (department hub) |
| `marketing-ad-researcher` | 2 — competitor harvest plan, longevity ranking, customer voice, coverage |
| `marketing-angle-strategist` | 3 — scored angle map with auditable arithmetic |
| `marketing-hook-writer` | 4 — the modular creative bank, built on verbatim customer language |
| `marketing-ad-scripter` | 5 — modules, continuity kits, prompts, assembly map, QA protocol |
| `marketing-production-planner` | 6 — blockers, tracks, cost estimate, shoot briefs, release gates |
| `marketing-ad-tester` | 7 — clip QA, test design, readout, and the feedback loop back to 3, 4 and 5 |

Each member is published independently and works on its own.

## Provenance

`source/hooksmith.md` is the markdown skill this agent was converted from. The tool templates carry its
instructions, parameterised: anything the original hard-coded to one team's repositories,
file paths or people became an input you supply, and where a template would otherwise
depend on reading something it cannot reach, it asks for that material as an argument
instead.

## Licence and use

Published by Kata Team on FindAgent. Free to connect.
