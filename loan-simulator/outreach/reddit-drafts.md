# Reddit の投稿の下書き

[議論 13](../../docs/discussions/loan-simulator/20261108/13-where-to-find-people.md) で決めた、紹介ページに人を呼ぶための投稿。
投稿はユーザーの Reddit アカウントで、ユーザーが行う。

**振り返りの日：2026-11-23**（最初の投稿から2週間）。

## 投稿の前に（掲示板ごとに必ず）

Reddit は自動での取得を止めているため、Claude は各掲示板の決まりを直接は読めなかった。Web 検索では決まりの本文が見つからなかった。

- [ ] 掲示板の右側（スマホでは「About」）の **Rules** を読む。「self-promotion」「surveys」「links」「apps」の決まりを探す
- [ ] 宣伝やアンケートが禁止なら、**リンクを載せない版**（下の A）にするか、その掲示板には投稿しない
- [ ] 迷ったら、投稿の前にモデレーターに「アンケートのリンクを載せてもよいか」をメッセージで聞く
- [ ] リンクは掲示板ごとの `?from=` 付きのものを使う（どこから来たかがアンケートに残る）

| 掲示板 | 種類 | リンク |
|---|---|---|
| r/FirstTimeHomeBuyer | A（主役の人たち） | `https://loanchart.netlify.app/?from=reddit-fthb` |
| r/Mortgages | A（主役の人たち） | `https://loanchart.netlify.app/?from=reddit-mortgages` |
| r/RealEstate | A（主役の人たち） | `https://loanchart.netlify.app/?from=reddit-realestate` |
| r/SideProject | B（作り手） | `https://loanchart.netlify.app/?from=reddit-sideproject`（**2026-11-09 に投稿済み**：[投稿](https://www.reddit.com/r/SideProject/comments/1xr9uy6/im_building_an_adfree_mortgage_calculator_for/)） |
| r/alphaandbetausers | C（試したい人） | `https://loanchart.netlify.app/?from=reddit-alphabeta` |

r/personalfinance は宣伝に厳しいことで知られる。決まりを読んで、許されていなければ投稿しない。

### 全部の掲示板で：下書きをそのまま使わない

**2026-11-09 訂正**：下書き A・B に「ローンの広告が出た」「payday loan の広告が出た」と書いていたが、Claude の作り話だった。実際に試したアプリで出た広告は、ふるさと納税・eSIM・求人など（[04](../../docs/discussions/loan-simulator/20261108/04-hands-on-karls-mortgage.md)、[05](../../docs/discussions/loan-simulator/20261108/05-hands-on-loan-deposit-tool.md)）。試したことに合う文に直した。**「I」で始まる文は、ユーザー本人にとって本当かを必ず確かめる。**

下書きは Claude（AI）が書いたもの。r/FirstTimeHomeBuyer は「主に AI が書いた投稿」を禁止している（決まり 9）。ほかの掲示板でも同じ決まりがありうる。
**下書きは「何を伝えるか」のメモとして使い、投稿の文はユーザー自身の言葉で書く。**

## 掲示板ごとの決まり（読んだもの）

### r/FirstTimeHomeBuyer（2026-11-08 に読んだ。[スクリーンショット](reddit-rules.jpg)）

決まりは10個。関係するもの：

- **3. No selling/promotion**：売る・宣伝することを禁止。サービスや、自分が関わるサイトへのリンクも宣伝に含む。破ると追放（ban）。DM・電話・メールの依頼も禁止。
- **4. No posts by industry professionals**：業界の人（不動産業者、ローン担当者、保険の担当者など）は、モデレーターの事前の許可なしに投稿できない。
- **9. No low-effort, karma farming, engagement bait, or AI-generated posts**：主に AI が書いた投稿は削除。
- 10. Moderator discretion：目的に合わない投稿はモデレーターが消せる。

判断：**リンクは載せられない。アプリを作っていると書くのも宣伝と見なされうる。下書き A はこの掲示板では使わない。**
できること：(1) 投稿せずに、掲示板の中を検索して読む（calculator、amortization、extra payment、ChatGPT など）。(2) モデレーターに、リンクなしの質問の投稿をしてよいか先に聞く。

**決定：(1) と (2) を両方やる**（[議論 2026-11-09/01](../../docs/discussions/loan-simulator/20261109/01-fthb-read-and-ask-mods.md)）。

#### r/FirstTimeHomeBuyer：読む

ブラウザで開いて、上位の投稿をいくつか読み、タイトルと要点（またはスクリーンショット）を Claude に渡す。投稿した人の名前は要らない。

| 調べる言葉 | 開くリンク |
|---|---|
| calculator | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=calculator&restrict_sr=1 |
| amortization | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=amortization&restrict_sr=1 |
| extra payment | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=%22extra+payment%22&restrict_sr=1 |
| ChatGPT | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=chatgpt&restrict_sr=1 |
| PMI | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=PMI+monthly+payment&restrict_sr=1 |
| spreadsheet | https://www.reddit.com/r/FirstTimeHomeBuyer/search/?q=spreadsheet&restrict_sr=1 |

見たいこと：何で計算しているか／何に困っているか／AI に聞いているか／税・保険・PMI を含めた支払いで迷っているか。

#### r/FirstTimeHomeBuyer：モデレーターに聞く

掲示板の「Message the mods」から送る。**文はユーザーの英語で書く。** 伝える点：

- 自分は個人で、広告のないローン計算のアプリを作っている（業界の人に当たるかもしれないので、先に聞いている）。
- 聞きたいのは「いま何を使って計算しているか、何に困っているか」だけ。
- 投稿にリンクもアプリの名前も載せない。DM も頼まない。
- そういう投稿をしてよいか。だめなら投稿しない。

返事が来るまで投稿しない。返事が来なければ投稿しない。


### r/Mortgages（2026-11-09 に読んだ）

決まりは4つ（R1〜R4）。関係するもの：

- **R1. Submission Guidelines**：投稿は住宅ローンについての質問か議論。**アンケートと投票（Surveys and polls）は禁止。**
- **R2. Advertising or soliciting**：会社・製品・サイト・**アプリ**の宣伝、**自分が持っているものや関わっているものの宣伝**、DM を頼むことは禁止。
- R4. Low-effort：中身のない投稿は禁止。

右の列に「Tools: houseeconomics.com」とあり、掲示板がすすめる計算の道具がある。

判断：**アンケートのリンクも、アプリを作っているという話も載せられない。この掲示板には投稿しない。読むだけにする。**

### r/SideProject と r/alphaandbetausers（2026-11-09 に見た）

どちらも**決まりの一覧がない**。説明文だけ。

| 掲示板 | 説明 | 規模 | 見た投稿の例 |
|---|---|---|---|
| r/SideProject | 個人の作品を見せて、建設的な感想をもらう場所 | 週34万人が訪問・週2万件の投稿 | 動くゲームを動画つきで見せ、「次はどのゲームがいい？」と聞く投稿（賛成2,365） |
| r/alphaandbetausers | アプリやサイトを試す人を探す場所 | 週1万人・週2,591件 | 「試してほしい人」「知りたいこと4つ」「データは端末から出ない」を具体的に書き、リンク（賛成26・コメント9） |

判断：**リンクを載せて投稿してよい場所**。ただし Reddit 全体の決まり（同じ投稿をあちこちに貼らない、など）は守る。
注意：
- 投稿が多いので、すぐ流れる。反応がよいのは、**具体的で、見てすぐわかるもの**（画面・動画）と、**答えやすい質問**。
- r/alphaandbetausers は「試せるもの」がある前提の場所。今はまだ試せないので、「作る前に聞きたい」と正直に書く。反応は小さいかもしれない。

---

## A. 住宅・ローンの掲示板（質問の形）

**Title:** How do you run your mortgage numbers now — calculator app, lender site, spreadsheet, or ChatGPT?

**Body:**

> I'm building a mortgage and loan calculator for Android, and before I go further I'd like to hear from people with a real loan in front of them.
>
> A few questions:
>
> 1. What do you actually use to work out your payment, extra payments, or payoff date? An app, your lender's site, a spreadsheet, an AI chatbot?
> 2. What annoys you about it, or what's missing?
> 3. If you've asked ChatGPT (or similar) about your loan, did it do the job? What would make you open an app instead?
>
> For context: the one I'm making has no ads (not now, not later), no account, and keeps your loans on your phone. The calculator apps I tried had ads on every screen, and getting rid of them meant buying a separate paid app, or wasn't possible at all. That felt wrong for something you use to make a big money decision.
>
> *(Only if the rules allow links:)* If you'd rather answer privately, there's a short form here: [link with ?from=]
>
> Thanks. I'll read every reply.

## B. r/SideProject（作り手向け、ページの感想をもらう）

**Title:** I'm building an ad-free mortgage calculator for Android. Would this page make you want it?

**Body:**

> The loan calculator apps I tried had ads on every screen, and getting rid of them meant buying a separate paid app, or wasn't possible at all. So I'm building one with no ads, no account and no tracking, that opens straight to the answer and shows a dated payment schedule with extra payments.
>
> It isn't built yet. I made a one-page site with a short survey to see if anyone wants it: [link with ?from=reddit-sideproject]
>
> Two things I'd love feedback on:
>
> 1. Does the page explain it clearly in a few seconds?
> 2. Honest question: people now ask ChatGPT for loan math. Would you still use an app for this? Why or why not?
>
> The page itself has no analytics or cookies. The form only records which link you came from.

## C. r/alphaandbetausers（試したい人を探す）

**Title:** [Android] Ad-free mortgage & loan calculator — looking for early testers

**Body:**

> LoanChart is a mortgage and loan calculator for Android: monthly payment in three inputs, a payment schedule with real dates, extra payments from any month, and side-by-side comparison of offers. No ads, no account, data stays on your phone.
>
> It's in development. If you have a mortgage or are about to get one, I'd like to know what you need before I finish it. Short form (email optional, only used to tell you when it's out): [link with ?from=reddit-alphabeta]
