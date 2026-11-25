# Google Stitch 用のプロンプト

[機能と画面](../features-and-screens.md) の画面を、Google Stitch で形にするための英語のプロンプト。

使い方：

1. Stitch で新しいプロジェクトを作り、モバイル（Android）を選ぶ。
2. まず「0. 共通」を貼り、続けて ① から順に1つずつ貼る（1回に1画面）。
3. 気に入った案ができたら、HTML を書き出して `loan-simulator/design/stitch/` に置く。スクリーンショットもあるとよい。

注意：

- **ブランド（名前・色・トーン）はまだ決めていない**。ここで作る見た目は「画面の並びと情報の量」を確かめるための仮のもの。
  アプリの名前は画面に出さない。
- 数字はすべて計算して確かめた値。Stitch が数字を変えたら、元に戻すよう指示する。
  - $300,000・3.5%・30年：月 $1,347.13、利息の合計 $184,968、1回目は利息 $875.00・元金 $472.13
  - 1回目が 2026年12月なら、最後は 2056年11月
  - 毎月 $200 の追加返済を1回目から：2050年10月に終わる（73か月 = 6年1か月早い）、利息が $42,090 減る（合計 $142,879）

## 0. 共通（最初に貼る）

```
I'm designing an Android app (Material Design 3) for US home buyers and people repaying a mortgage.
It is a loan calculator with no ads, no account, and no tracking. The core value is "trustworthy":
it never interrupts your money decisions, it opens straight to the calculator, and it shows details only when you ask.

Style:
- Calm, quiet, and trustworthy. Light theme. Lots of white space.
- One restrained accent color (deep teal or navy). No gradients, no illustrations, no stock photos.
- Large, clear numbers with tabular (monospaced) digits. Money is always right-aligned.
- No ad banners, no promotional cards, no "rate offers", no login.
- Do not show an app name or logo anywhere.
- Bottom navigation with only two tabs: "Calculate" and "My loans". A settings icon in the top-right.
Keep all numbers exactly as I give them.
```

## ① 計算（開いたときの画面）

```
Screen 1: "Calculate" tab, the screen the app opens to.

Top: three inputs only, in a compact card:
- Loan amount: $300,000
- Interest rate: 3.5 %
- Term: 30 years

Below, the result, very large and clear:
- "$1,347.13 / month"
- "Total interest $184,968"
- A small line explaining the first payment: "1st payment: $875.00 interest + $472.13 principal",
  shown as a thin horizontal bar split into two parts (interest vs principal).

Then three collapsed rows that expand in place (show them collapsed, with a chevron):
- "Home costs" (subtitle: "Taxes, insurance, PMI, HOA")
- "Extra payments" (subtitle: "Pay off sooner")
- "Start date" (subtitle: "Dec 2026")

At the bottom, two buttons: "Schedule" (outlined) and "Save" (filled).
The screen must feel as simple as a three-input calculator when nothing is expanded.
```

### ①' 「Home costs」を開いたとき

```
Same screen, with "Home costs" expanded.
Inside the expanded section:
- Home price $375,000
- Down payment $75,000 (20%)  [toggle between $ and %]
- Property tax $4,500 / year
- Home insurance $1,800 / year
- PMI $0 (shown greyed, with note "Not needed at 20% down")
- HOA $0 / month

The big result at the top changes to "$1,872.13 / month" with a breakdown:
Principal & interest $1,347.13, Property tax $375.00, Insurance $150.00.
Show the breakdown as a simple stacked bar with a legend.
```

## ② 返済スケジュール

```
Screen 2: "Schedule", opened from the "Schedule" button.
Top app bar with back arrow and title "Schedule". Subtitle: "$300,000 · 3.5% · 30 years".

A segmented control: "Monthly" | "Yearly" (Monthly selected).

A line chart of the remaining balance from Dec 2026 to Nov 2056.
A second, dashed line shows the balance with extra payments, reaching zero in Oct 2050.
Legend: "Without extra" / "With $200/month extra".

Below, a table with columns: Date, Payment, Principal, Interest, Balance.
First rows:
- Dec 2026  $1,547.13  $672.13  $875.00  $299,327.87
- Jan 2027  $1,547.13  $674.09  $873.04  $298,653.78
- Feb 2027  $1,547.13  $676.06  $871.07  $297,977.72
(Payment includes the $200 extra.)
Highlight one row with a small "Today" chip to show where the borrower is now.
```

## ③ 追加返済（下から出るシート）

```
Screen 3: a modal bottom sheet titled "Extra payments", over the Calculate screen.

A list of rules the user added, each as a row:
- "Every month · $200 · from Dec 2026"
A button "+ Add extra payment" that offers: Every month / Every year / One time, each with a start month.

A switch: "Pay every two weeks (26 payments a year)" — off.

At the bottom, the effect, clearly:
- "Paid off Oct 2050"
- "6 years 1 month sooner"
- "You save $42,090 in interest"
And a "Done" button.
```

## ④ 保存したローン

```
Screen 4: "My loans" tab.
A list of saved loan cards. Each card shows: name, balance today, monthly payment, payoff date, and a thin progress bar of how much is paid.

Card 1: "Our house" — Balance today $280,649 · $1,349.13 / month · Paid off May 2051 · 294 payments left.
Card 2: "Bank A offer" — $300,000 · 3.5% · 30 years · $1,347.13 / month.
Card 3: "Bank B offer" — $300,000 · 3.25% · 30 years · $1,305.62 / month.

Cards can be selected with a checkbox for comparison. When two or more are selected,
a bottom bar appears: "Compare (2)".
No account, no cloud icon. A small footnote: "Saved on this device only."
```

## ⑤ 比べる

```
Screen 5: "Compare", opened from My loans.
Top app bar with back arrow and title "Compare".

A side-by-side comparison of three loans, each in a column:
- "Bank A · 30 yr" — 3.5%, $1,347.13 / month, total interest $184,968, paid off Nov 2056
- "Bank B · 30 yr" — 3.25%, $1,305.62 / month, total interest $170,022, paid off Nov 2056
- "15 yr" — 3.0%, $2,071.74 / month, total interest $72,914, paid off Nov 2041

Rows: Rate, Monthly payment, Total interest, Paid off, Total paid.
Mark the lowest monthly payment and the lowest total interest with a subtle label ("Lowest").
Under each column, show the difference from the best option, e.g. "+$14,946 interest".
No recommendations, no "apply now" buttons.
```

## 設定

```
Screen 6: "Settings", opened from the top-right icon.
Sections:
- Display: Currency (USD), Number format.
- Your data: Export loans, Import loans.
- Privacy: a row "What this app doesn't collect" that opens a simple page listing:
  No ads. No advertising ID. No analytics. No account. Your loans stay on this device.
- About: Version 1.0.
Keep it plain and short.
```
