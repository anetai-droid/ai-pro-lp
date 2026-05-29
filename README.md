# Public Page

https://anetai-droid.github.io/ai-pro-lp/

# ai-pro-lp — AIプロ用コンテンツ 販売LP / 体験版 / 法務ページ（GitHub Pages）

介護・障害福祉の事業所向け「AIプロ用コンテンツ」の**販売LP・無料体験・法務ページ**一式。
GitHub Pages で公開する**プレーンな静的サイト**（ビルド不要・HTMLを開くだけ）。

## 本番ポータルとは別物

- 購入者ポータル（`ai-pro-portal` / FastAPI / Cloud Run）とは**完全に分離**したリポジトリ。
- ここには**有料教材・GCSの鍵・顧客データを一切置かない**。誰でも見られる公開マーケ用のみ。
- 本番を壊さず、ここだけ自由に更新できる。

## 構成

```
ai-pro-lp/
├── index.html       … 販売LP（買う前に見るページ）
├── trial.html       … 無料体験（個別支援計画たたき台を架空事例で。本物の25レシピは出さない）
├── privacy.html     … プライバシーポリシー（仮文面）
├── terms.html       … 利用規約（仮文面）
├── tokushoho.html   … 特定商取引法に基づく表記（仮文面）
├── styles.css       … 全ページ共通デザイン（信頼・安心／白基調＋落ち着いた青）
├── .nojekyll        … GitHub Pages の Jekyll 処理を無効化
└── README.md        … このファイル
```

申し込みフォームは**置かない**（LP内に個人情報を保存しない）。ボタンから**オートビズのフォームURL**へ遷移させる。

## 文字コードについて（重要）

全ファイルは **UTF-8（BOMなし）** で、`<meta charset="UTF-8">` 済み。**ブラウザでは正常表示**される。
エディタ/ターミナルが Shift-JIS(cp932) で開くと文字化けして見えるだけなので、**編集は UTF-8 対応エディタ（VS Code 等）**で行い、確認は必ずブラウザで。

## 公開前に差し替える箇所（`[　]`＝オレンジ表示で目印）

- [ ] 事務時間・before/afterの分数（`[　]` / `[30]` / `[5]`）
- [ ] **デモ動画**（任意）：YouTube/Vimeo にダミー事例で撮影 → `index.html` の iframe に
- [ ] 事業所版の**価格**（`[　] 円`）
- [ ] **オートビズの申し込みフォームURL**（index・trial のボタン）
- [ ] サービス名／事業者名（各フッター・OGP画像）
- [ ] **特商法**：事業者名・責任者・住所・電話・メール・支払/引渡/返金条件
- [ ] **プライバシー／利用規約**：事業者名・連絡先・外部サービス名・管轄裁判所
- [ ] 法務3ページは可能なら**専門家の確認**を受けてから公開

## ローカルで確認

`index.html` をブラウザにドラッグ。サーバとして見るなら:

```powershell
python -m http.server 8000   # → http://localhost:8000
```

## GitHub Pages で公開

```powershell
git init
git add .
git commit -m "init: AIプロ用コンテンツ 販売LP / 体験版 / 法務ページ"
gh repo create ai-pro-lp --public --source . --remote origin --push
```

公開設定: GitHub の **Settings → Pages → Source = Deploy from a branch → main / (root)**。
数分後 `https://<ユーザー名>.github.io/ai-pro-lp/` で公開。
