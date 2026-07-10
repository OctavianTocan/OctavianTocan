# Octavian Tocan

**AI Agent Architect / Full-Stack Engineer.** I build agent infrastructure that holds up on cheap computers and survives unattended runs.

**A decade shipping production software** · Zaragoza, Spain

Most of the AI infrastructure code I've read this year is wrapper code, and most of it falls over the moment it has to run on its own. I keep trying to show that the fix is a smaller, sharper system around the model.

## What I run

Two agents on OpenClaw (one for me, a separate one for my girlfriend), with Telegram as the interface to them. I keep a local fallback gateway on the same computer, running [Hermes by Nous Research](https://github.com/NousResearch/hermes-agent), which occasionally steps in to debug and fix Wretch when Wretch goes down.

Underneath: 21 cron jobs and a multi-layer memory system glued together by my own routing, with a dream-loop cron that promotes session facts into durable storage with conflict checks. The two memory plugins doing the heavy lifting are open-source projects I layered in, not things I wrote: [Hindsight](https://github.com/vectorize-io/hindsight) for cross-session observations and [LCM](https://github.com/Martian-Engineering/lossless-claw) for context compression that never truncates. Everything around them is mine, including Tribunal, a multi-model critic pipeline where Claude, Codex, and Gemini review independently and a judge synthesizes the verdict.

Three plugins I authored sit on top: [openclaw-notion](https://github.com/OctavianTocan/openclaw-notion) (18 tools, 56 tests), [openclaw-todoist](https://github.com/OctavianTocan/openclaw-todoist) (12 tools, per-agent scoped auth), and [openclaw-menu-handler](https://github.com/OctavianTocan/openclaw-menu-handler) (Telegram keyboards that bypass the LLM entirely, so /menu has zero latency).

Agent behavior is governed by [claude-rules](https://github.com/OctavianTocan/claude-rules), 227 policies across 22 categories, grown one near-miss at a time.

## What I'm building

- [**Pawrrtal**](https://github.com/OctavianTocan/pawrrtal-ai): my full-stack AI workspace and provider-agnostic agent loop. Web and Telegram as first-class channels, filesystem-backed workspaces, multi-provider model routing (Claude, Gemini, Codex, xAI), streaming tool use, encrypted per-workspace credentials, and iteration caps plus wall-clock budgets so a loop can't run away. ~728 commits and 217 PRs so far. I built it because I was tired of debugging LangChain wrappers at 2am and wanted code I'd written myself.

- [**TwinMind**](https://twinmind.com/) *(Lead Web Engineer)*: an AI meeting assistant for iOS, web, and Chrome. I built their entire React Native app from scratch as the only engineer on it, a brownfield Expo integration that ports core TwinMind views into the existing native iOS and Android apps as a shared module, shipped end-to-end with 591 tests. On the web side, I led full-stack, with memory page loads ending up 43x faster and a 12,000-line side panel cut to 600.

## A few of my public repos

- [**cloakbrowser-skill**](https://github.com/OctavianTocan/cloakbrowser-skill): Claude skill wrapping stealth Chromium, so agents can fetch, screenshot, and run JS on sites that block headless browsers. My most-installed tool: `npx skills add OctavianTocan/cloakbrowser-skill`.
- [**raft**](https://github.com/OctavianTocan/raft): terminal UI for GitHub PRs and stacked diffs, built on OpenTUI.
- [**ralph-ai-coding-loop**](https://github.com/OctavianTocan/ralph-ai-coding-loop): autonomous coding loop with disk-persisted state, multi-backend support, and 3-iteration stuck detection.
- [**agent-retro-loop**](https://github.com/OctavianTocan/agent-retro-loop): turns an agent's session logs into rules, with conflict checks before anything gets written.
- [**blueprint-documentation-generator-plugin-for-ue5**](https://github.com/OctavianTocan/blueprint-documentation-generator-plugin-for-ue5): C++ UE5 editor plugin that turns Blueprint node graphs into markdown via a local Ollama model.

## Two things I keep proving in code

**Linting is infrastructure.** Small custom CI gates (file length, nesting depth, no tools defined inside providers) catch more real regressions for me than any LLM review suite I've used. Each is under 200 lines, and together they're how a codebase stays legible at speed.

**Thin harness, fat skills.** The agent doesn't need to be smart, it needs to call the right small tool with a real schema. I keep collapsing 400-line agent prompts into 30 lines plus five well-named tools, and behavior gets better on cheaper models.

## About

Self-taught. My first shipped code made $35,000 in its first month when I was 16: the event system, NPC AI, and building system for a Unity survival template.

At 20, I co-founded [Infima Games](https://infimagames.com). Our Low Poly Shooter Pack sits at 4.8★ across 459 reviews, with a free tier used by tens of thousands of developers. Most recently, I was Lead Web Engineer at TwinMind, a Sequoia-backed AI memory startup.

Zaragoza, Spain. EU citizen. English, Spanish, Romanian.

## Reach me

[contact@octaviantocan.com](mailto:contact@octaviantocan.com) if you're working on agent platforms, developer tools, or observability for non-deterministic systems, anything where the real question is how to make it reliable.

Zaragoza, late hours.
