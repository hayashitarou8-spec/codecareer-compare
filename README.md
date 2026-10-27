# CodeCareer Compare（コードキャリア比較）

IT・特化型転職エージェントを、公式条件の同条件表で比較する静的サイト。

- ブランド仮: **CodeCareer Compare**
- 生活トラブル（`kurashi-trouble-compare`）／ClinicBasics と **命名・見た目・A8メディアを混ぜない**
- アフィリエイトリンクはプレースホルダ（`{{AFFILIATE_LEVTECH}}` 等）。A8/afb承認後に差し替え
- 禁止: AIスクール・稼ぎ方商材・退職代行

調査メモ: `/workspace/it-career-affi/`

## 構成

```
codecareer-compare/
  index.html
  disclosure.html      # アフィリエイト・PR開示
  privacy.html
  legal.html           # 特商法・運営者（プレースホルダ）
  styles.css           # インディゴ系（kurashi緑と分離）
  articles/
    it-engineer-agent-comparison-2026.html   # 経験者ピラー
  README.md
```

## ローカル確認

依存なし（素の HTML/CSS）。リポジトリ直下が publish ディレクトリです。

```bash
cd /workspace/codecareer-compare
python3 -m http.server 8080
# ブラウザで http://127.0.0.1:8080/
```

または:

```bash
npx --yes serve -l 8080 .
```

## Render 静的サイト手順

kurashi と同様のパターン（`buildCommand: true` / `publishPath: ./`）。

1. GitHub に本ディレクトリを **別リポジトリ** で push（例: `codecareer-compare`）。`kurashi-trouble-compare` と混ぜない。
2. [Render Dashboard → New Static Site](https://dashboard.render.com/static/new)
3. 設定例:
   - **Name**: `codecareer-compare`（`kurashi-*` / `clinic*` にしない）
   - **Branch**: `main`（または `master`）
   - **Build Command**: `true`（ビルド不要。空欄不可のUIなら `true`）
   - **Publish Directory**: `./`（リポジトリルート）
4. デプロイ後の URL 例: `https://codecareer-compare.onrender.com`
5. A8 には **新メディア** としてこの URL を申請（副サイト002・暮らしトラブルと比較しない）

### MCP / CLI で作る場合の前提

- Render の `create_static_site` は **Git リポジトリ URL が必須**
- GitHub 未接続・未 push のときはローカルまでで止め、上記手順で後から接続する

## 公開前チェック

- [ ] `legal.html` の `{{OPERATOR_NAME}}` / 住所 / メール等を実情報に置換
- [ ] ピラー内 `{{AFFILIATE_*}}` を ASP 管理画面のリンクに置換
- [ ] 開示・プライバシー・特商法がフッターから辿れること
- [ ] 求人数・キャンペーン表記を公式で再確認して日付更新

## ピラー結論3社（経験者）

1. レバテックキャリア — https://career.levtech.jp/
2. Geekly — https://www.geekly.co.jp/
3. マイナビ転職 IT AGENT — https://mynavi-agent.jp/it/

更新日: 2026-10-27（Asia/Tokyo）
