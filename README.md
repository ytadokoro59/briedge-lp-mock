# ブライエッジ様 ハイクラス向けLP モック

## 概要

| 項目 | 内容 |
|------|------|
| 案件名 | ブライエッジ株式会社 ハイクラス向けLP |
| 用途 | 関係者確認用テストページ（クライアント提案モック） |
| 公開方法 | GitHub Pages |
| 対象 | 年収1,000万円以上のハイクラス転職候補者 |

## ファイル構成

```
briedge-lp-mock/
├── index.html          # GitHub Pages トップページ（highclass-lp.htmlと同内容）
├── highclass-lp.html   # ハイクラスLP本体
├── highclass-lp.css    # スタイルシート
├── highclass-lp.js     # インタラクション（FAQ・スクロールリビール等）
└── assets/
    ├── top_entrance-uai-1280x1280.jpg  # FV背景写真（仮）
    ├── hallway_1-1.jpg                 # VALUEセクション写真（仮）
    ├── matsushimasan_2-1.jpg           # アドバイザーセクション写真（仮）
    └── logo_horizontal.svg             # BRIEDGEロゴ（仮）
```

## 注意事項

> **このページはモック段階の確認用です。**

- 画像・写真：ブライエッジ公式サイトからの仮利用。正式選定後に差し替え予定
- 文言・キャッチコピー：仮置き。クライアント確認後に修正予定
- 数値・実績：Numbersセクションの数値は確認待ち（HTML内に `<!-- DATA: -->` コメントで明示）
- CTAリンク：`register.html`（未作成）へのダミーリンク

## 画像差し替え方法

FV背景写真は `highclass-lp.css` の冒頭で指定しています：

```css
.fv {
  /* FV背景画像：正式選定後にクライアント指定画像に差し替え */
  --hero-image: url("./assets/top_entrance-uai-1280x1280.jpg");
}
```

`assets/` フォルダの画像ファイルを差し替えるか、URLを変更してください。

## GitHub Pages 公開設定

Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / Folder: `/(root)`
