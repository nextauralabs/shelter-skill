# Shelter Agent Skill

Connect AI agents to your real bank data. Read-only access to financial health, cash forecasts, spending insights, and AI coaching — powered by Plaid.

## What it does

| Ask your agent... | Endpoint |
|---|---|
| "How am I doing?" | `GET /v1/status` |
| "When do I run out of money?" | `GET /v1/runway` |
| "What does next week look like?" | `GET /v1/forecast` |
| "Any problems I should know about?" | `GET /v1/alerts` |
| "Where am I wasting money?" | `GET /v1/opportunities` |
| "Can I afford $200 headphones?" | `POST /v1/affordability` |
| "Give me today's coaching" | `GET /v1/coach/daily` |
| Complex financial questions | `POST /v1/ask` |

## Install

### Claude Code (marketplace)

```
/plugin marketplace add nextauralabs/shelter-skill
/plugin install shelter@shelter-skills
```

### npm

```bash
npm install -g @shelter/agent-skill
```

### Manual

Copy `SKILL.md` and `references/` into `~/.claude/skills/shelter/`.

### OpenClaw / ClawHub

```bash
clawhub install shelter
```

## Setup

1. **Sign up** at [shelterfinance.com](https://shelterfinance.com)
2. **Connect your bank** via Plaid (~60 seconds)
3. **Create an API key** at [shelterfinance.com/settings/api-keys](https://shelterfinance.com/settings/api-keys)
4. **Set your environment variable**:
   ```bash
   export SHELTER_API_KEY="wv_your_key_here"
   ```
5. **Test**:
   ```bash
   curl -s -H "X-Shelter-Key: $SHELTER_API_KEY" \
     https://api.shelterfinance.com/agent/v1/status
   ```

## Security

- **Read-only** — can never move money
- **Scoped API keys** — you choose what the key can access
- **No raw bank data** — returns computed insights, not transactions
- **Keys are hashed** — secrets are never stored in plain text
- **Audit logging** — every API call is logged
- **Instant revocation** — disable any key from your settings

## License

MIT
