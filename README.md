# Live-Labo ライバー獲得LP プロトタイプ

## ファイル構成
- `index.html` - 単一ファイル完結のLP本体（インラインCSS/JS、外部依存はGoogle Fontsのみ）
- `README.md` - この説明書

## プレビュー方法
ローカルでブラウザで開けば即見られます:
```
open /Users/yusukeyokouchi/Desktop/live-labo-lp/index.html
```
もしくはFinderから`index.html`をダブルクリック。

## WordPressに「キャンペーンページ」として公開する手順
**既存サイトは一切触りません。** 新規固定ページとして追加するだけです。

1. WP管理画面 → `固定ページ` → `新規追加`
2. タイトル: 「ライバーデビュー応援キャンペーン」（URLスラッグは `campaign` 推奨）
3. ブロックエディタで `+` → `カスタムHTML` ブロックを追加
4. `index.html` の `<body>` 〜 `</body>` の中身を全選択コピー → カスタムHTMLブロックに貼り付け
5. ページ右側 `公開状態` → `非公開` または `パスワード保護` に設定 → `下書き保存`
6. `プレビュー` ボタンで確認 → OKなら `公開`
7. 公開URL: `https://live-labo.jp/campaign/`

### テーマヘッダー/フッターを消したい場合
`カスタムHTML` 直貼りだとテーマの`<header>`/`<footer>`が上下に出てしまいます。完全にLP化したいなら:
- 方法A: テンプレート `templates/page-campaign.php` を作って空白テンプレートにする
- 方法B: プラグイン `Page Builder Framework` 等で「空白テンプレート」設定
- 方法C: そのままテーマ装飾上に重ねる（既存サイト感とのつながりは出る）

## 編集ポイント（Yokouchiさんが触る箇所）
| 何を | どこ |
|---|---|
| LINE導線URL | `href="#contact"` を全部 `href="https://lin.ee/xxxxx"` に置換 |
| キャンペーン内容（5大特典） | `<ul class="campaign-list">` 内 |
| 数字訴求（500+、100%等） | `<section class="stats">` 内 |
| 所属ライバー写真・名前 | `<section class="livers">` 内 |
| FAQ追加・修正 | `<section class="faq">` 内 `<details>` |
| ヒーローキャッチコピー | `<h1>あなたの"好き"を…` |

## 設計判断メモ
- **配色**: Live-Labo既存の赤(#d4002a相当)+黒+白を継承、補色にゴールド(#c8a456)で大手感
- **フォント**: Noto Sans JP + Inter（数字用）。既存サイトと統一
- **画像**: 既存`live-labo.jp/wp-content/uploads/`配下のライバー写真URLを直接参照（追加アップロード不要）
- **依存**: 外部ライブラリゼロ。CSSアニメーションとvanilla JSのみ
- **モバイル**: 固定下部CTA、ヘッダーCTAは非表示に切替
- **SEO**: 一旦 `noindex,nofollow` 設定済み。公開時に外す

## ベンチマーク
- ワンカラット（onecarat.com）: 数字訴求の強さ、フローティング緑LINE CTA、期間限定boxを参考
- 321（321.inc/lp）: 余白の使い方、大文字キャッチ、写真の力強さを参考

## 次のステップ案
1. ローカルで確認 → 文言・写真の差し替え指示
2. LINE実URL差し込み
3. WordPress固定ページ作成 → カスタムHTML貼り付け → 下書きプレビュー
4. ヒーロー写真をプロカメラマン撮影に差し替え（オプション）
5. Aパターン/Bパターン作ってABテスト（オプション）
