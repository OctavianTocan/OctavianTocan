# Octavian Tocan

I build agent infrastructure that holds up under real traffic.

Most "AI engineering" work in 2026 is glue, and most glue is bad. I keep
trying to prove that the way out isn't a smarter model — it's a smaller,
sharper system around it.

## What I'm building

- **[OpenClaw](https://github.com/OctavianTocan?tab=repositories&q=openclaw)** —
  self-hosted gateway that turns messaging platforms (Telegram, WhatsApp)
  into the front door for AI coding agents. The agents run on their own
  filesystem, behind their own permission boundaries, with a memory layer
  that survives a process restart. Currently runs Wretch (the builder) and
  Dr. Hermes (the diagnostician) on a $20 Hetzner box. Hermes autonomously
  reads Wretch's logs and proposes structural fixes — I didn't plan that;
  it emerged from the shared filesystem protocol.

- **Pawrrtal** *(public soon)* — provider-agnostic agent loop with native
  Claude Agent SDK and Gemini providers, in-process MCP tool bridges,
  per-agent permission gating, and a chat router that owns tool composition
  (so providers stay tool-agnostic; enforced by a CI gate). Replaces the
  "wrap LangChain and pray" path with code I can actually debug at 2am.

- **[TwinMind](https://twinmind.com)** *(day job, ThirdEar)* — AI meeting
  assistant for iOS and web. I ship across the stack: brownfield React
  Native, Auth0 + Firebase auth flows, transcript pipelines, and the CI
  infrastructure that runs the whole thing on a single Mac Mini without
  falling over.

## Two opinions I keep proving in code

**Linting is infrastructure.** Five small custom CI gates — file-length,
nesting depth, no-tools-in-providers, dev-mode-console-clean,
identity-files-size-doctor — catch more real regressions than any LLM
review suite I've used. Each is under 200 lines. None of them know
about each other. They're how a codebase stays legible at speed.

**Thin harness, fat skills.** The agent doesn't need to be smart. It
needs to call the right small focused tool with a real schema. I keep
collapsing 400-line agent prompts into 30 lines plus five well-named
tools and getting better behavior on cheaper models.

## Where I write

- **[LinkedIn](https://www.linkedin.com/in/octaviantocan/)** — semi-public,
  builder side. Hypothesis-driven, with a 48-hour feedback loop on every
  post.
- **Here, in code** — less filtered, more honest.

## Reach me

[contact@octaviantocan.com](mailto:contact@octaviantocan.com) if you're
working on agent platforms, developer tools, observability for
non-deterministic systems, or anything where the real question is
"how do you make this reliable, not just impressive in a demo."

Madrid · Europe/Madrid · late hours.
