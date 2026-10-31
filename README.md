# Top AI Projects

**Tarun Singh Chauhan** — AI / GenAI / LLM Engineer · Jaipur, India
[Portfolio](https://tarunchauhan.vercel.app) · [LinkedIn](https://linkedin.com/in/tarunchauhanml) · [GitHub](https://github.com/TarunSinghChauhan) · tarunsinghchauhan088@gmail.com

A single index of my best AI engineering work: LLM evaluation, multi-agent pipelines, RAG operations, human-in-the-loop safety, and LLM observability. Every project below is its own repository with its own README, tests and setup instructions.

## At a glance

| Project | What it is | Stack | Repo |
|---|---|---|---|
| **LLM Evaluation Harness & Red-Teaming** | Benchmarks GPT-4o and Claude with statistical rigor; LLM-as-judge ensemble; adversarial testing | Python, LangGraph, LangSmith, MLflow, FastAPI, Docker, Redis | [llm-eval-harness](https://github.com/TarunSinghChauhan/llm-eval-harness) |
| **Multi-Agent Code Review & Auto-Remediation** | 3-agent LangGraph pipeline that finds vulnerabilities and proposes fixes under a cost cap | Python, LangGraph, OpenRouter, FastAPI, PostgreSQL, Redis, Docker | [multi-agent-code-review](https://github.com/TarunSinghChauhan/multi-agent-code-review) |
| **Real-Time RAG Ops Platform** | RAG pipeline with embedding-drift detection, automated re-indexing and an ops dashboard | Python, FastAPI, Qdrant, LangChain, Redis, Chart.js | [rag-ops-platform](https://github.com/TarunSinghChauhan/rag-ops-platform) |
| **ORACLE — LLM Observability** | Span tracing, anomaly and output-drift detection, alerting and a dashboard for LLM apps | Python, SQLite, Flask, LangChain callbacks, GitHub Actions | [Oracle](https://github.com/TarunSinghChauhan/Oracle) |
| **HITL Approval Agent** | Stateful human-in-the-loop agent that gates execution on a confidence score, with an audit trail | Next.js 14, Prisma, PostgreSQL, Groq (Llama 3.3-70B) | [hitl-approval-agent](https://github.com/TarunSinghChauhan/hitl-approval-agent) · [live demo](https://hitl-approval-agent.vercel.app) |
| **CodeCave — Bilingual LLM Code Tutor** | Turns pasted code into spoken, step-by-step explanations in English and Hindi | Gemini API, Groq API, Node.js (Vercel), Web Speech API | [CodeCave](https://github.com/TarunSinghChauhan/CodeCave) |

## 1. LLM Evaluation Harness & Red-Teaming Framework
Python · LangGraph · LangSmith · OpenAI/Anthropic APIs · MLflow · FastAPI · Docker · Redis

- Benchmarks GPT-4o and Claude Sonnet on 50 MMLU prompts using ROUGE-L, BERTScore and bootstrapped 95% confidence intervals; regression detection runs in under 4 minutes per CI run instead of days.
- LLM-as-judge ensemble (GPT-4o + Claude) with inter-rater agreement scoring (Cohen's kappa = 0.81) across 20+ adversarial red-team attack patterns.

## 2. Multi-Agent Code Review & Auto-Remediation System
Python · LangGraph · OpenRouter · FastAPI · Docker · PostgreSQL · Redis

- 3-agent LangGraph pipeline (static analysis, OWASP scanner, LLM fix proposal) that stays under $0.50 per review; found 23 issues, including 4 critical vulnerabilities, in benchmark testing.
- 12-pattern OWASP scanner (regex + AST, zero API cost) with typed LangGraph state contracts that remove silent LLM output failures.

## 3. Real-Time RAG Ops Platform with Drift Detection
Python · FastAPI · Qdrant · LangChain · Redis · Docker · Chart.js

- Production-style RAG pipeline with Qdrant vector search and cosine-similarity drift detection that triggers automated re-indexing; 75% Redis cache hit rate on repeated queries.
- Real-time dashboard tracking p95/p99 latency SLOs, retrieval quality (Hit@5) and embedding drift score.

## 4. ORACLE — LLM Observability and Anomaly Detection
Python · SQLite · Flask · LangChain · GitHub Actions

- Span tracer with SQLite persistence, z-score latency and cost anomaly detection, output-drift detection (Jaccard similarity on word shingles), Slack-compatible webhook alerts, a live dashboard, and a LangChain callback handler. Fully offline: no API keys needed.
- CLI: `oracle scan` (with `--webhook`, `--fail-on` for CI gating, `--watch`) and `oracle prune`. CI runs the suite on Python 3.10 to 3.13, with a separate job proving the core works without LangChain installed.
- Engineering work on top of the first version, each reproduced before it was fixed: a thread-safety bug that silently dropped spans in parallel LangChain chains, a quadratic anomaly scan (rewritten as a single linear pass with exact running statistics), a stored XSS in the dashboard, and false "critical" alerts for spans that were faster than a zero-variance baseline. 180+ tests.

## 5. HITL Approval Agent — Stateful AI Safety System
Next.js 14 · Prisma · PostgreSQL · Groq (Llama 3.3-70B)

- Gates execution on a self-assessed confidence score: auto-executes above the threshold, otherwise persists the task with a full JSON audit trail for human approve/reject.
- Documented a real architectural gap: the gate relied only on self-reported confidence, so a softly worded high-risk request could auto-execute. That finding motivated per-category approval thresholds.

## 6. CodeCave — Bilingual LLM Code Tutor
Gemini API · Groq API · Node.js (Vercel Serverless) · JavaScript · Web Speech API · Web Workers

- Bilingual (English/Hindi) tutor that turns pasted Python or JavaScript into spoken step-by-step explanations, using a strict JSON output schema, server-side validation and prompt-injection mitigation so malformed output never reaches the UI.
- Provider-fallback layer (Gemini models, then Groq) with runtime model discovery and 503/429 retries, response caching, and a rule-based offline explainer for free-tier resilience. API keys stay server-side.

## More

- [finance-research-agent](https://github.com/TarunSinghChauhan/finance-research-agent) — FastAPI research agent over financial data tools, with Postgres-backed storage and a full unit-test suite.
- [llm-inference-engine](https://github.com/TarunSinghChauhan/llm-inference-engine) — llama.cpp-based inference server with request batching, a Redis queue and load-test/quantization benchmarks.
- [CodePulse](https://github.com/TarunSinghChauhan/CodePulse) — Next.js/TypeScript code-playback and narration tool, tested with Vitest and Testing Library.

## What I look for in AI systems

Evaluation before optimisation, cost caps and typed contracts around every LLM call, and a human in the loop wherever a wrong answer is expensive.
