---
title: "asc CLI で App Store Connect をターミナルと AI から操作する"
emoji: "🍎"
type: "tech"
topics: ["ios", "appstore", "ai", "claudecode","codex"]
published: true
---

## はじめに

**App Store Connect の操作は、ダッシュボードの手作業だけでなく、CLI と AI エージェントから行うことができます。**

iOS や macOS のアプリを出すとき、避けて通れないのが **App Store Connect への提出** です。

ビルドのアップロード、アプリ説明の記入、スクリーンショットのアップロード、審査提出など。やるべきことがたくさんあります。しかし、**毎回ダッシュボードを開いて手入力するやり方では、手間と時間がかかります。**

**そこで、本記事では、asc CLI とその Agent Skills を使い、Claude Code や Codex などの AI エージェントから App Store Connect を扱う方法を整理します。**

私自身は、コマンドを直接叩くより **Agent Skills 経由で AI に任せる使い方**を主にしています。本記事も、その前提で書いています。

**この記事の対象読者**
- Claude Code、Codex などから App Store Connect を操作したい人
- App Store Connect の定番作業を Agent Skills に任せたい人
- アプリ提出まわりの手順を、毎回自分で覚え直したくない人

**この記事でわかること**
- asc CLI と Agent Skills の役割分担
- インストール・認証・スキル導入までの流れ
- AI エージェントへの指示の出し方と実践例

**この記事で扱わないこと**
- CI/CD パイプラインへの組み込み詳細
- App Store Connect API の全エンドポイント解説
- RevenueCat 側の MCP / スキル詳細（連携の話は最後に短く触れる）

## asc CLI

**asc CLI**（**App Store Connect CLI**）**とは、App Store Connect API をターミナルのコマンドから操作できる Go 製の CLI ツールです。**

https://asccli.sh

https://github.com/rorkai/App-Store-Connect-CLI

Xcode や App Store Connect ダッシュボードを開かずに、ビルドのアップロード、TestFlight 配布、審査提出、メタデータ更新までをターミナルから完結できます。

対応プラットフォームは、App Store Connect API がサポートする **iOS / macOS / tvOS / visionOS** です。

ただし、CLI 本体だけでは「どのコマンドをどの順で叩くか」はまだ人間側の知識です。**AI エージェントから安定して使うには、その手順を Agent Skills として渡す必要があります。**

## Agent Skills

**Agent Skills とは、asc コマンドをどの順番で・どう組み合わせるかを AI エージェントに教える Markdown ベースの手順書です。**

スキル側のリポジトリはこちらです。

https://github.com/rorkai/app-store-connect-cli-skills

ビルド、TestFlight、メタデータ、審査提出、署名など、ASC まわりの定番ワークフローがスキル化されています。エージェントはスキルを読み、必要な `asc` コマンドを組み立てて実行します。

私の運用では、次のような分担になっています。

| レイヤー | 役割 |
| --- | --- |
| **asc CLI** | 実際に ASC API を叩く実行基盤 |
| **Agent Skills** | 「何をどの順でやるか」を AI に教える手順書 |
| **AI エージェント** | 自然言語の指示を受けて、スキルと CLI を組み合わせて実行する |

つまり、入口は自然言語で指示すればよく、その裏では Skills と CLI が動いている、という形です。

![asc CLI / Agent Skills / AI エージェントの役割分担](/images/asc-cli-app-store-connect/role-division.png)

## とりあえず、使い方だけ知りたい人はこちら

1. `brew install asc` でインストールする
2. App Store Connect API キー（`.p8`）で `asc auth login` する
3. `asc install-skills` で Agent Skills を入れる
4. AI エージェントに、対象アプリ・やりたいこと・完了条件を明示して指示する
5. 提出や配布の前は、dry-run / 確認ステップを挟むよう伝えておく

## インストールと認証

Agent Skills 経由で使う場合でも、下回りとして asc CLI のインストールと認証は必要です。

### インストール

```bash
# Homebrew（推奨）
brew install asc

# Install script（macOS / Linux）
curl -fsSL https://asccli.sh/install | bash
```

### 認証

App Store Connect API キー（`.p8`）を [appstoreconnect.apple.com](https://appstoreconnect.apple.com) で発行し、登録します。

```bash
asc auth login \
  --name "MyApp" \
  --key-id "ABC123" \
  --issuer-id "DEF456" \
  --private-key /path/to/AuthKey.p8 \
  --network
```

トラブル時は `asc auth doctor` で切り分けできます。認証が通ったら、動作確認として次を実行します。

```bash
asc apps list
```

アプリ一覧が見えれば、エージェントから ASC を触る土台は整っています。

## Agent Skills を入れる

次に、AI エージェントが手順を知っている状態にします。

```bash
# asc CLI から直接インストール
asc install-skills

# npx 経由で特定エージェント向けにインストール
npx skills add rorkai/app-store-connect-cli-skills --global --agent codex
```

これで、ビルド、TestFlight、メタデータ、審査提出などの定番フローを、エージェントがスキルとして参照できるようになります。

## AI エージェントへの指示の出し方

Skills を入れたあとのポイントは、**ゴールだけ言わないこと**です。

エージェントはスキルを読めますが、対象アプリや完了条件が曖昧だと、途中で止まります。あるいは、想定と違う範囲まで進みます。

### 悪い例

```text
App Store に出しておいて
```

### 良い例

```text
asc の Agent Skills を使って、次を実行してください。

対象アプリ: MyApp
やること: ビルドして Internal Testers に TestFlight 配布する
完了条件:
- apps list で対象アプリ ID を特定できている
- ビルドのアップロードが成功している
- Internal Testers グループへの追加が完了している
- 各ステップの結果を確認し、失敗したら止める
```

指示に含めると安定しやすい要素は、次の4つです。

1. **対象** — アプリ名 / Bundle ID / グループ名
2. **やること** — TestFlight 配布なのか、メタデータ更新なのか、審査提出なのか
3. **完了条件** — 何が満たされたら終わりか
4. **安全策** — 失敗したら止める、提出前に確認する、dry-run する

asc は破壊的操作に `--dry-run` をサポートしています。エージェントに任せるときも、「提出の前に dry-run で確認して」と書いておくと安心です。

## よくある指示例

ここからは、よくある作業を自然言語の指示例で示します。コマンド列を覚える必要はありません。エージェントと Skills 側に寄せます。

### TestFlight 配布

```text
asc のスキルを使って、MyApp をビルドし、
Internal Testers グループへ TestFlight 配布してください。

- 次のビルド番号を取得してから進める
- アップロード成功を確認してからグループ追加する
- 失敗したら止めて、原因を報告する
```

エージェントはスキルを参照し、ビルド番号算出 → アーカイブ → アップロード → グループ追加、といった順で `asc` を組み立てます。

### メタデータ更新

```text
asc のスキルを使って、MyApp の App Store メタデータを更新してください。

- 対象ロケール: 日本語 / 英語
- リリースノートは直近の git log から生成する
- 適用前に差分を見せて、問題なければ apply する
```

説明文やスクリーンショットまわりも、ダッシュボードを開かずに進めやすくなります。

### 審査提出

```text
asc のスキルを使って、MyApp を審査提出する準備をしてください。

- 提出前チェックを先に実行する
- ブロッカーがあれば修正案を出して止まる
- 問題なければ、提出コマンドの内容を確認させてから実行する
```

提出は取り返しがつきにくいので、**確認ステップを指示に含める**のがおすすめです。

## おわりに

App Store Connect の操作は、毎回同じ手順を自分で思い出すのも負担です。

それに対して、**asc CLI を実行基盤に、Agent Skills で手順を AIエージェント に渡す**と、入口を自然言語に寄せられます。

私自身は、この Agent Skills ベースの使い方を主にしています。まずは `brew install asc` → `asc auth login` → `asc install-skills` まで進め、エージェントに 審査画面の記載を埋めることを頼んでみてください。

そんな私が **Shipaton 2026 Japan Ambassador** を務めているのが、RevenueCat 主催のモバイルアプリハッカソン **Shipaton 2026** です。

https://jp.shipaton.com/

開催期間は **2026年8月1日（土）〜9月30日（水）**。2ヶ月間でアプリを開発し、ストアに公開し、マネタイズにチャレンジするイベントです。参加資格は不問で、AI 開発ツールのクレジットも用意されています。

「ストア公開」と「課金実装」が参加条件に近いイベントだからこそ、本記事で紹介した asc CLI のようなツールが効いてきます。興味がある方は、ぜひ参加してみてください。

https://jp.shipaton.com/


## Xアカウント

日常的な実践内容はXで発信しています。
https://x.com/_nogu66

## 参考文献

- [Shipaton 2026](https://jp.shipaton.com/)
- [Shiapton 2026 登録サイト](https://revenuecat-shipaton-2026.devpost.com/?ref_content=featured&ref_feature=challenge&ref_medium=portfolio&_gl=1*temstq*_gcl_au*ODgxMzc2NjkuMTc4MTg0NjY0Nw..*_ga*MjI3Mjc5OTg5LjE3ODE4NDY2NDc.*_ga_0YHJK3Y10M*czE3ODM3NjYwNTYkbzEzJGcxJHQxNzgzNzY2MDY1JGo1MSRsMCRoMA..)
- https://asccli.sh
- https://github.com/rorkai/App-Store-Connect-CLI
- https://github.com/rorkai/app-store-connect-cli-skills
