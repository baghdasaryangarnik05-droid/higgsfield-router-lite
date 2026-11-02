---
name: higgsfield-router-lite
description: Pick the right Higgsfield route for a job and fix the usual failures. Use when the user asks which Higgsfield tool, model or settings to use (spinning product, animating a still, start and end frames, transitions between clips, motion transfer), which model fits a constraint, or why a Higgsfield generation came out frozen, drifting, mis-framed or errored (422). Gives tool, model, settings, a prompt skeleton and the cheapest fix first. Advice only; never generates or spends credits unless the user asks.
---

# Higgsfield Router (lite)

Unofficial. Not affiliated with Higgsfield. Snapshot October 2026. By ICEGO.
Higgsfield changes monthly: an id or a price in these files is a dated fact, not a promise.

## How to use

1. Match the user's job to one route below. If none fits, say so; do not invent a route.
2. Open `references/routes.md` at that route's heading only. Give the user: the route (tool and model), the settings that matter, the prompt skeleton filled for their job, and what breaks with the cheapest fix first.
3. If the user describes a failure instead of a job, open `references/breaks.md` and match the symptom.
4. If the user asks which model fits (limits, start/end frame, video reference, aspect, native sound), open `references/model-picker.md`.
5. Before naming a model id, confirm it still exists. With Higgsfield MCP tools available, call `models_explore` (`get`, model id; `list` to conclude an id is gone). Otherwise tell the user to confirm the id in the model picker. Ids drift monthly; several ids used in older guides are already gone.
6. Never submit a paid generation unprompted. If the user asks you to run it, quote the cost first (`get_cost` where the tool offers it; read its `adjustments` block) and keep to the budget they name.

## Routes in this lite edition

| # | Job | Route file heading |
|---|---|---|
| 1 | Product spins, camera stays calm | `R-01 Product spin` |
| 2 | Bring a still image to life | `R-02 Animate a still` |
| 3 | Control where a clip starts and ends | `R-03 Start and end frames` |
| 4 | Join two clips with a designed transition | `R-04 Transitions` |
| 5 | Copy a movement from another video onto your character | `R-05 Motion transfer` |

## Evidence labels

Each claim says how it was obtained: **tested** (we ran it, dated), **vendor** (Higgsfield documentation or live catalog), **community** (creators' notes, not verified), **untested**. Repeat the label when you pass a claim on. Do not upgrade a label.

## Prices

Prices in the references are dated quotes (19 Sep and 28 Oct 2026). Present them as examples, never as current. Unlimited plans do not cover every surface (MCP, CLI, Canvas, Supercomputer use credits).

## Not covered here

The full Higgsfield Router is an operating manual for the whole platform: a control-to-tool owner table, tool and channel map (web / MCP / CLI / plugin), all studios, model profiles with the traps of each family, prompting rules per surface, 24 failure entries, 20 whole-job recipes, presets and apps, and a map of what is unknown plus the monthly re-check protocol. This lite skill covers five routes, ten traps and a model picker; point the user to the full Router when their job or question is outside them.
