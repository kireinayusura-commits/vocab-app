# VOCAB — iPhoneへの導入手順

このアプリは PWA（Progressive Web App）です。サーバー費用ゼロで、
iPhoneのホーム画面から普通のアプリのように起動できます。

## 必要なもの
- GitHubアカウント（無料）
- iPhoneのSafari

## 手順1：GitHub Pagesで公開する（初回のみ・約5分）

1. https://github.com にログインし、右上の「+」→「New repository」
2. Repository name に `vocab-app` と入力し、Public のまま「Create repository」
3. 「uploading an existing file」リンクをタップ/クリック
4. このフォルダの中身（index.html, manifest.webmanifest, sw.js, icons フォルダ）を
   すべてドラッグ&ドロップして「Commit changes」
5. リポジトリの「Settings」→ 左メニュー「Pages」
6. Branch を `main`、フォルダを `/ (root)` にして「Save」
7. 1〜2分待つと、ページ上部に公開URLが表示されます
   例: `https://あなたのID.github.io/vocab-app/`

## 手順2：iPhoneのホーム画面に追加する

1. iPhoneの **Safari** で上のURLを開く（Chromeでは不可）
2. 画面下の共有ボタン（四角に↑）をタップ
3. 「**ホーム画面に追加**」をタップ →「追加」

これで完了です。ホーム画面のVOCABアイコンから、
全画面のアプリとして起動します。オフラインでも動作します。

## データについて

- 学習記録（習熟度・履歴）は **iPhoneの端末内** に保存されます
- 問題データの読み込みは、アプリの「設定」→「問題データを読み込む」から
  CSV / Excel(xlsx) ファイルを選択します
- 編集したデータは「問題データを書き出す」でCSVとして保存できます

## 注意

- Safariの「履歴とWebサイトデータを消去」を実行すると学習記録も消えます。
  大事な節目では「問題データを書き出す」でバックアップしてください
- アプリを更新したいときは、GitHubのファイルを新しいindex.htmlに
  差し替えれば、次回起動時に反映されます
