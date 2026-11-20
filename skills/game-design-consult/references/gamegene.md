# Using GameGene

Tool names may carry a server prefix; match on the suffix. If deferred, load them in one ToolSearch call. If no GameGene tool exists, say in one line that the GameGene MCP server is not connected (https://gamegene.app/mcp) and go on with general knowledge and the web.

## Record types

- **claims (工夫)** — one game's decision: what the makers did, why, what they rejected, where it came from.
- **genes** — a mechanic traced across games.
- **joseki (定石)** — a recurring judgement with its cases. Case `relation`: `names` (maker named it), `same_judgment` (GameGene's reading — say so), `departure` (deliberately broke it).
- **struggles** — recorded design problems, each with answers from several games. Best hit when the user describes a symptom.
- **reception** (on claims) — how players received the decision (landed / split / unintended). `assessmentJa` is GameGene's reading; voices don't indicate how many felt so.

## Calls

1. `gamegene_search` with a design word (Japanese works best) and a short, generic `intent`. Narrow with `types`.
2. `gamegene_struggles` for a symptom; if nothing matches, search the underlying design word and joseki.
3. `gamegene_claims` in **one** call, `format: "cite"`. Prefer `geneSlugs` or games named in a struggle/joseki record; heavily documented games can eat the budget. If `truncatedByBudget`, page with `offset`.
4. `gamegene_joseki` with a `slug` for the full record and departures; without one, the light list of all joseki.
5. `gamegene_genes` with `compact: true` only when you need the whole mechanic map.

## Citation rules

- Makers' own words **only** when `source.type` is interview or talk **and** `directness` is direct; otherwise GameGene's reading.
- Draft/researching, or `opposingSources > 0`: say unconfirmed / disputed. `ai_generated` alone is not a warning.
- `source.author` is who wrote the source, not necessarily the person in the claim.
- For an English page, insert `/en` right after the domain.
