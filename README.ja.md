# GameGene MCP

[English](README.md) | **日本語**

[![Connect the GameGene MCP](https://img.shields.io/badge/MCP-connect%20GameGene-6e56cf)](https://gamegene.app/mcp)
[![mcptry](https://mcptry.com/badge/app.gamegene/gamegene)](https://mcptry.com/servers/app.gamegene/gamegene)
[![GameGene MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/app.gamegene/gamegene/badges/score.svg)](https://glama.ai/mcp/connectors/app.gamegene/gamegene)

**同じ設計の判断に先に当たった作り手が、何を選び何を捨てたかを、出典つきで AI から引けます。**

[GameGene](https://gamegene.app) は、ゲームの設計の系譜を記録するサイトです。どの作品がどんな判断に当たり、作り手が何を選び、なぜそうし、何を捨てたかを、講演・インタビュー・ポストモーテムの出典つきで記録しています。GameGene の MCP サーバーをつなぐと、Claude・ChatGPT・Claude Code・Codex・VS Code などの MCP クライアントから、作業の途中でこの記録を読めます。

この repo は、サーバーの公開の入口です。できること、つなぎ方、不具合の報告先を置いています。サーバーは GameGene が運営していて、ソースはこの repo にはありません。

## つなぎ方

接続先の URL:

```
https://gamegene.app/api/mcp
```

要るのは GameGene のアカウント (無料) だけです。つなぐときに一度だけ、OAuth でサインインします。

| クライアント | 手順 |
|---|---|
| Claude | コネクタの «探索» で **GameGene** を検索して接続。見つからなければ、上の URL でカスタムコネクタを追加 |
| ChatGPT | アプリの一覧へは申請中。いまは開発者モードを有効にして、上の URL でコネクタを作成 |
| Claude Code | `claude mcp add --transport http gamegene https://gamegene.app/api/mcp` の後、`/mcp` を開いてサインイン |
| Codex CLI (0.166 以降) | `codex mcp add gamegene --url https://gamegene.app/api/mcp` |
| VS Code | コマンドパレット → **MCP: Add Server** → HTTP → 上の URL |

画面つきの手順は **[gamegene.app/mcp](https://gamegene.app/mcp)** にあります。

## こんなことを訊けます

- «ローグライクを作っている。負けを理不尽に感じさせない作り方の先例を、作り手の狙いと一緒に挙げて»
- «敵の次の行動を見せる仕組みはどこから来た？採り入れた作品と、その狙いは»
- «この案はもう誰かが出している？近い作品を出典つきで»

AI には、使った記録の出典と GameGene のページを添えて答え、記録が無いことは «記録が無い» と分けて言うよう伝えています。

## ツール

どのツールを呼ぶかは AI が選びます。主なもの:

| ツール | 返すもの |
|---|---|
| `gamegene_search` | 語に当たる作品・Gene・人物・工夫・トリビア・定石 |
| `gamegene_game` | 作品1本の全体 |
| `gamegene_claims` | 工夫 (主張) と、その根拠 |
| `gamegene_joseki` | 定石 (作品をまたいで繰り返し現れる設計の判断) と、その出所 |
| `gamegene_person` | 人物1人: 関わった作品と発言 |

いまの全部の一覧は [gamegene.app/mcp](https://gamegene.app/mcp#tools) にあります。サーバーは読むだけで、記録を書き換えることはできません。

## プランと回数

| プラン | 1日の回数 | 質問の目安 | 1分の回数 |
|---|---|---|---|
| Free | 200 | 10問ほど | 20 |
| Supporter | 1,000 | 60問ほど | 30 |

1日の上限は日本時間の0時に戻ります。最新の数は [gamegene.app/mcp](https://gamegene.app/mcp#limits) にあります。

## 記録が無かったとき

欲しい作品や設計の問いの記録が無ければ、**GameGene の調査依頼** を出してください: [gamegene.app/feedback](https://gamegene.app/feedback?panel=submit)。そのまま調査の列に入り、結果が出たら知らせます。検索で見つからなかったことも記録に残り、毎日の調査の材料になります。

記録の不足は、この repo の issue ではなく調査依頼へお願いします。そのほうが早く対応できます。

## issue

この repo の issue で受けるもの:

- **不具合**: ツールがエラーになる、誤ったものを返す、クライアントからつながらない
- **ツールへの要望**: AI が使いにくい、返す量が多すぎる・少なすぎる、新しいツールや引数が欲しい

## データの扱い

- AI アプリに送った質問や会話は、GameGene には届きません。届くのは AI が呼んだツールの引数だけです。
- 上限・不具合の調査・サービスの改善のために、呼び出しごとにツール名・引数・アカウント・接続したアプリ・日時を記録し、180日で消します。返した中身は記録しません。
- 詳しくは [gamegene.app/mcp](https://gamegene.app/mcp#data) と [プライバシーポリシー](https://gamegene.app/legal/privacy)

## 関連

- [game-genre-playbooks](https://github.com/gamegene-app/game-genre-playbooks): 同じ記録から作った、ジャンルごとの設計判断の無料スキル。このサーバーがあってもなくても使えます。
