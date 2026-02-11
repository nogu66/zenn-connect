---
title: "Skills-Orchestration Developmentのすゝめ ~バイブコーディングとノーコード開発を両立したアプローチの提案~"
emoji: "🧠"
type: "tech"
topics: ["ai", "vibecoding", "エージェント設計", "Rork", "claudecode"]
published: true
---

## はじめに

**こんにちは、noguです。**

本記事は以下の記事の続編的立ち位置になります。

https://zenn.dev/nogu66/articles/rork-introduction

前回の記事ではRorkの紹介をしました。

本記事では、Rorkを事例に、AIコーディングにおける**新しいアプローチ**を提案します。

### この記事の対象読者
- AIエージェントの「**Agent Skills**」という概念に興味がある方
- Claude Code / Cursor等でAIを活用した開発をしている方
- Vibe Codingに興味があるが品質のばらつきに困っている開発者


### この記事のスコープ
**扱うこと:**
- 「**Skills-Orchestration Development**」の提唱と定義
- Rorkを事例にしたSkillsの効果
- 開発者が今すぐ実践できるアクション

**扱わないこと:**
- Rorkの基本的な使い方（別記事で対応）
- 特定フレームワークの詳細実装
- LLMモデルの選定方法

### この記事を読むと得られるもの

- Agent Skillsの技術的な仕組みの理解
- 自分の開発環境でSkillsを活用するための具体的な指針



## Agent Skillsとは
本題に入る前にAgent Skillsとは、**専門知識とワークフローを使用して AI エージェントの機能を拡張するための軽量でオープンな形式**です。

もともとAnthropicに開発されました。その後、オープンスタンダートとしてリリースされたことをきっかけに、ますます多くのエージェント製品に採用されてきいます。

### Skillsの基本構造

Agent Skillsは、**`SKILL.md`ファイルを含むフォルダ**として構成されます。このフォルダには、以下の要素を含むことができます：

```
my-skill/
├── SKILL.md          # 必須: 指示とメタデータ
├── scripts/          # オプション: 実行可能なコード
├── references/       # オプション: ドキュメント
└── assets/           # オプション: テンプレート、リソース
```

`SKILL.md`ファイルは、YAML frontmatter（メタデータ）とMarkdown形式の指示で構成されます：

```yaml

name: pdf-processing
description: Extract text and tables from PDF files, fill forms, merge documents.


# PDF Processing

## When to use this skill
Use this skill when the user needs to work with PDF files...
```

最低限、`name`と`description`のメタデータが必要で、Markdown本文には実際の指示が記述されます。

### Progressive Disclosureの仕組み

Skillsの技術的な優れている点は、**Progressive Disclosure**（**段階的開示**）の仕組みにあります。これは以下の3段階で動作します：

#### 1. **発見（Discovery）**

エージェント起動時、各Skillの`name`と`description`のみを読み込み、どのSkillが関連するかを判断できる最小限の情報だけを保持します。

#### 2. **活性化（Activation）**

タスクがSkillの説明と一致した場合、エージェントは`SKILL.md`の完全な指示をコンテキストに読み込みます。

#### 3. **実行（Execution）**

エージェントは指示に従って実行し、必要に応じて参照ファイルを読み込んだり、バンドルされたコードを実行したりします。

このアプローチにより、**エージェントは高速に動作しながら、必要な時に必要な専門知識にアクセス**できます。

Agent Skillsについてより詳しく知りたい方はこちらをご覧ください。

https://agentskills.io/home

## Skills-Orchestration Development

ここで提唱したいのが**Skills-Orchestration Development**（**スキルズ・オーケストレーション開発**）です。

:::message
**ネーミングについては、他によいものがあれば提案してくださると幸いです**
:::


Skills-Orchestration Developmentとは、**AIエージェントに「Agent Skills（ベストプラクティスをパッケージ化したモジュール）」を組み込むことで、自由度を維持しながら品質を均質化するアプローチ**です。

これは、バイブコーディングとノーコード開発の中間のような位置付けであると考えています。

![バイブコーディングとノーコード開発の中間](/images/skills-orchestration-development/thrid-way.png)

ユーザーは自然言語で自由に指示を出せる（Vibe Codingの良さ）。しかし実際の実装は、ベストプラクティスを内包したSkillが主導する（No-Codeの安定性）

![比較](/images/skills-orchestration-development/compare.png)

**Vibe Codingの**「**品質のばらつき**」**とNo-Codeの**「**柔軟性の低さ**」**を同時に解決する、両者のいいとこ取りをした第3の道になるのではないか**。という仮説を持っています。

もちろん、**熟練したソフトウェアエンジニア**にとっては無駄なスキルが増えることにより、コンテキストやワークスペースのトークン増加になる可能性があります。

しかし、一方で**知識・経験の少ないメンバー**が作業する場合でも一定の品質を守ることが可能になると感じています。


## RorkにおけるSkillsの活用事例

### Rorkとは

**Rork**は、自然言語の指示からReact Nativeアプリを構築・公開できるプラットフォームです。
詳しくは以下の記事で紹介しています。

https://zenn.dev/nogu66/articles/rork-introduction

Rorkが類似ツール異なる点として、**Agent Skillsを積極的に活用している**が挙げられます。

### RorkのSkills実行の様子

Rorkで機能追加を行うと、Agent Skillsが自動的に読み込まれます。

![Agent Skillsの読み込み](/images/rork-introduction/add-photo.png)

人間が出す場当たり的な指示に対しても、Skillsが介在することで高品質なコードの生成を可能にしています。

### RorkのSkills一覧
Rorkでは、観測できる範囲で以下のAgent Skillsが用意されています。

- **expo-docs**
    - Expo SDKモジュールのドキュメント（expo-cameraを含む可能性あり）
- **project**
    - アイコン・サムネイル生成
- **rork toolkit**
    - AI機能（チャット、画像生成、音声認識など）
- **backend**
    - Hono/tRPC によるAPI構築
- **debugging**
    - デバッグツール
- **in-app-purchases**
    - アプリ内課金（RevenueCat)

これにより、バックエンドでのAPIとの通信のような普遍的なやりとりをコンポーネント化していると考えられます。

一方、UI的な内容に関してはある程度の自由度を持たせていると感じるため。**重要な処理はコンポーネント、見た目の部分は自由度を高く実装**できます。

:::message
**2026年2月11日現在**
:::

### 具体例: RevenueCatの導入

課金機能の導入を例に、Skillsの効果を見てみます。


#### **Skillsなしの場合（通常のVibe Coding）**

ユーザーが「課金機能を追加して」と指示すると、AIは一般的な知識で実装を試みます。

**結果として**
- RevenueCatのベストプラクティスに沿っていない実装
- サンドボックステストの手順が欠落
- リストア処理の考慮不足
- プラットフォーム固有の設定の漏れ
- 環境依存の高い処理でのつまづき

ユーザーがRevenueCatに詳しくなければ、これらの問題に**気づくことすらできません**。

#### **Skillsありの場合（Rork）**

RorkはRevenueCat統合のSkillを持っています。
ユーザーが「課金機能を追加して」と指示すると：

1. RevenueCat Skillが自動的に展開される
2. ベストプラクティスに沿った実装が自動的に適用される
3. サンドボックステスト、リストア処理、プラットフォーム設定がすべて含まれる

![in-app-purchase](/images/skills-orchestration-development/in-app-purchase.png)


**ユーザーの知識に関係なく、品質が均質化された正しい実装が生成される**のです。

これがSkills-Orchestration Developmentの核心です。



## 開発者が今すぐ実践できること

Skills-Orchestration Developmentの考え方は、Rorkだけでなく**Claude Code、Cursor、その他のAI開発ツール**でも応用できます。

### Skillsを自分で用意する

あなたが使っているAI開発ツールに、あらかじめ**再利用可能なベストプラクティス**（**Agent Skills**）を用意しておくことが重要です。

例えば
- **ドメイン固有のルールやバリデーション要件を文書化したSkills**
- **社内独自の実装方法をコンポーネント化したSkills**

### Skillの設計原則

効果的なSkillを設計する際のポイント

1. **単一責務**: 1つのSkillは1つの機能領域に特化する
2. **自己完結性**: Skill内にWhat/Why/Howをすべて含める
3. **バリデーション内包**: 正しく実装されたかを検証する基準を含める
4. **段階的開示**: すべてを一度に展開せず、必要な部分だけを提供する

### これからのAI活用開発

今後のAI活用開発においては、「いかに良いプロンプトを書くか」だけでなく、「**いかに良いAgent Skillsを事前に用意しておくか**」も成果を分ける重要な要因になります。

なぜならば、あなたが在籍しているような企業において、**真に必要なのは全体としての成果向上だからです**。


あなたのプロジェクトで頻繁に必要になるパターン（**認証、決済、通知、データ同期**）。これらについてAgent Skillsを整備しておくことで、AI開発の品質が安定します。それにより、**あなただけではなく全体として生産性と品質の向上が可能となるでしょう**。


## まとめ

**Skills-Orchestration Development**は、Vibe Codingの「自由度」とNo-Codeの「品質安定性」を両立するアプローチです。

その核となる**Agent Skills**は、ベストプラクティスをパッケージ化し、Progressive Disclosureでコンテキスト効率を高め、ユーザーの知識に依存しない均質な成果物を実現します。

Rorkはこの設計を徹底しているからこそ、ユーザーの知識に関係なく高品質なアプリを生成できています。

そして、この考え方はRorkに限った話ではありません。Claude Code、Cursor、その他のAIツールで開発するすべての開発者が、**自分だけのAgent Skillsを用意しておく**ことで、同じ恩恵を受けられます。



### **この記事が参考になったら、ぜひXでフォローしてください！**
https://x.com/_nogu66

質問や感想があれば、お気軽にDMやリプライで教えてください。



## 参考リンク

- [Agent Skills公式サイト](https://agentskills.io/home)
- [Rork公式サイト](https://rork.com/?ref=nogu)
