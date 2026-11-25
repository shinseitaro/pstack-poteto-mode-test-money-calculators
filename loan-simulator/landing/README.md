# LoanChart の紹介ページ

アプリを作る前に、欲しい人がいるか・何が欲しいかを集めるための1ページ（[議論 12](../../docs/discussions/loan-simulator/20261108/12-landing-page-plan.md)）。

- `index.html`：紹介ページ（英語）。アンケートは Netlify Forms（フォーム名 `needs`）。
- `thanks.html`：送ったあとのページ。
- `ja/`：日本版（パイロット）の紹介ページとアンケート（フォーム名 `needs-ja`、2026-11-09〜）。
- `img/`：Stitch で作った画面（`../design/stitch/` を幅600に縮めたもの）。

約束：計測のタグ、Cookie、外部のフォントや script は入れない（「集めない」アプリの紹介ページなので）。

## 手元で見る

```bash
cd loan-simulator/landing && python3 -m http.server 8765
# http://localhost:8765/ を開く（フォームの送信は Netlify に置いたときだけ動く）
```

## 公開している場所

- https://loanchart.netlify.app 、ウェブ版は https://loanchart.netlify.app/app/ （Netlify のプロジェクト `loanchart`、ID `dc8f77c9-48b1-4e7b-93b9-73884a9d726c`、2026-11-08 公開）
- 回答は Netlify の「Forms」→ `needs` で見る（Claude からは Netlify の MCP で読める）。
- フォームの検出は、プロジェクトの設定で有効にしてある（新しいプロジェクトでは最初は無効）。

## 更新するとき

この README は公開しない。`index.html`・`thanks.html`・`img/` だけを別のフォルダに写して公開する。

`/app/` には、ウェブ版のアプリ（`../../../../loanchart` のビルド）を一緒に置く（2026-11-09 から）。
ウェブ版は、Google のサーバーから部品やフォントを読みに行かないように、`--no-web-resources-cdn` を付けてビルドする（フォントはアプリに入れてある）。

```bash
# 1. ウェブ版をビルド（loanchart で）
cd ../../../../loanchart
clj -M:cljd clean && clj -M:cljd compile
flutter build web --no-web-resources-cdn --base-href /app/
cd -

# 1b. 日本版（パイロット）もビルド。ページの題を日本語にする手順は loanchart の README
flutter build web --no-web-resources-cdn --base-href /ja/app/ --dart-define=MARKET=jp -o build/web-jp

# 2. 紹介ページとウェブ版をまとめて公開（日本版は /ja/ と /ja/app/）
P=$(mktemp -d) && cp -r index.html thanks.html img ja "$P"/ && cp -r ../../../../loanchart/build/web "$P"/app && cp -r ../../../../loanchart/build/web-jp "$P"/ja/app
npx -y netlify-cli deploy --prod --dir "$P" --site dc8f77c9-48b1-4e7b-93b9-73884a9d726c --no-build
```
