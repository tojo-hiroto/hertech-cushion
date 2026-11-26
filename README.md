# HerTech IGタイアップ クッションページ（デモ）

IGストーリーのタイアップリンク → 興味分野を選択 → 年代を選択 → 該当LPへ遷移するクッションページ。

## 遷移先

| 分野 | 20代 | 30代 | 40代以上 |
|---|---|---|---|
| Webデザイン | /20wdig-pm | /30wdig-pm | /40wdig-pm |
| 動画編集 | /20veig-pm | /30veig-pm | /40veyt-pm |

（すべて https://lp.her-tech.jp 配下。`index.html` 内の `LP` オブジェクトで管理）

## パラメータ引き継ぎ

このページのURLに付けた `?` 以降のパラメータは、遷移先LPにそのまま付与されます。

例：`https://<user>.github.io/hertech-cushion/?utm_source=ig&utm_campaign=xxx`
→ 動画編集 × 40代を選択 → `https://lp.her-tech.jp/40veyt-pm?utm_source=ig&utm_campaign=xxx`

- 分野選択はURLのハッシュ（`#wd` / `#ve`）で管理しているため、ステップ間でクエリは消えません
- ブラウザの「戻る」でステップ1に戻れます
- 選択時に `dataLayer` へ `cushion_select` イベント（field / age / dest）をpushしています（GTM導入時用）
