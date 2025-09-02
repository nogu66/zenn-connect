---
title: "【徹底解説】Claude Code UI と Cloudflare Tunnelでスマホから快適にAIコーディング"
emoji: "🚀"
type: "tech"
topics: ["ClaudeCode", "AI", "Claude", "Cloudflare", zennfes2025free]
published: true
---

## はじめに

先日、X（旧Twitter）を眺めていたところ、私の開発スタイルを根底から揺るすぶる、衝撃的な投稿が目に飛び込んできました。

https://x.com/masa_oka108/status/1960832969217859847

それは、**スマホからClaude Codeを使う方法**という投稿でした。単なるテキストエディタではなく、ローカルPC環境で動作するAIコーディングアシスタントを、どこからでも自在に操る―。その手法を、私は「この環境を自分のものにしたい」と強く思わされました。

その投稿がきっかけで出会ったのが、本記事で紹介する **`Claude Code UI`** と **`Cloudflare Tunnel`** の組み合わせです。

`Claude Code` は、`Anthropic` 社が開発した強力なAIアシスタントですが、本来はPCのターミナル操作が必須でした。しかし、`Claude Code UI` がその常識を覆し、ブラウザ上で直感的に操作できるGUIを提供します。

さらに、`Cloudflare Tunnel` を使えば、そのパワフルな環境を、外出先のスマートフォンからでも安全に呼び出すことが可能になります。

この記事では、私が衝撃を受けた環境を、誰もが手に入れられるように、その具体的な手順を丁寧に解説します。

### 対象読者
- `Claude Code` を利用しているが、ターミナル操作が少し面倒だと感じている方
- AIコーディングツールを、より直感的なUIで操作したい開発者
- 外出先や移動中に、スマートフォンやタブレットでコーディング作業をしたい方
- `Cloudflare Tunnel` を使ったセキュアなリモートアクセス環境に興味がある方

### 記事のスコープ
この記事では、`Claude Code UI` のセットアップ方法から、`Cloudflare Tunnel` を用いて外部からアクセスする手順までを、丁寧に解説します。
`TaskMaster AI` との連携など、より高度な機能については触れません。

## 課題：CLIベースのAIツール操作の限界
`Claude Code` や `Cursor CLI` は非常に強力なAIコーディングアシスタントですが、すべての操作がコマンドライン上で行われるため、開発フローにおいていくつかの非効率な点がありました。

- **What**: ターミナル上で過去の対話履歴を追いかけるのは困難です。
- **Why**: スクロールバックには限界があり、特定のやり取りを見つけるためには `grep` など別のツールを駆使する必要がありました。
- **How**: 結果として、以前のコンテキストを再利用したくても、簡単にはできず思考が中断されがちでした。

- **What**: コードファイルを参照・編集しながらAIと対話する際、ターミナルとエディタを行き来する必要があります。
- **Why**: これにより、コンテキストスイッチのコストが発生し、集中力が削がれます。
- **How**: 特に、AIが生成したコードスニペットをプロジェクトの複数ファイルに適用するような場合、この行き来は非常に煩雑になります。

これらの課題を解決し、AIとの対話を開発ワークフローにシームレスに統合するのが `Claude Code UI` です。

## 解決策：Claude Code UIによる開発体験の向上
`Claude Code UI` は、Claude CodeおよびCursor CLI用のデスクトップおよびモバイル UI です。ローカルまたはリモートから使用して、Claude Code または Cursor でアクティブなプロジェクトやセッションを表示し、どこからでも（モバイルまたはデスクトップ）変更を加えることができます。これにより、どこでも動作する適切なインターフェースが実現します。Claude Sonnet 4、Opus 4.1、GPT-5などのモデルをサポートしています。

https://github.com/siteboon/claudecodeui

## 主な特徴（詳細解説）

### 1. レスポンシブデザイン
- **What**: デスクトップ、スマホ、タブレットなど、あらゆるデバイスの画面サイズに最適化されたUIを提供します。
- **Why**: これにより、PCでの本格的な開発作業中はもちろん、移動中にスマートフォンで少しアイデアを試したり、タブレットでコードレビューをしたりといった、柔軟な働き方が可能になります。
- **How**: ブラウザでアクセスするだけで、特別なアプリをインストールすることなく、どのデバイスでも一貫した操作性を得られます。

![モバイル版](/images/claudecodeui/mobile.png =250x)


### 2. インタラクティブなチャット
- **What**: 使い慣れたチャットアプリのようなUIで、AIとの対話をスムーズに行えます。
- **Why**: CLIでの一行ずつのやり取りとは異なり、会話の流れ全体を視覚的に把握できます。これにより、複雑な問題解決の際にも思考を整理しやすくなります。
- **How**: チャット履歴は自動で保存され、いつでも過去の対話を参照できます。コードブロックはシンタックスハイライト付きで表示され、ワンクリックでコピーできます。

![デスクトップ版](/images/claudecodeui/desktop.png)


### 3. ファイルとGitの統合
- **What**: UI内に、シンタックスハイライト付きのファイルエクスプローラーと、Gitの差分表示やコミットが可能なGitエクスプローラーを搭載しています。
- **Why**: AIにプロジェクト全体のコードを読み込ませて質問したり、生成されたコードを直接ファイルに書き込んだり、そのままGitでバージョン管理したり、といった一連の作業がUI内で完結します。エディタとターミナルを往復する必要はもうありません。
- **How**: 左側のパネルでファイルツリーをブラウズし、ファイルをクリックして内容をチャットに送りAIにコンテキストを伝えます。AIの提案を編集し、保存。その後Gitパネルに切り替え、変更内容を確認してコミットメッセージを書き込み、コミットを実行します。

![Git](/images/claudecodeui/git.png =250x)


### 4. セッション管理
- **What**: 複数の対話セッションを管理し、簡単に切り替えたり再開したりできます。
- **Why**: プロジェクトごとや、解決したい課題ごとにセッションを分けることで、コンテキストが混ざるのを防ぎます。「あの機能についてAIと相談した履歴はどこだっけ？」と探す手間がなくなります。
- **How**: 新しいチャットを開始すると新しいセッションが作られ、過去のセッションはリストから選択するだけでいつでもその時の状態に戻ることができます。

![セッション](/images/claudecodeui/new-session.png)

## 具体的な導入手順

### 前提条件
- Node.js v20以上
- `Claude Code` または `Cursor CLI` がインストールされ、設定済みであること

### セットアップ

1.  **リポジトリをクローン**
```bash
git clone https://github.com/siteboon/claudecodeui.git
```

```
cd claudecodeui
```
https://github.com/siteboon/claudecodeui?tab=readme-ov-file

2.  **依存関係をインストール**
```bash
npm install
```

3.  **環境変数を設定**

`.env.example` ファイルをコピーして `.env` ファイルを作成します。これは、アプリケーションの基本的な設定を管理するための重要なステップです。
```bash
cp .env.example .env
```
必要に応じて、`.env` ファイルを編集して、デフォルトのポート `5173` などを変更できます。

`.env`
```.env
# Claude Code UI Environment Configuration
# Only includes variables that are actually used in the code

# =============================================================================
# SERVER CONFIGURATION
# =============================================================================

# Backend server port (Express API + WebSocket server)
#API server
PORT=5173
#Frontend port
VITE_PORT=5173
```

4.  **アプリケーションを起動**
```bash
npm run dev
```

![起動](/images/claudecodeui/npm-run-dev.png)


ブラウザで `http://localhost:5173` を開くと、UIが表示されます。

![UI](/images/claudecodeui/session.png)



### セキュリティに関する注意
**重要**: セキュリティ上の理由から、インストール直後はすべてのClaude Codeツール（ファイルの読み書きやコマンド実行など）が無効になっています。右上の設定メニューから、自分が利用したいツールを選択して有効化してください。

## Cloudflare Tunnelで外部からアクセスする

`Claude Code UI` をローカルでセットアップできたら、次はいよいよ `Cloudflare Tunnel` を使って、外出先のスマートフォンや別のPCからでもアクセスできるように設定します。

`Cloudflare Tunnel` は、面倒なポート開放やグローバルIPアドレスの心配をすることなく、ローカルで実行されているサービスを安全にインターネットへ公開できる非常に便利な機能です。

### 前提条件

- **Cloudflareアカウント**: 無料で作成できます。
- **独自ドメイン**: Cloudflareに登録するためのドメインが必要です。
- **`Claude Code UI`がローカルで起動していること**: `http://localhost:5173` でアクセスできる状態にしておいてください。

### 1. `cloudflared` のインストール

まず、Cloudflare Tunnelを操作するためのコマンドラインツール `cloudflared` をインストールします。お使いのOSに合った方法でインストールしてください。

**macOS (Homebrew)**
```bash
brew install cloudflare/cloudflare/cloudflared
```

**Windows (Scoop)**
```bash
scoop install cloudflared
```

**Linux**
```bash
# .deb (Debian, Ubuntu)
curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared.deb

# .rpm (Red Hat, CentOS)
curl -L --output cloudflared.rpm https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.rpm
sudo rpm -i cloudflared.rpm
```
インストール後、`cloudflared --version` を実行して、バージョン情報が表示されれば成功です。

### 2. Cloudflareへのログイン

次に、`cloudflared` をあなたのCloudflareアカウントに接続します。
以下のコマンドを実行してください。

```bash
cloudflared tunnel login
```

コマンドを実行すると、ターミナルにURLが表示され、自動的にブラウザが開いてCloudflareへのログインを求められます。

![Cloudflareへのログイン](/images/claudecodeui/cloudflare-login.png)

ログイン後、`cloudflared`があなたのドメインにアクセスすることを許可する画面が表示されます。ここで利用したいドメインを選択し、「Authorize」ボタンをクリックします。
※この機能を利用するには、あらかじめCloudflareに独自ドメインを登録しておく必要があります。

![Connect](/images/claudecodeui/connect.png)

![ドメインの設定](/images/claudecodeui/domain.png)

![認証](/images/claudecodeui/authorize.png)

成功すると、以下のような画面が表示されます。

![成功](/images/claudecodeui/complete.png)

同時に、ターミナル側にも成功メッセージが表示され、`~/.cloudflared/` ディレクトリに証明書ファイル (`cert.pem`) が生成されていれば、アカウントへの接続は完了です。

![ログイン成功](/images/claudecodeui/success-login.png)

### 3. トンネルの作成

次に、外部からのアクセスを受け付けるための「トンネル」を作成します。
`my-claude-code-ui` の部分は、好きな名前に変更できます。

```bash
cloudflared tunnel create my-claude-code-ui
```

このコマンドを実行すると、トンネルのIDと、JSON形式のクレデンシャルファイル（`<TUNNEL_ID>.json`）が生成されます。このIDは後で使いますので、控えておいてください。

### 4. トンネルのルーティング設定

作成したトンネルに、「どのドメインへのアクセスを、どのローカルサービスに転送するか」を設定します。

以下のコマンドを実行してください。`<SUBDOMAIN.YOUR_DOMAIN>` の部分を、あなたが使いたいサブドメインとドメインに置き換えます。`<TUNNEL_ID>` は先ほど控えたIDです。

```bash
cloudflared tunnel route dns <TUNNEL_ID> <SUBDOMAIN.YOUR_DOMAIN>
```

これにより、CloudflareのDNSに `SUBDOMAIN.YOUR_DOMAIN` のCNAMEレコードが自動的に作成され、トンネルに紐付けられます。

### 5. トンネルの実行

最後に、トンネルを実行して、ローカルの `Claude Code UI` を公開します。
`Claude Code UI` は `http://localhost:5173` で動いているので、そこへ転送するように指定します。

`~/.cloudflared/` ディレクトリに `config.yml` というファイルを作成し、以下のように記述します。

`config.yml`:
```yaml
tunnel: <TUNNEL_ID>
credentials-file: /Users/<YOUR_USERNAME>/.cloudflared/<TUNNEL_ID>.json

ingress:
  - hostname: <SUBDOMAIN.YOUR_DOMAIN>
    service: http://localhost:5173
  - service: http_status:404
```
`<TUNNEL_ID>`, `<YOUR_USERNAME>`, `<SUBDOMAIN.YOUR_DOMAIN>` を自分のものに書き換えてください。

この設定ファイルがあれば、以下のコマンドだけでトンネルを起動できます。
```bash
cloudflared tunnel run
```

![モバイルからの接続](/images/claudecodeui/tunner-mobile.jpeg =250x)


これで、いつでもどこからでも、あなたの `Claude Code UI` にアクセスできるようになりました！

**※ 2025/08/30：ドメインからログインできない現象を調査中**

## おわりに
本記事では、`Claude Code UI` がどのようにCLIベースのAIコーディングの課題を解決し、開発体験を向上させるかを詳細に解説しました。

単なるUIの提供に留まらず、ファイル操作からバージョン管理まで、AIとの対話を中心とした開発ワークフロー全体をシームレスに統合してくれる強力なツールです。CLIの操作性に不便を感じていた方は、ぜひ導入を検討してみてください。

より詳細な情報や最新のアップデートについては、[公式GitHubリポジトリ](https://github.com/siteboon/claudecodeui) をご確認ください。


## 𝕏フォローしてくれると嬉しいです！
𝕏ではリアルタイムな情報発信しているので、フォローしてください！

https://x.com/_nogu66
## 参考
- https://claudecodeui.com/
- https://github.com/siteboon/claudecodeui
- https://zenn.dev/takajun/articles/fbd783e459c722
