# Higgsfield Router Lite

A free Claude skill that tells Claude which Higgsfield tool and model to use for a job, and what to try first when a generation fails. Unofficial, not affiliated with Higgsfield. Snapshot October 2026.

## What it does

You describe a job, for example a product that should spin while the camera stays still, or a still image you want to animate. Claude picks the tool and model, lists the settings that matter, fills a prompt skeleton for your job, and gives the cheapest fix first for when it breaks. If you describe a failure instead (a frozen clip, a drifting character, a 422 error), it matches the symptom to a known fix.

It has five routes (product spin, animating a still, start and end frames, transitions, motion transfer), ten failure entries and a model picker for constraints like start/end frame or video reference.

Every claim carries a label: tested (run and dated), vendor, community or untested. Model ids and prices change monthly, so the skill tells Claude to check an id with `models_explore` before naming it, and the prices in it are dated examples from September and October 2026. It only gives advice. It does not generate anything or spend credits unless you ask.

## Install

Copy this folder to `~/.claude/skills/higgsfield-router-lite/` and restart Claude Code.

## Free to use

Free to use and share. Please keep the credit to ICEGO.

## Longer version

ICEGO also sells a longer paid manual that covers the whole platform: https://whop.com/icegostudio/higgsfield-router
The free skill is also on Whop: https://whop.com/icegostudio/higgsfield-router-lite
