# Design log (repo-local memory)

Lets each consultation build on the last. It lives in the user's repository, in their language, readable by humans. Use it only inside a project; skip it silently otherwise.

```
docs/design-consult/        # or beside an existing design folder; reuse one if found
├── game-profile.md         # what the game is now
├── decisions.md            # one row per decision, with status
├── sources.md              # evidence already gathered
├── history.md              # condensed older consults
└── consults/YYYY-MM-DD-<topic>.md
```

## At the start

Read `game-profile.md`, `decisions.md`, `history.md`; grep `consults/` and `sources.md` for the topic and read only matches. Reuse evidence, name conflicts with adopted decisions, and ask in one line how `proposed`/`testing` ones went — those outcomes are evidence no database has.

## At the end

If `docs/design-consult/` (or an existing design folder) is already there, update it without asking and say what you wrote in one line. If there is none, ask once before creating it: say it keeps the game's profile, decisions and sources in their repository so the next consult builds on this one, and that nothing in it is sent anywhere. Create it only after a yes; after a no, skip it for the rest of the conversation.

**consults/<date>-<topic>.md** — the question, mode, related past consults, 結論, 根拠 (one line per precedent with label and link), 次に試すこと (each with the result that would change the decision), 残った穴. Only what a future consult needs.

**decisions.md** — append; never rewrite past rows except status and outcome.

```
| 日付 | 判断 | 状態 | 結果・メモ | 相談 |
```

Status: `proposed` → `adopted` / `rejected` / `testing`. Change it only when the user decides or reports a result (if implemented in the same session, `testing`, with any measured before → after). Record outcomes with dates; if the user's words are ambiguous, say how you read them.

**sources.md** — sources you actually read, so they aren't searched again.

```
| URL | 作品・話題 | 1行メモ | ラベル | GameGeneへ送信 |
```

**game-profile.md** — create in the first consult, refine as constraints appear; mark inferences (推測).

```
- ジャンル・形式:
- 規模（人数・期間・プレイ時間）:
- 狙う体験（ピラー）:
- 制約・やらないこと（推奨や実験がこれに反したら外す。退けた案の理由もここに足す）:
- 参考にしている作品:
```

## Keep it small

Condense without asking when a limit is exceeded (git keeps history), and say what you condensed.

| File | Limit | Condense by |
|---|---|---|
| `consults/` | > 8 files | fold all but the 5 newest into `history.md` |
| `decisions.md` | > 25 rows | move rejected and superseded rows to `history.md` |
| `sources.md` | > 40 rows | drop duplicates and unused rows; keep rows marked sent |
| `game-profile.md` | > ~30 lines | rewrite to the current truth |
| `history.md` | > ~80 lines | merge by topic; keep decision, outcome, reason |

`history.md` is organized by topic, one line per decision: what, status and date, outcome, why.

## Privacy

The log holds unreleased details. Never copy it into searches, `intent` fields, or anything sent outside.
