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

Further reading: [AI agent evaluation (guide)](https://seaotter.ai/docs/ai-agent-evaluation)
· [Best AI agent evaluation tools (2026)](https://seaotter.ai/docs/best-ai-agent-evaluation-tools)
· [Compare the tools](https://seaotter.ai/docs/compare)
· [Glossary](https://seaotter.ai/docs/glossary)

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE) — CC0 1.0 (public domain).
