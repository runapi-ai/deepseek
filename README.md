<p align="center">
  <a href="https://github.com/runapi-ai/deepseek">
    <h3 align="center">DeepSeek API Skill for RunAPI</h3>
  </a>
</p>

<p align="center">
  Configure OpenAI-compatible or Anthropic-compatible clients to use DeepSeek models on RunAPI.
</p>

<p align="center">
  <a href="https://runapi.ai/models/deepseek"><strong>Model Reference</strong></a> | <a href="https://github.com/runapi-ai/deepseek"><strong>Skill Repo</strong></a> | <a href="https://runapi.ai/models"><strong>All Models</strong></a>
</p>

<div align="center">

[![skills.sh](https://www.skills.sh/b/runapi-ai/deepseek)](https://www.skills.sh/runapi-ai/deepseek/deepseek)
[![ClawHub](https://img.shields.io/badge/ClawHub-runapi--deepseek-111827)](https://clawhub.ai/runapi-ai/runapi-deepseek)
[![License](https://img.shields.io/github/license/runapi-ai/deepseek)](https://github.com/runapi-ai/deepseek/blob/main/LICENSE)

</div>
<br/>

Call the DeepSeek API through RunAPI with OpenAI-compatible clients or
Anthropic-compatible Messages clients. Point clients at `https://runapi.ai/v1`
for Chat Completions, or `https://runapi.ai` for `/v1/messages`, send
`deepseek-v4-pro` or `deepseek-v4-flash`, and pay through one RunAPI balance.
This skill teaches Claude Code, Codex, Gemini CLI, Cursor, and 50+ agents how
to wire DeepSeek requests through RunAPI.

The canonical agent file is `skills/deepseek/SKILL.md`.

## Install the skill

```bash
npx skills add runapi-ai/deepseek -g
```

Or paste this prompt to your AI agent:

```text
Install the deepseek skill for me:

1. Clone https://github.com/runapi-ai/deepseek
2. Copy the skills/deepseek/ directory into your
   user-level skills directory (e.g. ~/.claude/skills/
   for Claude Code, ~/.codex/skills/ for Codex).
3. Verify that SKILL.md is present.
4. Confirm the install path when done.
```

## Use DeepSeek on RunAPI

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_RUNAPI_TOKEN",
    base_url="https://runapi.ai/v1",
)

response = client.chat.completions.create(
    model="deepseek-v4-pro",
    messages=[{"role": "user", "content": "Hello, DeepSeek!"}],
)
print(response.choices[0].message.content)
```

```javascript
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: "YOUR_RUNAPI_TOKEN",
  baseURL: "https://runapi.ai/v1",
});

const response = await client.chat.completions.create({
  model: "deepseek-v4-flash",
  messages: [{ role: "user", content: "Hello, DeepSeek!" }],
});
console.log(response.choices[0].message.content);
```

```bash
curl -X POST "https://runapi.ai/v1/chat/completions" \
  -H "Authorization: Bearer YOUR_RUNAPI_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek-v4-pro",
    "messages": [{"role": "user", "content": "Hello, DeepSeek!"}]
  }'
```

Get a RunAPI API Key at <https://runapi.ai/api_keys>.

## Anthropic-compatible option

```bash
ANTHROPIC_BASE_URL=https://runapi.ai \
ANTHROPIC_API_KEY=YOUR_RUNAPI_TOKEN \
claude
```

Use model `deepseek-v4-pro` or `deepseek-v4-flash` when calling
`POST /v1/messages`.

## Supported DeepSeek models

| Model ID | Notes |
|---|---|
| `deepseek-v4-pro` | Higher quality DeepSeek chat and reasoning tasks |
| `deepseek-v4-flash` | Fast DeepSeek chat |

## Routing

- DeepSeek API on RunAPI: <https://runapi.ai/models/deepseek>
- Provider page: <https://runapi.ai/providers/deepseek>
- Browse the full RunAPI catalog: <https://runapi.ai/models>
- Skill repository: <https://github.com/runapi-ai/deepseek>

## Agent rules

- Keep API keys in `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, or your secret
  manager; never inline them in commits or shell history.
- Stream long responses (`stream: true`) so the agent can release the
  terminal/IO loop early.
- For pricing, rate-limit, and commercial-usage answers, link to
  <https://runapi.ai/models/deepseek> rather than this README.

## License

Licensed under the Apache License, Version 2.0.
