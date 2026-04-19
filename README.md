# Let Me Explain…

> Wikipedia の記事を、編集とデザインで読み直す試み。
> An editorial re-reading of Wikipedia articles.

公開URL: https://let-me-explain.netlify.app

---

## 構造

```
.
├── index.html              # ハブ(目次)ページ
├── _redirects              # 旧URLからのリダイレクト
├── netlify.toml            # Netlifyビルド設定
├── meat/                   # N°001 — Meat / 食肉
│   ├── index.html
│   └── img/
└── sushi/                  # N°002 — Sushi / 鮨
    ├── index.html
    └── images/
```

各題目は独立したサブディレクトリで管理し、画像は各ディレクトリ内に格納する。

## URL設計

- `/` — ハブ(目次)
- `/meat/` — N°001 食肉
- `/sushi/` — N°002 鮨

旧URL(`/what-is-meat` 等)は `_redirects` で新URLへ301リダイレクト。

## デプロイ

GitHubリポジトリと Netlify(プロジェクト名: `let-me-explain`)を連携しているため、
`main` ブランチへ push すると自動デプロイされる。

```bash
git add .
git commit -m "メッセージ"
git push
```

## 新しい題目の追加方法

1. 新ディレクトリを作成: `mkdir new-topic`
2. `new-topic/index.html` を配置(画像は `new-topic/img/` または `new-topic/images/` 等)
3. `</body>` の直前に「ハブへ戻る」バッジを追加(他のサブページからコピペ可)
4. ルートの `index.html` の `<nav class="list">` 内に新エントリを追加:
   ```html
   <a class="item" href="/new-topic/">
     <span class="num">N°&nbsp;003</span>
     <div class="title-block">
       <span class="prefix">let me explain…</span>
       <span class="title"><em>Topic</em><span class="ja">日本語名</span></span>
     </div>
     <span class="arrow">→</span>
   </a>
   ```
5. ハブの統計セクション(Subjects/Active数)を更新
6. commit & push

## デザインシステム(ハブページ)

- **フォント**: Bodoni Moda(欧文ディスプレイ)/ Shippori Mincho(和文)/ JetBrains Mono(ラベル)
- **カラー**: 黒地(`#0a0807`)+ 金(`#c9a961`)+ 朱(`#c41e1e`)+ 骨色(`#e8dccb`)
- **アクセント**: 赤い `…` で「説明の続きがある」シリーズ感を表現

## Netlify情報

- **Project name**: `let-me-explain`
- **Site ID**: `262b3efb-8d78-4736-8d81-2ad12fc5e842`
- **Team ID**: `680929f2ccddbe5d4e37494b`

## 旧プロジェクト(削除済み or 削除予定)

- `what-is-meat` → `/meat` へ統合
- `what-is-sushi` → `/sushi` へ統合
- `what-is-sushi-old` → 廃止

## ライセンス

コンテンツの一次出典は [Wikipedia](https://ja.wikipedia.org)(CC BY-SA)。
編集・デザインは個人プロジェクト。
