# GameGene MCP

**English** | [日本語](README.ja.md)

[![Connect the GameGene MCP](https://img.shields.io/badge/MCP-connect%20GameGene-6e56cf)](https://gamegene.app/mcp)
[![mcptry](https://mcptry.com/badge/app.gamegene/gamegene)](https://mcptry.com/servers/app.gamegene/gamegene)
[![GameGene MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/app.gamegene/gamegene/badges/score.svg)](https://glama.ai/mcp/connectors/app.gamegene/gamegene)

**Ask your AI how other developers made the same design call, and get their own words with a source.**

[GameGene](https://gamegene.app) records game design history: which games faced a design call, what their developers chose, why, and what they gave up, each traced to a talk, interview or postmortem. The GameGene MCP server lets Claude, ChatGPT, Claude Code, Codex, VS Code and other MCP clients read those records while you work.

This repository is the public front door for the server: what it does, how to connect, and where to report problems. The server itself is hosted by GameGene; its source is not in this repository.

## Connect

Server URL:

```
https://gamegene.app/api/mcp
```

All you need is a free GameGene account. You sign in once through OAuth when you connect.

| Client | How |
|---|---|
| Claude | Search for **GameGene** in the connector directory and connect, or add a custom connector with the URL above |
| ChatGPT | Under review for the app directory. For now, turn on developer mode and create a connector with the URL above |
| Claude Code | `claude mcp add --transport http gamegene https://gamegene.app/api/mcp`, then open `/mcp` and sign in |
| Codex CLI (0.166+) | `codex mcp add gamegene --url https://gamegene.app/api/mcp` |
| VS Code | Command Palette → **MCP: Add Server** → HTTP → the URL above |

Step-by-step instructions with screenshots: **[gamegene.app/mcp](https://gamegene.app/mcp)**

## What you can ask

- "I'm designing a roguelike. What precedents are there for making losses feel fair, and what did the designers intend?"
- "Where did showing the enemy's next move come from, and why did designers adopt it?"
- "Is my idea new, or has someone already shipped it? Show me the closest games with sources."

The AI is told to answer with the source and the GameGene page of each record it uses, and to say plainly when GameGene has no record of something.

## Tools

The AI picks the tools on its own. The main ones:

| Tool | What it returns |
|---|---|
| `gamegene_search` | Games, Genes, creators, design moves, trivia and heuristics matching a word |
| `gamegene_game` | Everything about one game |
| `gamegene_claims` | Design moves (claims) with their evidence |
| `gamegene_joseki` | Heuristics: design judgments that recur across games, with where they came from |
| `gamegene_person` | One creator: the games they worked on and what they said |

The full, current list is on [gamegene.app/mcp](https://gamegene.app/mcp#tools). The server is read-only: it cannot change any records.

## Plans and limits

| Plan | Calls a day | Roughly | Calls a minute |
|---|---|---|---|
| Free | 200 | 10 questions | 20 |
| Supporter | 1,000 | 60 questions | 30 |

The daily limit resets at midnight Japan time. Current figures are on [gamegene.app/mcp](https://gamegene.app/mcp#limits).

## When something is missing

If GameGene has no record of a game or a design question you need, **send a research request on GameGene**: [gamegene.app/feedback](https://gamegene.app/feedback?panel=submit). It goes straight into the research queue, and you are told when the result is in. Searches that find nothing are also logged and feed the daily research.

Please do not file missing records as issues here; the research request is faster.

## Issues

Use the issues in this repository for:

- **Bugs**: a tool errors, returns something wrong, or a client cannot connect
- **Tool feedback**: a tool is hard for the AI to use, returns too much or too little, or you want a new tool or argument

## Data

- Your questions and conversations with your AI app never reach GameGene. Only the arguments of the tools the AI calls do.
- Each call is logged (tool name, arguments, account, connected app, time) for limits, troubleshooting and improving the service, and deleted after 180 days. The content returned is not logged.
- Details: [gamegene.app/mcp](https://gamegene.app/mcp#data), [Privacy policy](https://gamegene.app/legal/privacy)

## Related

- [game-genre-playbooks](https://github.com/gamegene-app/game-genre-playbooks): a free skill for AI agents with genre-by-genre design calls built from the same records. It works with or without this server.
