# SEO修正メモ（2026-06-17）

## 修正内容

- `sitemap.xml` を拡張子なしの正規URLに統一しました。
- `fees.html` はサイトマップから除外し、`/services` への統合ページとして `noindex` を付けました。
- 各HTMLの canonical、OG URL、Breadcrumb JSON-LD、内部リンクを拡張子なしURLへ統一しました。
- `404.html` が画像ファイルになっていたため、通常の404 HTMLページに差し替えました。
- Cloudflare の `/cdn-cgi/l/email-protection` がSearch Consoleに出る原因を減らすため、ソース内の直接メールアドレスと `mailto:` をお問い合わせフォーム導線に置き換えました。
- Cloudflare Pages向けに `_redirects` を追加し、`.html` URLから正規URLへの301リダイレクトを明示しました。

## Search Consoleでの確認手順

1. 修正版をデプロイする。
2. `https://yuki-tax.jp/sitemap.xml` をSearch Consoleで再送信する。
3. URL検査で次を確認する。
   - `https://yuki-tax.jp/`
   - `https://yuki-tax.jp/services`
   - `https://yuki-tax.jp/faq`
   - `https://yuki-tax.jp/fees.html`
4. `fees.html` はインデックス対象ではなく、`/services` に統合されれば問題ありません。
5. `/cdn-cgi/l/email-protection` はサイト側からリンクが消えれば、時間経過で404一覧から薄まります。
