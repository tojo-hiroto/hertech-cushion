# HerTech クッションページ（IGタイアップ用）

IGストーリーのタイアップリンクから流入したユーザーに「興味分野」と「年代」を選んでもらい、該当する無料イベントLPへ遷移させるページ。

## 構成

公開URL：https://event.her-tech.jp/ （GitHub Pages ＋ カスタムドメイン）

- `igtieup/index.html` … IGタイアップ用クッションページ本体（HTML / CSS / JS を1ファイルに集約）→ https://event.her-tech.jp/igtieup/
- `igtieup/assets/` … アイコン・イラスト画像
- `index.html` … ルートにアクセスされた場合は https://her-tech.jp/ へ転送
- `CNAME` … カスタムドメイン設定（event.her-tech.jp）。削除しないこと

ビルド不要の静的ファイルのみ。施策ごとにフォルダを切って追加できる。

## 遷移先LP

| 分野 | 20代 | 30代 | 40代以上 |
|---|---|---|---|
| Webデザイン | lp.her-tech.jp/20wdig-pm | lp.her-tech.jp/30wdig-pm | lp.her-tech.jp/40wdig-pm |
| 動画編集 | lp.her-tech.jp/20veig-pm | lp.her-tech.jp/30veig-pm | lp.her-tech.jp/40veyt-pm |

変更する場合は `igtieup/index.html` 内の `var LP = { ... }` を編集する。

## パラメータの引き継ぎ

このページのURLに付けた `?` 以降のパラメータは、遷移先LPにそのまま付与される。

例：`https://event.her-tech.jp/igtieup/?utm_source=ig&utm_campaign=xxx`
→ 動画編集 × 30代を選択 → `https://lp.her-tech.jp/30veig-pm?utm_source=ig&utm_campaign=xxx`

- 同名のキーがLP側URLにある場合は、このページ側の値を優先
- 分野の選択はURLのハッシュ（`#wd` / `#ve`）で保持しているため、ブラウザの「戻る」で1問目に戻れる
- 選択時に `dataLayer` へ `cushion_select` イベント（field / age / dest）をpushしている（GTM導入時の計測用）

## 更新方法

`main` ブランチにpushすると、1〜2分でGitHub Pagesに反映される。
