<p align="center">
  <a href="https://syntropylabs.ai">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/logo-horizontal-dark.svg">
      <img src="assets/logo-horizontal-light.svg" alt="SyntropyLabs" width="320">
    </picture>
  </a>
</p>

<p align="center">
  Observability and evaluation for LLM applications and agents.
</p>

<p align="center">
  <a href="https://syntropylabs.ai">Website</a> ·
  <a href="https://syntropylabs.ai/docs">Docs</a> ·
  <a href="https://pypi.org/project/syntropylabs-evalkit/">PyPI</a> ·
  <a href="https://www.npmjs.com/package/syntropylabs-evalkit">npm</a> ·
  <a href="mailto:founder@syntropylabs.ai">Contact</a>
</p>

---

SyntropyLabs shows you what your agent did, tests it before your users do, and scores every answer.

| Step | What it does |
| --- | --- |
| **Trace** | One `init()` call instruments your LLM clients, agent frameworks, HTTP calls and database queries. Every model call, tool call and token lands in one trace. |
| **Simulate** | Generate scenarios from your agent's prompt and tools, replay them against your real agent with synthetic users, and grade each run. |
| **Evaluate** | Score datasets and live traffic with LLM-as-judge and deterministic evaluators, and gate releases on the scores from CI. |
| **Optimize** | On the roadmap. |

## EvalKit SDKs

EvalKit is the open-source SDK that sends your traces to SyntropyLabs. It is Apache-2.0 licensed.

| Language | Repository | Install |
| --- | --- | --- |
| Python | [evalkit_sdk_py](https://github.com/Syntropylabs-ai/evalkit_sdk_py) | `pip install syntropylabs-evalkit` |
| TypeScript | [evalkit_sdk_ts](https://github.com/Syntropylabs-ai/evalkit_sdk_ts) | `npm install syntropylabs-evalkit` |

### Python

```python
import evalkit

evalkit.init(subscription_key="tk_live_...", service_name="my-service")

# Every OpenAI, Anthropic, HTTP and database call from here on is traced.
from openai import OpenAI

OpenAI().chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hello"}],
)
```

### TypeScript

```ts
import evalkit from "syntropylabs-evalkit";

evalkit.init({
  subscriptionKey: process.env.EVALKIT_SUBSCRIPTION_KEY!,
  serviceName: "my-service",
});

// Every OpenAI, Anthropic, HTTP and database call from here on is traced.
```

Your subscription key is on the Environments page of the [SyntropyLabs console](https://app.syntropylabs.ai), under Settings → This project → Environments.

### Coding agents

The `evalkit` command that comes with the Python SDK points a coding agent's own telemetry at SyntropyLabs. It supports Claude Code, Codex, Gemini CLI, Cursor, Windsurf and OpenCode.

```bash
evalkit coding install --vendor claude-code --key tk_live_...
```

## Contributing

Issues and pull requests are welcome on the SDK repositories. For anything else, write to [founder@syntropylabs.ai](mailto:founder@syntropylabs.ai).
