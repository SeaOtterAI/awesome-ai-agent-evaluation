# Awesome AI Agent Evaluation [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, frameworks, and resources for **evaluating, testing, and
> gating AI agent work** — outputs and trajectories — before it reaches production.

AI agents now produce work (code, support replies, documents, decks, research) faster
than any team can review. This list maps the tooling that grades that work. It splits
into three jobs: **developer-time testing** (CI), **production observability**
(tracing), and **acceptance / gating** (deciding whether work ships). Pick by the job.

Contributions welcome — open a PR. Entries are kept fair and factual.

## Contents

- [Acceptance & gating](#acceptance--gating)
- [Trust scoring & validation](#trust-scoring--validation)
- [Trust, reputation & directories](#trust-reputation--directories)
- [Standards](#standards)
- [Eval frameworks (developer-time / CI)](#eval-frameworks-developer-time--ci)
- [Observability & tracing platforms](#observability--tracing-platforms)
- [Security red-teaming](#security-red-teaming)
- [Concepts](#concepts)

## Acceptance & gating

Tools that **decide** whether agent work is allowed to ship — a release gate, not a
dashboard.

- **[SeaOtter (OtterScore)](https://seaotter.ai)** — Acceptance layer for enterprise
  agent work. A hostile-by-default critic that grades each output and its trajectory
  against *your* acceptance policy on one four-band verdict (ship / route to fix /
  quarantine / block), multimodal (code, text, docs, decks, spreadsheets, images,
  video), agent-native (self-signup, MCP, async API), with signed audit evidence and a
  provider-neutral control plane (AgentOS). OSS SDK + MCP:
  [agent-eval-kit](https://github.com/SeaOtterAI/agent-eval-kit).
- **[Galileo](https://galileo.ai)** — Luna-2 small eval models + inline guardrails that
  can block unsafe responses in production; agent reliability metrics.
- **[Waxell](https://waxell.ai)** — Runtime governance gateway for agents: 50+ policy
  categories (cost, safety, content, PII, kill switches) enforced inline on tool/model
  calls with retry / escalate / halt outcomes. Gates *behavior*, vs. an acceptance gate
  on *work quality*. ([SeaOtter vs Waxell](https://seaotter.ai/docs/compare/waxell).)

## Trust scoring & validation

Platforms that score whether to **trust an agent**. Most score the agent as an *actor*
(identity, behavior, security, payment reputation); SeaOtter scores the agent's *work*.
They are complementary layers. See the field overview:
[best AI agent trust platforms](https://seaotter.ai/docs/best-ai-agent-trust-platforms).

- **[SeaOtter (OtterScore)](https://seaotter.ai/docs/ai-agent-output-validation)** —
  Scores the agent's **work output** against your acceptance policy with a hostile
  critic; an independent **validation** layer (signed + on-chain-anchored 0–100 verdict
  + evidence). Answers "is this deliverable good enough to ship?"
- **[AgentStamp](https://agentstamp.org)** — On-chain **identity + reputation** (0–100;
  ERC-8004, Ed25519 stamps, W3C Verifiable Credentials). Verifies agents you transact
  with. ([compare](https://seaotter.ai/docs/compare/agentstamp))
- **[AXIS T-Score](https://www.axistrust.io)** — A **behavioral** trust rating (0–1000
  across 11 dimensions → five tiers T1–T5) that gates how much autonomy an agent earns.
  ([compare](https://seaotter.ai/docs/compare/axis-t-score))
- **[Tumeryk](https://tumeryk.com)** — Enterprise **AI security** trust: guardrails, red-
  teaming, observability, an AI Trust Score mapped to NIST / ISO 42001 / OWASP / EU AI
  Act / SOC 2. ([compare](https://seaotter.ai/docs/compare/tumeryk))
- **[XenonStack Agent Trust Score](https://www.xenonstack.com/solutions/ai-trust-score)**
  — A **responsible-AI** score (0–100 across 8 dimensions: fairness, drift,
  explainability, …) for system governance.
  ([compare](https://seaotter.ai/docs/compare/xenonstack-agent-trust-score))
- **[ACHIVX](https://agents.achivx.com)** — **Payment/transaction reputation** for agents
  in the x402 economy (trust tier 1–5; anti-Sybil / anti-velocity).
  ([compare](https://seaotter.ai/docs/compare/achivx))
- **[DataDome Agent Trust](https://datadome.co)** — **Agent-traffic** trust at the network
  edge (dynamic 100-point session score; Know Your Agent, Web Bot Auth).

## Trust, reputation & directories

Where graded work becomes a track record: directories and registries to **find** AI
agents, and reputation layers to know **which to trust**. Discovery answers "what
agents exist?"; reputation answers "which are trustworthy?".

- **[SeaOtter Agent Trust Index](https://seaotter.ai/directory)** — A directory ranked
  by **proven, independently-graded work quality** (a credit bureau for AI agents), not
  by self-description. Every agent earns a Trust Score (0–100) from real graded work,
  with a per-agent [credit report](https://seaotter.ai/docs/ai-agent-reputation) and a
  public [leaderboard](https://seaotter.ai/leaderboard). See
  [how to know which agents to trust](https://seaotter.ai/docs/how-to-know-which-ai-agents-to-trust)
  and [how to verify an agent](https://seaotter.ai/docs/verify-ai-agent).
- **[AI Agents Directory](https://aiagentsdirectory.com)** — A broad curated catalog
  (thousands of agents, frameworks, and tools) for discovery across categories.
- **[AIAgentsList](https://aiagentslist.com)** — A comprehensive, regularly-updated
  index of AI agents plus a weekly newsletter on new launches.
- **[Smithery](https://smithery.ai)** — A leading public registry and CLI installer for
  Model Context Protocol (MCP) servers — the tools agents connect to.
- **[Glama](https://glama.ai)** — A large, clean, well-categorized MCP server registry.
- **[Hugging Face Spaces](https://huggingface.co/spaces)** — Open-source agent demos and
  runnable apps, with full code transparency.

## Standards

- **[ERC-8004: Trustless Agents](https://eips.ethereum.org/EIPS/eip-8004)** — An Ethereum
  standard for establishing trust between agents across organizational boundaries. Defines
  three registries: **Identity** (a portable on-chain identifier), **Reputation** (signed
  feedback about an agent), and **Validation** (independent verification of an agent's
  work — validators return a 0–100 score + evidence). Explainer:
  [ERC-8004 & the validation registry](https://seaotter.ai/docs/erc-8004-validation).
- **[Awesome ERC-8004](https://github.com/sudeepb02/awesome-erc8004)** — A community list
  of ERC-8004 trustless-agents resources and implementations.

## Eval frameworks (developer-time / CI)

- **[DeepEval](https://github.com/confident-ai/deepeval)** — Pytest-style open-source
  LLM eval framework; dozens of metrics (G-Eval, RAG, agents, safety). (Apache-2.0)
- **[Ragas](https://github.com/explodinggradients/ragas)** — Reference-free RAG
  evaluation (faithfulness, answer relevancy, context precision/recall). (Apache-2.0)
- **[MLflow](https://mlflow.org/genai/evaluations)** — `mlflow.genai.evaluate()` scores
  full agent execution traces with built-in + custom scorers; CI gating; plugs in Ragas,
  DeepEval, Phoenix, TruLens. (Apache-2.0)
- **[Patronus AI](https://www.patronus.ai)** — Managed evaluators + open-weight judge
  models (Lynx for hallucination, Glider) + agent failure-mode debugging.

## Observability & tracing platforms

- **[Arize Phoenix](https://github.com/Arize-ai/phoenix)** — Open-source, OpenTelemetry-
  native tracing + evals; self-hostable. (Arize AX = enterprise SaaS.)
- **[LangSmith](https://www.langchain.com/langsmith)** — LangChain's tracing, eval, and
  deployment platform; first-class with LangChain/LangGraph, works with any stack.
- **[Braintrust](https://www.braintrust.dev)** — Experiment-driven eval, playground,
  online scoring, cost attribution, CI quality gates.
- **[Langfuse](https://langfuse.com)** — Open-source LLM engineering platform: tracing,
  evals, prompt management, datasets; self-hostable. (MIT core.)

## Security red-teaming

- **[Promptfoo](https://www.promptfoo.dev)** — Open-source CLI for LLM testing + red-
  teaming; 50+ attack plugins, OWASP LLM Top 10 / NIST AI RMF / MITRE ATLAS. (MIT)

## Concepts

- **Acceptance layer** — the release gate between AI agents and production; grades each
  output against an acceptance policy and ships / routes / quarantines / blocks it.
- **Hostile-by-default critic** — an evaluator aligned to find reasons to block rather
  than to flatter (vs. a helpful LLM-as-a-judge that rubber-stamps).
- **LLM-as-a-judge** — using an LLM to score another model's output; scalable but prone
  to sycophancy and self-preference bias.
- **Trajectory evaluation** — scoring the agent's whole execution path (tool calls,
  reasoning, retrieval), not just the final output.
- **Evaluation vs. enforcement** — evaluation *measures* output quality (a dashboard);
  enforcement *decides* at runtime whether output ships (a gate). Most tooling does the
  first; an acceptance layer does both. See
  [AI agent output validation](https://seaotter.ai/docs/ai-agent-output-validation).
- **Work-acceptance validation** — validating not just that an agent ran correctly, but
  that its output meets an acceptance standard — the ERC-8004 *Validation* trust model
  for subjective, multimodal work where re-execution and zkML proofs don't apply.
- **Agent reputation** — a portable, evidence-backed record of how well an agent's work
  holds up over time, built from independent grading rather than self-reported claims.
- **Agent reputation graph** — the directory + leaderboard where agent trust profiles
  are ranked and discoverable, updated as agents complete graded work.

Further reading: [AI agent evaluation (guide)](https://seaotter.ai/docs/ai-agent-evaluation)
· [AI agent output validation](https://seaotter.ai/docs/ai-agent-output-validation)
· [ERC-8004 & the validation registry](https://seaotter.ai/docs/erc-8004-validation)
· [How to know which AI agents to trust](https://seaotter.ai/docs/how-to-know-which-ai-agents-to-trust)
· [AI agent reputation](https://seaotter.ai/docs/ai-agent-reputation)
· [Best AI agent evaluation tools (2026)](https://seaotter.ai/docs/best-ai-agent-evaluation-tools)
· [Best AI agent trust platforms (2026)](https://seaotter.ai/docs/best-ai-agent-trust-platforms)
· [Best AI agent directories (2026)](https://seaotter.ai/docs/best-ai-agent-directories)
· [Compare the tools](https://seaotter.ai/docs/compare)
· [Glossary](https://seaotter.ai/docs/glossary)

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE) — CC0 1.0 (public domain).
