---
title: "Claude Code で Playground を作る（日本語訳）"
original: "[[Making Playgrounds using Claude Code]]"
source: "https://x.com/trq212/status/2017024445244924382"
author:
  - "[[@trq212]]"
published: 2026-01-30
translated: 2026-05-20
tags:
  - clippings
  - translation
  - technical-writing
lang: ja
---

# Claude Code で Playground を作る

> 原文: [[Making Playgrounds using Claude Code]]

**playground** という新しい Claude Code プラグインを公開しました。Claude が HTML playground を生成するのを助けます。スタンドアロンの HTML ファイルで問題を可視化し、操作し、Claude Code に貼り戻す出力プロンプトを得られます。

テキストだけでは向かないやり取りに特に有効だと感じています。例:

- コードベースのアーキテクチャの可視化
- コンポーネントデザインの調整
- レイアウト・デザインのブレスト
- ゲームのバランス調整

**はじめ方:** Claude Code で次を実行:

```
/plugin marketplace update claude-plugins-official
/plugin install playground@claude-plugins-official
```

お気に入りの playground の例:

### Claude Code の AskUserQuestion ツールのレイアウト変更

**プロンプト:** "Use the playground skill to create an playground that helps me explore new layout changes to the AskUserQuestion Tool"

（動画・画像は原文クリッピングを参照）

### 文章の批評とフィードバック

**プロンプト:** "Use the playground skill to review my SKILL.MD and give me inline suggestions I can approve, reject or comment"

### Remotion イントロの調整

**プロンプト:** "Use the playground skill to tweak my intro screen to be more interesting and delightful"

### アーキテクチャ図の閲覧とコメント

**プロンプト:** "Use the playground skill to show how this email agent codebase works and let me comment on particular nodes in the architecture to ask questions, make edits, etc"

### スーパーヒーロー・ローグライクのバランス

**プロンプト:** "Use the playground skill to help me balance the 'Inferno' hero's deck"

皆さんの試行を楽しみにしています。面白い playground を作るコツ——モデルとのユニークなやり取りを考え、それを表現するよう頼む。驚くかもしれません。良いものができたらぜひ共有してください。
