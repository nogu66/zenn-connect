---
title: "Swiftコードレビューをスキルとサブエージェントにしてみた"
emoji: "🔍"
type: "tech"
topics: ["swift", "claudecode", "codereview", "claude"]
published: true
published_at: 2025-11-22 10:00
---

## はじめに

コードを書いていて、こんな悩みを抱えたことはありませんか?

- 書いているコードが求められているコードスタイルにあっているか
- コードスタイルガイドを毎回確認するのが面倒
- レビュー結果が読みにくく、何をどう修正すればいいか分かりづらい

私もこの問題に直面していました。

この記事では、**Swiftのコードを題材として、GoogleのSwiftスタイルガイドをスキルとして構造化し、サブエージェントで自動的に参照させることで、一貫性のある高品質なコードレビューを実現した方法**を紹介します。

### この記事で得られること

- スキルとサブエージェントを組み合わせたコードレビューの実装方法
- コードレビューの品質と見やすさを改善する具体的なアプローチ

### この記事で扱わないこと

- スキルとサブエージェントの基本概念の詳細説明
   - [別記事](https://zenn.dev/nogu66/articles/claude-code-think-abount-skills-and-subagent)参照
- Swiftの文法や基本的な開発手法

### 対象読者

- 開発経験があり、コードレビューの品質向上に関心がある方
- Claude Codeやを使った効率化fに興味がある方

## なぜSkillsとサブエージェントの組み合わせなのか

良いコードレビューをClaude Codeするには、以下の2つの要素が必要です:

1. **レビュー基準(専門知識)**: コード規約やスタイルガイド(Googleのスタイルガイド)など
2. **レビュー実行環境**: コードを読み込み、基準に基づいて評価する仕組み

この2つを分離することで、以下のメリットが得られます:

- **再利用性**: 同じスタイルガイドを複数のプロジェクトで使える
- **保守性**: スタイルガイドの更新が全レビューに反映される
- **効率性**: 必要な時だけガイドを読み込む

特に、**再利用性**や**保守性**に関しては、ここで作成したスキルを基に、**別のサブエージェントに実装や修正をさせることに使用することができます**。

スキルとサブエージェントは、まさにこの設計思想に沿った機能です、

- **Skills**: 再利用可能な専門知識(スタイルガイド)を保持
- **サブエージェント**: 独立した実行環境でタスク(コードレビュー)を処理

詳しい使い分けについては、以下の記事をご覧ください。

https://zenn.dev/nogupro/articles/claude-code-think-abount-skills-and-subagent

## 実装の全体像

今回実装したシステムは以下の構成です。

![サブエージェントとスキル](/images/code-review-with-subagent-and-skills/system.png)

この構成により、以下が実現できます:

1. スタイルガイドの詳細は**必要な時だけ**読み込まれる
2. サブエージェントは**独立して**レビュータスクを処理
3. 同じSkillを**他のプロジェクト**でも再利用可能

## ステップ1: Swiftスタイルガイド Skillの作成

今回は、以下の**Googleが公開している**「**Swift Style Guide**」からスキルを作成してきます。
https://google.github.io/swift/

### スキルのディレクトリ構造

作成したスキルは、以下のようなディレクトリ構造になっています。

```
.claude/skills/google-swift-style/
   ├── SKILL.md
   ├── formatting-rules.md
   ├── naming-rules.md
   ├── programming-practices.md
   └── examples.md
```

### スキルの作成

それでは、スキルを作成していきましょう。

カスタムスキルの作成方法の詳細は以下をご覧ください。

https://code.claude.com/docs/ja/skills

今回は自分でスキルを定義するのではなく。`skill-creator`を使用してスキルを作成していきます。

https://github.com/anthropics/skills

これはスキルを簡単に作成するための仕組みになります。

詳細な内容は以下のブログが参考になります。

https://tech.findy.co.jp/entry/2025/10/27/070000#:~:text=1%E3%81%A4%E3%81%A7%E3%81%99%E3%80%82-,skill%2Dcreator,-%E3%82%B9%E3%82%AD%E3%83%AB%E3%82%92%E7%B0%A1%E5%8D%98

次に、以下のように入力してスキルを作成いたします。

```
https://google.github.io/swift/　このコードスタイルガイドをスキル化してください。
```
この入力では、以下のように簡素なスキルが作成されました。

```
.claude/skills/google-swift-style/
   └── SKILL.md
```

そのため、さらに修正指示を与えて、スキルを改善しています。

```
これをもう少し改善したい。具体的には、https://google.github.io/swift/ を元に作成しているが内容が少し落ちているので、ファイル分割してもうすこし詳しい内容をスキル化したい
```

そうすると、やっと以下のような構成にすることができました。
**※ トークン数はなかなか使用するので、注意してください**

```
.claude/skills/google-swift-style/
   ├── SKILL.md
   ├── formatting-rules.md
   ├── naming-rules.md
   ├── programming-practices.md
   └── examples.md
```
#### SKILL.md

内容としては、以下のような事項が記載されております。

```md
### 主要機能
1. **コードスキャン** - Swift コードファイルのスタイルガイド準拠を体系的にチェック
2. **違反の特定** - ファイル:行番号の参照で正確に指摘
3. **説明** - 各違反について具体的なルール引用を提供
4. **修正提案** - ビフォー/アフターのコード例を提示
5. **自動修正** - Edit ツールで自動修正を提供
6. **教育** - 各推奨事項の根拠を説明

### 絶対に守るべきルール（優先度最高）
- タブ禁止（4スペースでインデント）
- セミコロン禁止
- 強制アンラップ（`!`）は安全コメント必須
- `try!` は原則禁止
- **100文字の行制限**

### チェック優先順位
1. **Critical** - タブ、セミコロン、強制アンラップなど
2. **高優先度** - 安全性とベストプラクティス
3. **コードスタイル** - ブレース配置、トレーリングカンマなど
4. **命名とドキュメント** - 命名規則、APIドキュメント

### レビューワークフロー
スコープ確認 → ファイルスキャン → 優先度別チェック → レポート作成 → 自動修正提案

実用的、教育的、かつ有用なレビューを提供することを重視したツールです。

特定の規則に関する完全な詳細については、以下の関連ファイルを参照してください：
- [formatting-rules.md](./formatting-rules.md) - すべての書式設定仕様
- [naming-rules.md](./naming-rules.md) - ネーミングルール
- [programming-practices.md](./programming-practices.md) - ベストプラクティス
- [examples.md](./examples.md) - 良い例・悪い例
```

![Skill.md](/images/code-review-with-subagent-and-skills/skill-md-part1.png)
![Skill.md](/images/code-review-with-subagent-and-skills/skill-md-part2.png)
![Skill.md](/images/code-review-with-subagent-and-skills/skill-md-part3.png)

スキルは１ファイルあたり５０００トークンという決まりがあります。
そのため、詳細な規則に関しては、それぞれ適した子ファイルを参照することとなっています。

- **formatting-rules.md**：すべての書式設定仕様
- **naming-rules.md**：ネーミングルール
- **programming-practices.md**：ベストプラクティス
- **examples.md**：良い例・悪い例

## ステップ2: コードレビュー サブエージェントの作成

次に、作成したSkillを参照するサブエージェントを定義します。

### サブエージェントの配置場所

```
.claude/
└── agents/
    └── swift-code-reviewer.md
```

### swift-code-reviewer.mdの作成

次に、サブエージェントをサブエージェントを作成していきます。
こたらも今回は、以下のように入力して作成しています。

```
google-swift-styleのスキルを基にコードレビューするSubAgentを作成してください。
```

このような入力に対して、以下のようなサブエージェントが作成されます。

![swift-code-reviewer.md](/images/code-review-with-subagent-and-skills/agent.png)


### Claude Codeでの実行

では、ここまで作成してきたサブエージェントとスキルを使ってClaude Codeに以下のように依頼します。

```linux
> @agent-swift-code-reviewer '/Users/[UserName]/[workspace]/[Repository]/ContentView.swift'をレビューしてください。 
```
明示的に、サブエージェントを使うことを支持すれば、`@agent-swift-code-reviewer`のような呼び出しにする必要はないです。

しかし、今回は明示的に指定することで必ず挙動するように指示をしています。

### レビュー結果

実際にレビューを対応させると以下のように表示されました。

![レビュー結果](/images/code-review-with-subagent-and-skills/review-result.png)

**レビュー結果のサマリーや問題事項、推奨される対応事項などコードスタイルに沿った内容がレビュー指摘として上がっています。**（~~業務コードではないので、レビュー指摘が多い点は見逃してください~~）

## まとめ

GoogleのSwiftスタイルガイドをスキルとして構造化し、サブエージェントで参照させることで、以下を実現しました。

1. **一貫性のあるレビュー**: スタイルガイドに基づいた網羅的なチェック
2. **見やすい結果**: 優先順位付けと具体的な修正案
3. **再利用性**: 同じSkillを他のプロジェクトでも活用可能
4. **効率性**: Progressive Disclosureによるコンテキスト節約

この仕組みは、Swiftに限らず、他の言語のスタイルガイドにも応用できます。ぜひ、あなたのプロジェクトでも試してみてください。

## おわりに

今回の実装を通じて、スキルとサブエージェントの組み合わせが、コードレビューの品質向上に非常に効果的だと実感しました。

特に、以下の点が重要だと感じています:

- **専門知識(Skills)とタスク実行(サブエージェント)の分離**が保守性を高める
- **構造化されたレビュー基準**が一貫性を生む
- **具体的な修正案**が開発者の学習を促進する

一方で、毎回コード規約を参照させるのは、コンテキストやトークン使用の観点であるとオーバースペックであるようにも感じています。

今後は、よりよいサブエージェントとスキルの使用方法の模索、実際のプロジェクトにおいてのサブエージェントとスキルによる品質向上を目指していきます。


## Xフォローしてね！

Xではより頻繁に情報発信していますので、フォローしていただけると励みになります。

https://x.com/_nogu66

## 参考リンク

- [Google Swift Style Guide](https://google.github.io/swift/)
- [Claude Code - Sub Agents](https://code.claude.com/docs/ja/sub-agents)
- [Claude - Agent Skills](https://docs.claude.com/ja/docs/agents-and-tools/agent-skills/overview)
- [Claude CodeにおけるClaude SkillsとSubAgentsの使い分けと併用を理解する](https://zenn.dev/nogupro/articles/claude-code-think-abount-skills-and-subagent)
- https://code.claude.com/docs/ja/skills
- [【Claude】Agent Skills入門 - はじめてのスキル作成 -](https://tech.findy.co.jp/entry/2025/10/27/070000#:~:text=1%E3%81%A4%E3%81%A7%E3%81%99%E3%80%82-,skill%2Dcreator,-%E3%82%B9%E3%82%AD%E3%83%AB%E3%82%92%E7%B0%A1%E5%8D%98)
