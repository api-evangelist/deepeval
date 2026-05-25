# DeepEval (deepeval)

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
