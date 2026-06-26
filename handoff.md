# ブライエッジ様 ハイクラス向けLPモック — 引き継ぎメモ

最終更新：2026-06-26

---

## 1. プロジェクト概要

| 項目 | 内容 |
|------|------|
| 案件名 | ブライエッジ様 ハイクラス向けLPモック |
| 目的 | 関係者確認用のテストLP（クライアント提案用モック） |
| 対象層 | 年収1,000万円以上のハイクラス転職候補者 |
| 公開方法 | GitHub Pages（main ブランチ / root） |
| 現状 | ハイクラス向けLP作成・公開済み |
| 未着手 | ミドル向けLP（ハイクラスLPのコンポーネントを流用して制作予定） |

---

## 2. GitHub情報

| 項目 | URL |
|------|-----|
| リポジトリ | https://github.com/ytadokoro59/briedge-lp-mock |
| GitHub Pages | **https://ytadokoro59.github.io/briedge-lp-mock/** |

> 関係者にはGitHub PagesのURLを共有するだけで確認可能。

---

## 3. ファイル構成

```
briedge-lp-mock/
├── index.html              ← GitHub Pagesトップページ（highclass-lp.html と同内容）
├── highclass-lp.html       ← ハイクラス向けLP本体（15セクション）
├── highclass-lp.css        ← LPスタイル。FV背景・カラー変数・レスポンシブを管理
├── highclass-lp.js         ← FAQアコーディオン、スクロールリビール、ヘッダースクロール
├── README.md               ← 案件概要（外部向け）
├── handoff.md              ← このファイル（引き継ぎメモ）
├── .gitignore
└── assets/
    ├── top_entrance-uai-1280x1280.jpg  ← FV背景写真（仮・公式サイトより）
    ├── hallway_1-1.jpg                 ← VALUEセクション写真（仮・公式サイトより）
    ├── matsushimasan_2-1.jpg           ← ADVISORセクション写真（仮・公式サイトより）
    └── logo_horizontal.svg             ← BRIEDGEロゴ（公式サイトより）
```

---

## 4. 実装済み内容

- ハイクラス向けLPモックを静的HTML/CSS/JSで作成済み（Reactなし、ブラウザで直接開ける構成）
- GitHub Pagesで公開済み
- **FVは背景写真重ね型**：左→右で徐々に写真が透けるグラデーションオーバーレイ
- FV背景に `top_entrance-uai-1280x1280.jpg`（BRIEDGE受付エントランス）を仮使用
- VALUEセクションに `hallway_1-1.jpg` を仮使用
- ADVISORセクションに `matsushimasan_2-1.jpg` と `hallway_1-1.jpg` を仮使用
- ロゴは `logo_horizontal.svg` を使用（読み込み失敗時はテキストフォールバックあり）
- 画像はすべて `assets/` 配下から相対パスで参照（外部URL参照なし）
- GitHub Pages対応のため、CSS/JSリンクは `./` プレフィックスに統一済み
- PC（2カラム）・スマホ（1カラム）のレスポンシブ対応済み
- スマホ向けモバイル固定CTAあり

### セクション構成（全13セクション）

| # | ID | 内容 |
|---|-----|------|
| 01 | — | Header（固定） |
| 02 | #top | First View（背景写真重ね型） |
| 03 | #issues | Problem（悩みカード5枚） |
| 04 | #value | Value（価値訴求・写真） |
| 05 | #difference | Difference（比較表） |
| 06 | #criteria | Career Criteria（4カード） |
| 07 | #positions | Positions（4領域カード） |
| 08 | #cases | Cases（事例4件） |
| 09 | #reasons | Reasons（5カード） |
| 10 | #facts | Numbers（数値プレースホルダー） |
| 11 | #consultants | Advisor（コンサルタント紹介） |
| 12 | #contact | CTA（中間） |
| 13 | #faq | FAQ（アコーディオン5問） |
| 14 | — | Final CTA |
| 15 | — | Footer |

---

## 5. 確認済み事項

- GitHub Pagesの全ファイルが **HTTP 200 OK** で配信されていることを確認済み
- PC表示（1280px）・スマホ表示（375px）ともにJS評価でページ読み込みを確認済み
- セクション数：**13セクション** 正常読み込み
- 画像4点が `complete: true / naturalWidth > 0` で正常ロード済み
  - `logo_horizontal.svg`（300px幅）
  - `hallway_1-1.jpg`（900px幅）
  - `matsushimasan_2-1.jpg`（960px幅）
  - `top_entrance-uai-1280x1280.jpg`（CSS背景・HTTP 200確認）
- FV背景グラデーション：PC用（横グラデーション）・スマホ用（縦グラデーション）で切り替え済み

---

## 6. 直近のコミット

```
git log --oneline -5

c8a4c5b Fix: add ./ prefix to CSS/JS paths for GitHub Pages compatibility
d49943d Add Briedge highclass LP mock (initial)
```

---

## 7. 画像差し替え方法

正式画像が決まったら `assets/` に追加し、`highclass-lp.css` 冒頭の1行を差し替えるだけ。

```css
/* FV背景画像：正式選定後にクライアント指定画像に差し替え */
--hero-image: url("./assets/【新しいファイル名】.jpg");
```

現状の画像はすべて仮置き。クライアント確認後に正式選定予定。

仮置き画像一覧と差し替え箇所：

| 箇所 | 現在の仮画像 | 差し替え方法 |
|------|------------|------------|
| FV背景 | `top_entrance-uai-1280x1280.jpg` | `highclass-lp.css` の `--hero-image` を変更 |
| VALUEセクション | `hallway_1-1.jpg` | `highclass-lp.html` の `<img src>` を変更 |
| ADVISORカード写真 | `matsushimasan_2-1.jpg` | `highclass-lp.html` の `<img src>` を変更 |
| ADVISORセクション右側 | `hallway_1-1.jpg` | `highclass-lp.html` の `<img src>` を変更 |
| ヘッダーロゴ | `logo_horizontal.svg` | `highclass-lp.html` の `<img src>` を変更 |

---

## 8. 今後の作業候補

### A. ハイクラスLPの微調整

- [ ] FVの明るさ・文字色・写真オーバーレイの最終調整
- [ ] スマホFVの可読性確認（実機テスト）
- [ ] CTAボタンの目立ち方確認
- [ ] 正式写真への差し替え（クライアント選定後）
- [ ] Numbersセクションの仮数値を実数値に差し替え（`<!-- DATA: -->` コメント箇所）
- [ ] 仮文言・キャッチコピーの精査・修正
- [ ] クライアント確認フィードバックの反映

### B. ミドル向けLP制作

ハイクラスLPから流用できるコンポーネント：

- ヘッダー（固定・スクロール対応）
- CTAボタン群
- FAQアコーディオン
- スクロールリビール（`.reveal` クラス）
- 比較表（`.diff-table`）
- カードグリッド（`.problem-cards`、`.reason-grid` 等）
- CSS変数設計（`:root` の色・フォント定義）
- GitHub Pages公開構成（`assets/` 配置、相対パス）

ミドル向けの訴求変更点：

- トーンを少し明るく（現状の上質・秘匿性→市場価値・可能性）
- 市場価値の整理
- 経験の活かし方
- IT・SaaS・成長企業でのキャリア可能性
- 今すぐ転職しない相談も可能
- 営業限定ではなく、ビジネス職・専門職・マネジメント候補層向け

---

## 9. 次回再開時の手順

```bash
cd C:\Users\ytado\OneDrive\デスクトップ\briedge-lp-mock

git status
git pull origin main
cat handoff.md
```

その後、ローカルで確認したい場合：

```bash
# npx serve でローカルサーバー起動
npx serve . -l 5503
```

確認URL：
- ローカル：`http://localhost:5503/`
- GitHub Pages：`https://ytadokoro59.github.io/briedge-lp-mock/`

---

## 10. 備考

- `index.html` と `highclass-lp.html` は現在同一内容。今後ミドルLPを追加した場合、`index.html` を案件一覧ページに変更することも検討可能。
- Numbersセクション（`#facts`）の数値は `<!-- DATA: 〜 -->` コメントで明示してあるため、後で差し替えやすい。
- CTAリンク先は現在 `register.html`（未作成）のダミー。フォームページ制作時に差し替え。
