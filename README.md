# Hackathon 5 — Customer Success Digital FTE
### Stage 1 Prototype

**Project Owner:** Mehreen Asghar
**Stage:** 1 — Prototype Foundation Only
**Hackathon:** Hackathon 5

---

## Problem Statement

Customer success teams at SaaS companies spend the majority of their time answering repetitive, routine inquiries — billing questions, password resets, refund requests, and basic how-to questions. These consume agent time that should be reserved for complex, high-value customer relationships.

This project prototypes a **Customer Success Digital FTE** — an AI agent that autonomously handles tier-1 support inquiries across multiple channels, detects when escalation is needed, and formats responses appropriately for each channel.

---

## What This Prototype Does

The Stage 1 prototype simulates an AI support agent that:

- Receives inbound customer messages (simulated — no live APIs)
- Identifies the customer and retrieves their history
- Detects sentiment, urgency, and escalation triggers
- Searches a local knowledge base for relevant answers
- Formats responses differently depending on the channel
- Creates mock support tickets
- Escalates to a human agent when required

---

## Channels Supported (Simulated)

| Channel | Response Style |
|---|---|
| **Gmail** | Formal, detailed, professional salutation |
| **WhatsApp** | Short, conversational, plain language |
| **Web Form** | Balanced, structured, action-oriented |

---

## MCP Tools (Prototype)

| Tool | Purpose |
|---|---|
| `search_kb` | Search the local knowledge base for relevant content |
| `create_ticket` | Create a mock support ticket in memory |
| `get_history` | Retrieve mock customer interaction history |
| `send_response` | Format and deliver a channel-specific response |
| `escalate_to_human` | Flag the case for human agent review |

---

## Escalation Logic

The agent checks every message for escalation triggers before attempting to auto-respond:

- **Refund request** → Review required
- **Pricing negotiation** → Sales team handoff
- **Legal language** → Immediate escalation (high priority)
- **Angry customer** → Empathy-first + human review
- **VIP complaint** → Priority escalation
- **Security issue** → Immediate escalation (critical)

---

## Repository Structure

```
hackathon5-digital-fte-mehreen-stage1/
├── README.md                          ← This file
├── context/                           ← Support context for the agent
│   ├── company-profile.md             ← Fake SaaS company overview
│   ├── product-docs.md                ← Product knowledge base
│   ├── escalation-rules.md            ← When and how to escalate
│   ├── brand-voice.md                 ← Tone per channel
│   └── sample-tickets.json            ← Mock customer ticket examples
├── specs/                             ← Project specifications
│   ├── customer-success-fte-spec.md   ← Stage 1 spec document
│   ├── agent-skills.md                ← What the agent can do
│   ├── discovery-log.md               ← Assumptions, risks, learnings
│   └── prompt-history.md              ← Design decisions for judges
├── src/
│   └── agent/
│       ├── customer_success_agent.py  ← Main prototype agent logic
│       └── mcp_server.py              ← MCP tool definitions
└── tests/
    └── test_agent.py                  ← Prototype test suite
```

---

## How to Run the Prototype

```bash
# No external dependencies required for Stage 1

# Install minimal requirements
pip install pytest

# Run the agent demo
python src/agent/customer_success_agent.py

# Run the tests
pytest tests/ -v
```

The agent demo processes a set of sample messages and prints formatted responses for each channel. No API keys or services required.

---

## How Judges Should Review This Repo

1. **Start here:** Read [specs/customer-success-fte-spec.md](specs/customer-success-fte-spec.md) for scope and goals
2. **Design decisions:** Read [specs/prompt-history.md](specs/prompt-history.md) for all build decisions
3. **Agent logic:** Review [src/agent/customer_success_agent.py](src/agent/customer_success_agent.py)
4. **MCP tools:** Review [src/agent/mcp_server.py](src/agent/mcp_server.py)
5. **Context/KB:** Browse the [context/](context/) folder
6. **Tests:** Run `pytest tests/ -v` to see passing tests

---

## What Is NOT Implemented (By Design)

This is a **Stage 1 prototype only**. The following are intentionally not implemented:

| Feature | Reason |
|---|---|
| Gmail API | Stage 2 — requires OAuth2 + webhooks |
| Twilio WhatsApp | Stage 2 — requires Twilio credentials |
| PostgreSQL / any database | Stage 2 — data model stabilizes in Stage 1 |
| Kafka message queue | Stage 2 — async processing not needed yet |
| External CRM | Stage 2 — CRM choice not finalized |
| Kubernetes / deployment | Stage 3 — production infrastructure |
| Real LLM API calls | Stage 2 — prototype validates flow first |
| Authentication | Stage 2 — security layer comes after prototype |

---

*Hackathon 5 · Customer Success Digital FTE · Stage 1 · Mehreen Asghar*
