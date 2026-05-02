# 結城宏太税理士事務所サイト 完成版

## 内容

- `index.html`：トップページ
- `services.html`：業務内容一覧
- `fees.html`：料金一覧
- 個別ページ：`tax-advisory.html`, `inheritance.html`, `startup.html`, `accounting-dx.html`, `tax-investigation.html`
- `privacy.html`, `tokutei.html`, `404.html`
- `assets/css/style.css`, `assets/js/main.js`
- `robots.txt`, `sitemap.xml`, `site.webmanifest`

## 反映した主な方針

- 最新GA4 ID `G-8JLDZXYHXQ` を全ページに設置。
- プロフィール写真エリアは設けず、当面はイニシャル入りのプロフィールカードに統一。
- 業務内容・料金はトップページから独立させ、個別ページと料金一覧ページへ分岐。
- Claude統合版のアクセシビリティ、スライド一時停止、スティッキーCTA、ページトップ、対応エリアタグ等は採用。
- 過度な保証表現（完全、防衛、必ず削減等）は不使用。
- 社会保険・登記・補助金については、税理士業務外の手続代行と読まれないよう、試算・整理・専門家連携の表現に調整。

## 公開前に確認すること

1. 既存画像 `images/lobby.jpg`, `images/tower.jpg`, `images/exterior1.jpg` を同じパスに配置してください。
2. 料金表示について、税込・税別・実費別の事務所方針を最終確認してください。現状は「正式見積で明示」としています。
3. Formspree のフォームID `maqlllje` が現在の受信先で問題ないか確認してください。
4. Google Search Console に `sitemap.xml` を送信してください。
5. Googleビジネスプロフィールの名称・住所・電話番号をサイトと一致させてください。

## Wixで使う場合

Wix上で完全に差し替えるのではなく、ページ本文・見出し・個別ページ構成をビルダー側で再現し、GA4・構造化データ・OGP・canonical等はWixのSEO設定／カスタムコードに分けて反映するのが現実的です。静的ホスティングに移行する場合は、このフォルダをそのまま公開用のベースにできます。
