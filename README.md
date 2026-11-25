# Money Calculators

広告なし・計算が正確・買い切りの「お金の計算機」アプリを作るためのマーケティングのリポジトリ。
いまはアプリを作る前の段階で、ターゲット・メッセージ・紹介ページ・需要の確認を進める。

## このリポジトリが生まれた経緯

市場を探すツール **App Store Optimization Explorer** で、App Store と Google Play を調べた結果から始まった。

| | リポジトリ | ローカル |
|---|---|---|
| 市場を探すツール | [shinseitaro/app-store-optimization-explorer](https://github.com/shinseitaro/app-store-optimization-explorer)（private） | `../../app-store-optimization-explorer` |
| 調査の結論 | 同上の [`docs/calculator-deep-dive.md`](https://github.com/shinseitaro/app-store-optimization-explorer/blob/main/docs/calculator-deep-dive.md) | `../../app-store-optimization-explorer/docs/calculator-deep-dive.md` |

役割の分け方:

- **app-store-optimization-explorer**：市場を調べる作業（ツールを動かす、日本の市場を調べるなど）。調査の結果と結論はあちらに置く。
- **money-calculators（ここ）**：作ると決めた製品を売り込む作業（ブランド、ターゲット、紹介ページなど）。いずれアプリのコードもここから切り出す。

## 調査の結論（要約）

詳しくは `calculator-deep-dive.md`（調査日 2026-10-09、米国）。

- お金の計算機は10年以上続く定番の分野。上位アプリの多くは2010〜2015年にリリースされたもの。
- 既存アプリへの不満の中心は**広告**。低評価レビューの41%、2026年のレビューに限ると68%。
- 次に多いのは「計算が間違っている」「必要な機能が無い」。お金に詳しい人が作る意味がある。
- 計算機の Google 検索は2024年ごろから減っている。アプリ（ストア内の検索）を中心にし、Web は補助にするのがよさそう。

## 2つの製品候補

どちらも「広告なし・計算が正確・買い切り」が軸。最初は両方を並べて進める予定だったが、**2026-11-09 に B はいったん止め、A に集中すると決めた**（[理由](docs/discussions/pro-financial-calc/20261109/03-exam-calculator-rules.md)：B の一番大きな相手の受験生は、試験で使う物理電卓と同じ押し方を求めるが、それには TI・HP の製品をまねる必要がある）。
使う人も伝え方も違うので、**ブランドは別々にする**（2026-11-08 決定）。

| | A. ローン・複利の計算機（`loan-simulator`） | B. プロ用の金融電卓（`pro-financial-calc`） |
|---|---|---|
| 使う人 | 車や家を買う人、積み立てる人 | 金融の資格試験の受験生、学生、不動産・融資の実務家 |
| 市場 | 大きい（最大710万インストール） | 小さめ（最大55万インストール） |
| お金を払うか | 未確認。無料を渡り歩く人が多そう | 払っている（$4〜$17 の有料アプリが売れている） |
| 既存アプリの弱点 | 広告、平均と実際の利息の混同、実務の項目が足りない | 更新で動かなくなる、使い方がわからない、計算の誤り |
| 差別化 | 追加返済・返済スケジュールなど実務で要る機能 | TVM・NPV・IRR・債券などを正確に、わかりやすく |

注意: 「HP 12c」「BA II Plus」は他社の製品名（商標）。B は同じ計算ができる別の名前の電卓にする。

## 構成

```
money-calculators/
├── README.md
├── CLAUDE.md             新しいセッションで最初に読む案内と、記録の残し方のルール
├── docs/
│   └── discussions/      議論の記録（対象/日付/番号-テーマ.md。書き換えずに積み上げる）
│       ├── shared/           A・B に共通、リポジトリ全体のこと
│       ├── loan-simulator/
│       └── pro-financial-calc/
├── loan-simulator/       A：決めたこと（ブランド、ターゲット、メッセージ、紹介ページ）
└── pro-financial-calc/   B：同上
```

ディレクトリは必要になったときに作る。
議論の記録と「決めたこと」の分け方は `CLAUDE.md` を参照（[2026-11-08 決定](docs/discussions/shared/20261108/01-how-to-keep-records.md)）。

## 次にやること

1. **ターゲットとメッセージを決める**：A・B それぞれ、誰に・何を・どう伝えるか。
   - A は決めた（2026-11-08）：[`loan-simulator/target-and-message.md`](loan-simulator/target-and-message.md)
   - B は止めている（2026-11-09）。
2. **機能と画面を決める**（コードは `../../loanchart`。ClojureDart で Android とウェブ）：A は決めた（2026-11-08）：[`loan-simulator/features-and-screens.md`](loan-simulator/features-and-screens.md)。最初は Android、全部無料。画面を Google Stitch で試す（[プロンプト](loan-simulator/design/stitch-prompts.md)）。
3. **ブランドを決める**：A・B それぞれの名前、トーン、見た目。
   - A の名前は **LoanChart**（ローンチャート）、人柄は「落ち着いている・正直・飾らない」に決めた（2026-11-08）：[`loan-simulator/brand.md`](loan-simulator/brand.md)。話し方と見た目はまだ。
4. **紹介ページを作る**：「広告なし・買い切りの計算機」に興味を示す人がいるか確かめる。
5. ~~反応を比べて、先に作る方を決める~~ → A に決めた（2026-11-09。B は止めている）。

市場の調査で残っていること（金融電卓の使われ方、日本の市場）は
app-store-optimization-explorer の `HANDOFF.md`「4.1」で進める。
「実物を触る」は、A の Android のアプリ5つを 2026-11-08 にこちらで行った
（[まとめ](docs/discussions/loan-simulator/20261108/08-hands-on-summary.md)）。iOS はまだ。B の金融電卓は Android の3つを 2026-11-09 に触った（[結果](docs/discussions/pro-financial-calc/20261109/02-hands-on-results.md)）。
