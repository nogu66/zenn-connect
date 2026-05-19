---
title: "Claude Code のマーケットプレイス追加で 404 になる原因：プライベート Bitbucket と SSH"
emoji: "🔧"
type: "tech"
topics: ["claudecode", "bitbucket", "plugin", "git"]
published: true
published_at: 2026-05-20 08:00
---

## はじめに

**Claude Code**をチームとして活用するにあたり、スキル、エージェント、フック、MCPサーバーなどの設定を共有することは欠かせません。**Claude Codeにはプラグインという形で、他のユーザーにカスタムされた機能をプロジェクトやチーム全体に共有する機能があります。また、マーケットプレイスという形で複数のプラグインを束ねることも可能です。**

私自身、チームメンバー間で設定を共有できるようなマーケットプレイス/プラグインの開発を行い、すべてのメンバー間が自走できるような環境整備に挑戦しています。**その中で、エラーに直面しました。**

**この記事では、マーケットプレイス/プラグインの導入時に遭遇したエラーの原因と解決策について説明します。**

## 前提情報
- ソース管理
    - BitBucket（プライベート環境）
- 接続方法
    - SSH接続

## Error: 404 Not Found

まず、発生したエラーは次のようなものです。

```bash
Error: failed to load marketplace
Error: repository not found
Error: 404 Not Found
Error: path not found: .claude-plugin/marketplace.json
```

ざっくりと説明すると、「**マーケットプレイスが見つかりません**」ということです。プライベート環境下においたはずのマーケットプレイスが参照できていませんでした。

## 結論
**SSH接続**をしているリモートリポジトリに対して、次のように**HTTPS接続**していたことが原因でした。

### 前提：プラグインの追加方法
前提として、Claudeでは次のようにマーケットプレイスを追加することができます。
```bash
/plugin marketplace add <マーケットプレイスURL>
```

### 間違ったプラグインの追加方法
エラー発生したとき、次のようにHTTPSのアドレスを入力していました。そのため、SSH接続しか許可されていないためリポジトリがローカルからは参照することができるエラーが発生していました。
```bash
/plugin marketplace add https://bitbucket.org/<ワークスペース>/<レポジトリ>.git
```

### 正しいプラグインの追加方法
本来は、次のようにSSH接続する必要があります。このように設定することでプライベート環境にあるリモートリポジトリからローカルにプラグインを導入することができます。
```bash
/plugin marketplace add git@bitbucket.org:<ワークスペース>/<レポジトリ>.git
```
**次の章からは、なぜそのようなことが発生しているのか、原因をClaude Codeの仕組みから解説していきます。**

## `/plugin marketplace add` の仕組み

`/plugin marketplace add <URL>` を実行すると、Claude Code は概ね次の流れで marketplace を取り込みます。

1. **Git リポジトリの clone（またはダウンロード）**
   - `~/.claude/plugins/marketplaces/` 配下にキャッシュされます
   - Git URL で追加した場合は、通常は `git clone` で取得し、後から `git pull` で更新できるようにします
2. **マーケットプレイス定義の読み込み**
   - リポジトリ内の `.claude-plugin/marketplace.json` を読みます
   - ここに「このマーケットプレイスで配布しているプラグイン一覧」が書かれています
3. **プラグイン一覧の登録**
   - 利用可能になった一覧から `/plugin` UI で選んでインストールできるようになります
   - インストールすると skill / agent / MCP server / hook などが `~/.claude/plugins/` 配下（主に `data/` や `cache/`）に展開されます

[公式ドキュメント](https://code.claude.com/docs/en/discover-plugins)でも、`.git` 付きの Git URL を渡すとリポジトリを **clone** する、と説明されています。そのため、**SSH認証している場合は、Git の Clone や Pull が実行できずエラーが発生するということです。**

## まとめ

今回の 404 は、仕組みを追うと **Claude Code 独自の認証ではなく、普段の Git と同じ URL・同じ認証** の話でした。プライベート Bitbucket に marketplace を置いているなら、`/plugin marketplace add` には **いつも clone している SSH URL** を渡し、追加前に `git ls-remote` で疎通を確認しておくのが確実です。

**とはいえ、マーケットプレイスとプラグインはチーム開発ではかなり便利です。**

- **マーケットプレイス**
    - 社内で使う skill / agent / hook / MCP などを、1 つの Git リポジトリにまとめて配布できる
- **プラグイン**
    - メンバーが必要なものだけ `/plugin install` で入れられ、更新も `git pull` ベースで追従しやすい
- **チーム設定**
    - `.claude/settings.json` の `extraKnownMarketplaces` や `enabledPlugins` と組み合わせれば、「このプロジェクトではこの拡張を使う」という足場を揃えやすい

個人の `CLAUDE.md` や都度コピペで渡すより、**再現性のある形でノウハウを届けられること**がチームにおいて恩恵がが大きいと思います。公式の `anthropics/skills` のような公開 marketplace だけでなく、自社 Bitbucket に置いたプライベート marketplace でも同じ仕組みが使えます。これにより、プロジェクト固有のプラグインを安全に配布することが可能となります。

**社内で Claude Code を広げている方は、ぜひ一度 marketplace を切って、チームで使えるプラグインを配ってみてはいかがでしょうか。。**

## 参考記事
- [マーケットプレイスから事前構築されたプラグインを発見してインストールする](https://code.claude.com/docs/ja/discover-plugins)
- [プラグインを作成する
](https://code.claude.com/docs/ja/plugins)
- [プラグインマーケットプレイスの作成と配布
](https://code.claude.com/docs/ja/plugin-marketplaces)

## X
最新の情報はこちらで投稿しています。
https://x.com/_nogu66

