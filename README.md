# DeepEval (deepeval)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

DeepEval is an open-source LLM evaluation framework — built and maintained by Confident AI — for testing and benchmarking large language model applications. It is structured like Pytest but specialized for LLM systems, providing 40+ research-backed metrics that run locally against any LLM provider. DeepEval ships as the `deepeval` Python package on PyPI together with a `deepeval` command-line tool, integrates natively with pytest, LangChain, LangGraph, LlamaIndex, OpenAI Agents, CrewAI, Pydantic AI, AWS AgentCore, Google ADK, and Strands, and powers Confident AI's commercial evaluation, observability, and red-teaming platform.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/deepeval/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=opensource-api-evangelist&utm_content=repo)

## Tags

LLM Evaluation, LLM Testing, Evaluation Framework, Evaluation Metrics, LLM Observability, LLM as a Judge, G-Eval, RAG Evaluation, Agent Evaluation, Hallucination Detection, Bias Detection, Toxicity Detection, Red Teaming, Benchmarks, MMLU, Synthetic Data Generation, Prompt Optimization, CI/CD, Pytest, Python, Open Source, Apache 2.0, MCP

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## Project Snapshot

| Field | Value |
|---|---|
| Project | [confident-ai/deepeval](https://github.com/confident-ai/deepeval) |
| Maintainer | [Confident AI](https://www.confident-ai.com) |
| License | Apache-2.0 |
| Language | Python |
| Latest release | v4.0.3 (May 21, 2026) |
| Install | `pip install -U deepeval` |
| GitHub stars | 15,600+ |
| Sibling project | [confident-ai/deepteam](https://github.com/confident-ai/deepteam) — LLM red teaming framework |

## Install & Quickstart

```bash
pip install -U deepeval
# Optional: connect local test runs to Confident AI cloud
deepeval login
# Run a deepeval test suite (pytest under the hood)
deepeval test run test_example.py
```

```python
from deepeval import assert_test
from deepeval.metrics import GEval
from deepeval.test_case import LLMTestCase, SingleTurnParams

def test_correctness():
    metric = GEval(
        name="Correctness",
        criteria="Determine if output is correct based on expected output.",
        evaluation_params=[SingleTurnParams.ACTUAL_OUTPUT, SingleTurnParams.EXPECTED_OUTPUT],
        threshold=0.5,
    )
    case = LLMTestCase(
        input="What if these shoes don't fit?",
        actual_output="You have 30 days for a full refund.",
        expected_output="30-day full refund available.",
        retrieval_context=["All customers eligible for 30 day refund."],
    )
    assert_test(case, [metric])
```

## Metrics

**General / Custom**

- G-Eval — research-backed LLM-as-a-judge for arbitrary criteria
- DAG — graph-based deterministic metric builder

**Agentic**

- Task Completion, Tool Correctness, Goal Accuracy, Step Efficiency, Plan Adherence, Plan Quality, Tool Use, Argument Correctness

**RAG**

- Answer Relevancy, Faithfulness, Contextual Recall, Contextual Precision, Contextual Relevancy, RAGAS

**Multi-Turn / Conversational**

- Knowledge Retention, Conversation Completeness, Turn Relevancy, Turn Faithfulness, Role Adherence

**MCP**

- Task Completion (MCP), MCP Use, Multi-Turn MCP Use

**Multimodal**

- Text to Image, Image Editing, Image Coherence, Image Helpfulness, Image Reference

**Safety / Quality**

- Hallucination, Summarization, Bias, Toxicity, JSON Correctness, Prompt Alignment

## Benchmarks

One-line benchmarking against MMLU, HellaSwag, DROP, BIG-Bench Hard, TruthfulQA, HumanEval, GSM8K.

## Evaluation Model Providers

OpenAI, Azure OpenAI, Anthropic, Gemini, Amazon Bedrock, Vertex AI, DeepSeek, Grok, Moonshot, OpenRouter, Ollama, vLLM, LM Studio, LiteLLM, Portkey.

## Framework Integrations

OpenAI Agents, LangChain, LangGraph, LlamaIndex, CrewAI, Pydantic AI, Anthropic, AWS AgentCore, Google ADK, Strands.

## Confident AI Platform

`deepeval login` connects local runs to the Confident AI cloud for shared regression reports, dataset annotation, production tracing, prompt versioning, multi-turn simulations, real-time alerting, AI risk assessments (OWASP Top 10 for Agentic Applications), and human-in-the-loop feedback.

| Tier | Price | Notes |
|---|---|---|
| Free | $0 forever | 2 seats, 1 project, 5 test runs/week, 1 GB-month traces |
| Starter | from $19.99 / user / mo | Full unit + regression testing, custom metrics, dataset annotation, HITL |
| Premium | from $49.99 / user / mo | Chat simulations, no-code workflows, pre-commit evals, full API access |
| Team | Custom | Git-based prompt workflows, dataset versioning, SSO, HIPAA / SOC 2 |
| Enterprise | Custom | Dedicated on-prem, 24/7 support, penetration testing |

## Common Properties

- [Website — confident-ai.com](https://www.confident-ai.com)
- [Portal — deepeval.com](https://deepeval.com)
- [Documentation — Getting Started](https://deepeval.com/docs/getting-started)
- [Repository — confident-ai/deepeval](https://github.com/confident-ai/deepeval)
- [GitHubOrganization — confident-ai](https://github.com/confident-ai)
- [Package — PyPI](https://pypi.org/project/deepeval/)
- [License — Apache-2.0](https://github.com/confident-ai/deepeval/blob/main/LICENSE.md)
- [Issues](https://github.com/confident-ai/deepeval/issues)
- [Releases / ChangeLog](https://github.com/confident-ai/deepeval/releases)
- [Contributing](https://github.com/confident-ai/deepeval/blob/main/CONTRIBUTING.md)
- [Blog](https://www.confident-ai.com/blog)
- [Forum — Discord](https://discord.com/invite/3SEyvpgu2f)
- [Pricing](https://www.confident-ai.com/pricing)
- [SignUp](https://app.confident-ai.com/auth/signup)
- [Application — Confident AI cloud](https://app.confident-ai.com)
- [Tool — DeepTeam (red teaming)](https://github.com/confident-ai/deepteam)
- [Tool — Confident MCP Server](https://github.com/confident-ai/confident-mcp-server)
- [Documentation — DeepTeam](https://trydeepteam.com)
- [CodeExamples — blog-examples](https://github.com/confident-ai/blog-examples)
- [Integrations — models](https://deepeval.com/integrations/models/openai)
- [Twitter](https://twitter.com/confident_ai)
- [LinkedIn](https://www.linkedin.com/company/confident-ai)
- [YouTube](https://www.youtube.com/@confident-ai)

## APIs

DeepEval is a Python framework and CLI — there is no public REST API surface for the framework itself. The framework runs evaluations locally and (optionally) syncs results to the Confident AI cloud. Confident AI advertises full API access on Premium and above, but no public OpenAPI specification or developer reference is published at this time. As a result this catalog entry does not include any OpenAPI artifacts.

## Maintainers

**FN:** Kin Lane

**Email:** info@apievangelist.com
