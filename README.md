# Octavian Tocan

I build agent infrastructure that holds up on cheap boxes and survives the kind of unattended runs that break most setups.

Most of the AI infrastructure code I've read this year is wrapper code, and most of it falls over the moment it has to run on its own. I keep trying to show that the fix is a smaller, sharper system around the model.

## What I run

The personal stack that taught me where this breaks. Two agents (Wretch for me, a separate one for my girlfriend) on OpenClaw, with Telegram as the front door. A local Python fallback called Hermes lives on the same machine and has stepped in to debug Wretch when Wretch went down.

Underneath the agents: 21 cron jobs (nightly memory consolidation at 4am, infra health checks every 6h, PR monitor every 15m), two long-term memory systems I wrote from scratch (Hindsight for cross-session observations and entity graphs, LCM for DAG-summarised conversation history that never has to truncate), and Tribunal, a multi-model critic pipeline where Claude, Codex, and Gemini act as independent reviewers and a Codex judge synthesises the verdict.

Three OpenClaw plugins I authored sit on top: [openclaw-notion](https://github.com/OctavianTocan/openclaw-notion) (18 Notion tools, bidirectional sync, multi-agent workspace isolation, 56 tests), [openclaw-todoist](https://github.com/OctavianTocan/openclaw-todoist) (12 tools with per-agent scoped auth), and [openclaw-menu-handler](https://github.com/OctavianTocan/openclaw-menu-handler) (a Telegram keyboard plugin that bypasses the LLM entirely so /menu has zero latency).

Agent behaviour is governed by [claude-rules](https://github.com/OctavianTocan/claude-rules), a domain-organised ruleset I've been growing one near-miss at a time. It's at 220+ policies now.

## What I'm building

- **Pawrrtal** *(public soon)*: a provider-agnostic agent loop with native Claude Agent SDK and Gemini support, in-process MCP tool bridges, per-agent permission gating, and a chat router that owns tool composition so providers stay tool-agnostic (a CI gate enforces it). I built it because I was tired of debugging LangChain wrappers at 2am and wanted code I'd written myself.

- **[TwinMind](https://twinmind.com/)** *(ThirdEar, Lead Web Engineer)*: an AI meeting assistant for iOS, web, and Chrome. I led web full-stack and was the sole engineer on the React Native brownfield repo, shipping the auth flows, the transcript pipeline, the Daily Digest, the Todo page, and the My Mind dashboard end-to-end. Cut the React Native CI from 45 minutes to 8 with one Gradle-cache change. Memory page load improved 43x after refactoring around 25% of the codebase.

## A few of my public repos

- **[ai-nexus](https://github.com/OctavianTocan/ai-nexus)**: full-stack AI workspace with streaming chat, JWT auth, and Fernet-encrypted key storage. Active.
- **[ralph-ai-coding-loop](https://github.com/OctavianTocan/ralph-ai-coding-loop)**: my implementation of the Ralph Loop. Disk-persisted state, multi-backend (Claude, Codex, Gemini, aider), 3-iteration stuck detection.
- **[hermes-skills](https://github.com/OctavianTocan/hermes-skills)**: open-sourced skill library for Hermes-style runtimes.
- **[wt-cli-rust](https://github.com/OctavianTocan/wt-cli-rust)**: ground-up Rust rewrite of my own wt-cli, structured as a 12-step learning vehicle.
- **[agent-retro-loop](https://github.com/OctavianTocan/agent-retro-loop)**: a small skill that turns an agent's session logs into rules, with conflict checks before anything gets written.
- **[blueprint-documentation-generator-plugin-for-ue5](https://github.com/OctavianTocan/blueprint-documentation-generator-plugin-for-ue5)**: C++ UE5 editor plugin that turns Blueprint node graphs into markdown via a local Ollama model. 8 stars.
- More at [github.com/OctavianTocan](https://github.com/OctavianTocan).

## Two things I keep proving in code

**Linting is infrastructure.** Five small custom CI gates (file length, nesting depth, no tools defined inside providers, no console logs left in dev mode, an identity-file size doctor) catch more real regressions for me than any LLM review suite I've used. Each one is under 200 lines, fully independent of the others, and together they're how a codebase stays legible at speed.

**Thin harness, fat skills.** The agent doesn't need to be smart, it needs to call the right small focused tool with a real schema. I keep collapsing 400-line agent prompts into 30 lines plus five well-named tools, and behavior gets better on cheaper models.

## Where I write

- **[LinkedIn](https://www.linkedin.com/in/octaviantocan/)**: the semi-public, builder side. Hypothesis-driven, with a 48-hour feedback loop on every post.
- **Here, in code**: less filtered, more honest.

## Reach me

[contact@octaviantocan.com](mailto:contact@octaviantocan.com) if you're working on agent platforms, developer tools, observability for non-deterministic systems, or anything where the real question is how to make it reliable, not just impressive in a demo.

Zaragoza, late hours.
