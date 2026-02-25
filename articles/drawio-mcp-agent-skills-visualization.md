---
title: "draw.io MCP × Agent SkillsでAI図作成の品質を上げる"
emoji: "📊"
type: "tech"
topics: ["claude", "mcp", "drawio", "ai", "可視化"]
published: true
---

## はじめに

こんにちは、noguです。普段はシステム開発とAI推進、AIエージェント開発を行っています。

**この記事の対象読者**
- draw.io MCPに興味がある方
- Agent Skillsを実務で活用したい方
- プロジェクトのアーキテクチャ図作成を効率化したい方

**この記事でわかること**
- draw.io MCPの基本とセットアップ方法
- draw.io MCPの品質課題とその原因
- Agent Skillsで中間データの品質を制御する方法
- 実際のスタイルマッピングSkillの作り方

**この記事で扱わないこと**
- Agent Skillsの詳細な仕組み
- draw.io自体の詳しい使い方
- Mermaid記法の詳細

この記事を最後まで読むことで、**AIに図を作らせる際の品質を安定化させ、実務で使える図を効率的に生成できるよう**になります。

## draw.io MCPとは

**draw.io MCPは、draw.io公式がリリースしたMCPサーバー**です。LLMがdraw.ioエディタでダイアグラムを作成・編集できるようになります。

2026年2月にdraw.io公式（@drawioアカウント）から正式にアナウンスされました。

https://x.com/drawio/status/2020918870375370825?s=20

### 3つの実装方式

draw.io MCPには、3つの異なる実装方式があります:

| 特徴 | MCP App Server | MCP Tool Server | プロジェクト指示 |
|------|----------------|-----------------|----------------|
| 出力方法 | チャット内インライン | ブラウザ新タブ | draw.ioリンク |
| インストール | 不要 | npmパッケージ | 不要 |
| 対応形式 | XMLのみ | XML、CSV、Mermaid | XML、CSV、Mermaid |

**推奨はMCP Tool Server方式です。** npmパッケージとして提供され、すべてのデータ形式に対応しています。

### 3つのツール

MCP Tool Serverは、3つの異なるツールを提供しています。

1. **open_drawio_xml** - mxGraph XML形式（精密な制御が必要な場合）
2. **open_drawio_csv** - CSV表形式（組織図、階層データ向け）
3. **open_drawio_mermaid** - Mermaid構文（フローチャート、シーケンス図）**← 推奨**

**Mermaid形式が最も推奨されます。LLMがMermaid記法を理解しやすく、図の生成品質が安定するため**です。

### セットアップ方法

draw.io MCPのセットアップは非常にシンプルです。

```bash
npx @drawio/mcp
```

Claude Desktopで使う場合は、設定ファイルに以下を追加します:

```json
{
  "mcpServers": {
    "drawio": {
      "command": "npx",
      "args": ["@drawio/mcp"]
    }
  }
}
```

### 動作方法

draw.io MCPは、以下のパイプラインで動作します:

1. LLMが図のデータを生成（XML/CSV/Mermaid）
2. `encodeURIComponent`でURLエンコード
3. `pako.deflateRaw`で圧縮
4. Base64エンコード
5. JSON構造体を生成
6. `#create`ハッシュ付きURLを生成
7. ブラウザで起動

つまり、**draw.io MCPはデータをdraw.ioに渡すパイプラインに過ぎません。** 図の品質は、LLMが生成する中間データ（XML/CSV/Mermaid）に完全に依存します。

## draw.io MCPの弱点

draw.io MCPを実際に使ってみると、ある**弱点**に気づきます。

それは、**CSV・XML・Mermaidをdrawioフォーマットに変換するだけ**のツールにすぎないということです。図の精度は、LLMが生成する中間データの品質に完全に依存します。

つまり、以下のような問題が発生します。

- **スタイルが毎回異なる（色、フォント、配置など）**
- **レイアウトが不自然（重なり、間隔のばらつき）**
- **同じプロンプトでも出力が安定しない**

これは、LLMが中間データを生成する際に一貫性のあるルールを持たないためです。

### 品質が決まるポイント

図作成のフローを分解すると、以下のようになります。

![作成フロー](/images/drawio-mcp-agent-skills-visualization/flow.png)

**STEP 2〜3の中間データ生成の品質が、最終的な図の品質を決定します。** draw.io MCPは単なるパイプライン（STEP 4）なので、この部分には関与しません。

## Agent Skillsで中間データ品質を制御する

Agent Skillsは、Claudeに特定分野の専門知識を提供する再利用可能な学習教材です。Skillsを使うことで、中間データ生成のルールを定義し、一貫性のある出力を実現できます。

詳しい仕組みは、こちらの記事をご覧ください:

https://zenn.dev/nogu66/articles/claude-code-think-abount-skills-and-subagent

### なぜAgent Skillsが有効なのか

Agent Skillsが有効な理由は、以下の3つです。

1. **段階的開示（Progressive Disclosure）でコンテキスト効率が高い**
   - メタデータ（約100トークン）が最初にロードされる
   - 必要なときだけ完全な指示がロードされる
   - トークンの無駄を削減できる

2. **再利用可能で一貫性が保てる**
   - スタイルルールを一度定義すれば、すべての図作成で適用される
   - 会話をまたいで同じルールを使える
   - チーム内で共有できる

3. **スタイルマッピングに最適**
   - サンプル画像を与えることで、スタイルを学習できる
   - デザイン規則をSkillとして定義できる
   - LLMの出力を一貫性のあるものに制御できる

## どのように実装するのか

実際のスタイルマッピングSkillの作成手順を見ていきます。

### STEP 1: サンプル画像を用意する

まず、理想とする図のサンプル画像を用意します。これが「お手本」になります。

![サンプル](/images/drawio-mcp-agent-skills-visualization/sample.png)
*[公式サイト](https://drawio-app.com/blog/creating-different-types-of-flowcharts-with-draw-io/)より引用*

### STEP 2: Skills を作成する

今回は、サンプル画像スタイルへの適用とMCPでの画像作成までを行うスキルが欲しかったです。

そのため、その旨をClaude Codeに作成させています。

#### ディレクトリ構成

作成したSkillのディレクトリ構成は以下のようになります:

```
drawio-business-diagram/
├── SKILL.md              # メインのSkillファイル
└── references/
    ├── style-guide.md    # XMLスタイル定義
    └── diagram-templates.md  # テンプレート集
```

**各ファイルの役割**

| ファイル | 役割 |
|---------|------|
| `SKILL.md` | Skillのメタデータ、デザインスタイル、ワークフローを定義 |
| `references/style-guide.md` | draw.io XMLの具体的なスタイル定義（色、フォント、図形のスタイル文字列） |
| `references/diagram-templates.md` | 実際に動作するXMLテンプレート（コピペで使える完成例） |

この構成により、LLMは必要に応じて詳細なスタイル定義やテンプレートを参照し、一貫性のある図を生成できます。

以下は一部抜粋となりますので、全文はGitHubのリポジトリをご覧ください。

https://github.com/nogu66/claude-code/tree/main/drawio-business-diagram

#### SKILL.md

```md
---
name: drawio-business-diagram
description: Create professional business process diagrams in draw.io with a consistent corporate design style featuring dark navy process boxes, sky blue document shapes, and vertical swim lanes. Uses the draw.io MCP tool (open_drawio_xml) to render diagrams directly in the browser. Use when the user asks to create flowcharts, business process diagrams, swim lane diagrams, workflow diagrams, organizational process visualizations, or any diagram in draw.io format. Also use when the user mentions draw.io, mxGraph, or requests process flow visualization.
---

# Draw.io Business Process Diagram Creator

Generate professional business process diagrams in a consistent corporate design style using the draw.io MCP integration.

## Design Style

**Color Palette:**
- Process boxes: Dark navy `#1B365C`, stroke `#0D1B2A`, white text
- Document/data shapes: Sky blue `#4A90D9`, stroke `#2E6DA4`, white text
- Swim lane background: Light lavender `#D6E4F0`, stroke `#9BB8D3`
- Swim lane header text: Dark navy `#1B365C`, bold
- Arrows: Black `#000000`, orthogonal routing, block end arrows
- Decision diamonds: Sky blue `#4A90D9`, white text

**Shape Mapping:**
- Process / task / activity → Rounded rectangle (dark navy)
- Document / report / invoice / form / notification → Document shape with wave bottom (sky blue)
- Decision / condition → Diamond (sky blue)
- Data / database → Cylinder (sky blue)
- Start / End → Stadium shape (dark navy)

## Workflow

1. Understand the business process: roles, steps, documents, decisions
2. Identify swim lanes (one per role/department)
3. Map each process step to the correct shape using the shape mapping above
4. Generate draw.io XML following the style definitions in [references/style-guide.md](references/style-guide.md)
5. Render using `mcp__drawio__open_drawio_xml` with the generated XML

~~~
```

#### references/diagram-templates.md

```md
# Diagram Templates

## Template 1: Simple 3-Lane Business Process

A sales order process with 3 roles.

```xml
<mxGraphModel dx="1422" dy="762" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1100" pageHeight="700" math="0" shadow="0">
  <root>
    <mxCell id="0" />
    <mxCell id="1" parent="0" />
    
~~~

<mxCell id="crossEdge" value="" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#000000;strokeWidth=1.5;endArrow=block;endFill=1;" edge="1" source="[source_id]" target="[target_id]" parent="1">
  <mxGeometry relative="1" as="geometry" />
</mxCell>
```

#### references/style-guide.md

```md
# Draw.io XML Style Guide

## XML Structure

Every diagram uses this base structure:

~~~

## Cell Dimensions

| Shape | Width | Height |
|-------|-------|--------|
| Process box | 140 | 50 |
| Document shape | 120 | 60 |
| Decision diamond | 100 | 60 |
| Database cylinder | 100 | 60 |
| Start/End stadium | 120 | 40 |

## Swim Lane Construction

Build swim lanes using a table-based approach:

~~~

For cross-lane edges, set `parent="1"` (root level) so the arrow routes across lanes properly.
```

### 実際の効果

この方法で実際に試した結果、以下のような成果が得られました:

**スキルなし（左）とスキルあり（右）の比較**

| Before | After |
| ---- | ---- |
| ![Before](/images/drawio-mcp-agent-skills-visualization/before.png =250x) | ![After](/images/drawio-mcp-agent-skills-visualization/after.png =250x) |

- デザインを再現
- 配色パターンが完全に一致
- レイアウトルールが適用されている



試作段階でこの精度なら、業務レベルでも十分に実用的です。

## やってみた結果

### 成功した点

- **スタイルの一貫性が劇的に向上**
  - 同じSkillを使うことで、すべての図が統一されたデザインになった
  - 配色やフォントが自動的に適用される

- **作成時間の大幅な短縮**
  - サンプル画像とSkillを渡すだけで、ほぼ完成形が出力される
  - 手直しの時間が80%削減された

- **再利用性が高い**
  - 一度Skillを作れば、すべてのプロジェクトで使える
  - チームメンバーと共有できる

### 直面した課題と解決方法

#### 複雑なレイアウトの再現が難しい

複雑な図形配置や特殊なレイアウトは、Mermaidの表現力の限界で完全再現が難しい場合があります。

draw.io上で最終調整する前提で、80%の完成度を目指すのがよいかもしれない。

### 学んだこと

draw.io MCP × Agent Skillsの組み合わせを通じて、以下のことを学びました:

1. **中間データの品質が最終成果物を決定する**
   - MCPはパイプラインに過ぎない
   - 品質制御は中間データ生成の段階で行うべき

2. **Agent SkillsはAI出力の一貫性を保つ強力なツール**
   - 再利用可能な知識として定義できる
   - コンテキスト効率が高い
   - チームでの知識共有に最適

3. **完璧を目指さず、80%の完成度で十分**
   - AIが完璧な図を作ることは期待しない
   - 最終調整は人間が行う前提で、効率化を図る

## おわりに

draw.io MCP は、なかなか使いやすいMCPであると思います。

一方で、draw.io MCP単体ではLLMの出力に依存してしてしまいます。

Agent Skillsでスタイルマッピングと中間データの品質を制御することで、一貫性のある実用レベルの図を安定的に生成できるのではないかと考えています。

### 今すぐ始めるには

1. draw.io MCPをセットアップする: `npx @drawio/mcp`
2. 理想的な図のサンプル画像を用意する
3. Claude Codeに作成して欲しい内容をスキル化してもらう
5. Claude Codeで図を生成してみる

### 今後の展望

今後、以下のような発展が期待できます。

- より高度なレイアウトアルゴリズムのSkill化
- 業界標準のダイアグラムスタイル（UML、C4モデルなど）のSkillライブラリ
- チーム全体で共有できるSkillsのベストプラクティス集

---

この記事が役に立ったら、Xをフォローしていただけると嬉しいです!

https://x.com/_nogu66

## 参考リンク

- [draw.io MCP - npm](https://www.npmjs.com/package/@drawio/mcp)
- [draw.io MCP - GitHub](https://github.com/jgraph/drawio-mcp)
- [Claude Skills公式ドキュメント](https://docs.claude.com/ja/docs/agents-and-tools/agent-skills/overview)
- [Claude CteodeにおけるSkillsとSubAgentsの使い分け - Zenn](https://zenn.dev/nogu66/articles/claude-code-think-abount-skills-and-subagent)
