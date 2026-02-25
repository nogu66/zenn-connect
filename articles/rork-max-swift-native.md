---
title: "Rork Max登場 — ブラウザだけでSwifアプリを作れる時代が来た"
emoji: "🍎"
type: "tech"
topics: ["Rork", "swift", "ios", "ai", "アプリ開発"]
published: true
---

## はじめに

こんにちは、noguです。

本記事は以下の記事の続編です。

https://zenn.dev/nogu66/articles/rork-introduction

前回の記事ではRorkの紹介をしました。今回は、2026年2月に登場した**Rork Max**について紹介します。

これまでRorkは、React Native / Expoベースでクロスプラットフォームアプリを生成していました。

しかしRork Maxは、その常識を根本から覆しました。**ネイティブSwiftコードを直接生成する**のです。

ブラウザだけで、Xcodeなしで、SwiftUIのiPhoneアプリを作って実機にインストールし、App Storeに申請できる。これは「便利ツールが出た」という話ではなく、**iOS開発の構造そのものが変わった**という話です。

### この記事の対象読者

- iOSアプリを作りたいけどMacやXcodeの環境構築がハードルになっている方
- Swiftネイティブの品質で、もっと速く開発したい方
- 前回のRork紹介記事を読んで、続報が気になっていた方
- 開発体験の劇的な変化を感じたい人

### この記事のスコープ

#### **扱うこと**
- Rork Maxとは何か
- 従来のRork（React Native）との違い
- 技術的な仕組み（クラウドMac、ストリーミング）
- 対応機能の幅広さ
- App Store申請フロー

#### **扱わないこと**
- Rorkの基本的な使い方（前回記事で対応）
- Agent Skillsの詳細（別記事で対応）
- 料金プランの詳細

### この記事を読むと得られるもの

- Rork Maxの全体像と「**何がすごいのか**」の理解
- 従来のiOS開発フローとの違いの把握
- 自分のユースケースに合うかの判断材料


## Rork Maxとは

**Rork Max**は、自然言語の指示から**ネイティブSwiftコード**を生成し、Webブラウザ上でiOSアプリの開発・テスト・公開までを完結させるプラットフォームRorkに登場した**新機能**です。

![Rork Max トップページ](/images/rork-max/hero.png)

https://rork.com/?ref=nogu

AIモデルには**Claude Opus 4.6**を搭載し、Rorkエージェントによる自律的なコーディングを実現しています。

従来のRorkがReact Native / Expoベースだったのに対し、Rork Maxは**SwiftUI**でコードを生成します。これにより、Appleプラットフォームの性能をフルに引き出すネイティブアプリが作れるようになりました。

| 項目 | Rork（従来） | Rork Max |
| :--- | :--- | :--- |
| **生成コード** | React Native / Expo | ネイティブSwift（SwiftUI） |
| **対応プラットフォーム** | iOS & Android | Apple全般（iOS, iPadOS, watchOS, tvOS, visionOS） |
| **プレビュー** | Expo Goで実機確認 | クラウドiOSシミュレーターをブラウザにストリーミング |
| **実機インストール** | QRコード経由 | ワンクリック |
| **App Store申請** | Rorkから申請可能 | 2クリックで申請完了 |
| **AIモデル** | 複数モデル選択可 | Claude Opus 4.6（２回目の入力以降は数モデル選択可） |


## Rork Maxの始め方

### 無料版でのトグル有効化

Rork Maxは、**期間限定で無料プランでも試すことができます(2026年2月25日現在)**。**ただし、デフォルトでは従来のReact Nativeモードになっているため、まずMax機能を有効化する必要があります**。

プロンプト入力欄の左下にあるトグルをクリックして、**「Rork Max」の状態（オレンジ色）にする**だけでOKです。

#### **オン（Rork Maxモード）**

![Rork Maxトグル オン](/images/rork-max/toggle-on.png)

#### **オフ（通常のRorkモード）**

![Rork Maxトグル オフ](/images/rork-max/toggle-off.png)


オンにすると、ボタンがオレンジ色に光り「**Rork Max」**の表示に変わります。右側の `5/5` は**無料プランで残っているMaxの使用回数**です。

> **注意**: 無料プランではMaxモードを**1日5回**まで使用できます（2026年2月25日現在）。Maxモードはクラウドのコンピューティングリソースを多く使用するため、使い切ったら翌日にリセットされます。

### 基本的な使い方

1. **[Rork公式サイト](https://rork.com/?ref=nogu) にアクセス**し、アカウントを作成またはログイン

![Rork公式サイト](/images/rork-max/home.png)

2. **新規プロジェクトを作成**し、「Rork Max」トグルがオンになっていることを確認

![Rork Max](/images/rork-max/toggle-on.png)

3. **自然言語でアプリの内容を入力**する（日本語でもOK）

![入力](/images/rork-max/toggle-on.png)
```
例：「毎日の水分摂取量を記録するアプリ。ホーム画面にウィジェットも追加したい」

```

4. **クラウド上でビルドが始まる**。完了するとブラウザ内でiOSシミュレーターが起動

![プレビュー](/images/rork-max/preview.png)

5. **動作確認**しながらチャットで修正を指示


6. 実機インストールは**iPhoneをUSB接続してワンクリック**

![Rork Max](/images/rork-max/to-iphone.png)

7. App Store申請は「**Publish**」を2クリック　

![App Store申請](/images/rork-max/publish.png)

## なぜ「ネイティブSwift」なのか

これまでのAIアプリビルダーの多くは、React NativeやExpoを採用してきました。「一つのコードでiOSとAndroidの両方に対応できる」というメリットがある一方で、以下のような課題がありました。

- **パフォーマンスの低下**
- **OS固有の最新機能への対応の遅れ**
- **「ネイティブアプリならでは」の操作感の喪失**
- **「ネイティブアプリ」では簡単にできることができない**

Hacker Newsでも「**React Nativeベースのツールでは、洗練されたネイティブ感のあるデザインが必要になった瞬間に壁にぶつかる**」という指摘があります。Appleの審査でも、Expoラッパー的なアプリは好まれない傾向にあります。

Rork Maxは、この課題に対して「**SwiftUIでネイティブコードを直接生成する**」という、技術的に最も困難な道を選びました。


## 対応プラットフォームと機能

**Rork Maxが対応する範囲は驚くほど広いです。**

### すべてのAppleプラットフォーム

iPhone、iPad、Apple Watch、Apple TV、Vision Pro。Rork Maxはあらゆるスクリーンに対応したアプリを構築できます。

![対応プラットフォーム](/images/rork-max/platform.png)

### iPhoneでできることは、全部できる

![機能一覧](/images/rork-max/features-grid.png)

対応機能の一覧です。

| カテゴリ | 機能 | 概要 |
| :--- | :--- | :--- |
| **UI拡張** | Widget | ホーム画面・ロック画面にウィジェット表示 |
| **UI拡張** | Dynamic Island | リアルタイム情報の表示 |
| **UI拡張** | Live Activities | ライブアクティビティ |
| **AR/3D** | ARKit / LiDAR | 現実空間に3Dオブジェクトを配置 |
| **AR/3D** | 3Dゲーム | SceneKit / Metal対応、60fpsで動作 |
| **カメラ** | Camera & Vision AI | ボディトラッキング、顔検出、Snapchat風レンズ |
| **AI連携** | Siri Apps | Siriインテント統合 |
| **メッセージ** | iMessage Apps | ステッカー、マルチプレイヤーゲーム |
| **ヘルスケア** | HealthKit | ヘルスケアデータ連携 |
| **スマートホーム** | HomeKit | スマートデバイス制御 |
| **その他** | NFC / App Clips / Background Tasks | ハードウェア・システム機能 |

### ゲーム開発にも対応

App Storeで最大のカテゴリであるゲームも、Rork Maxで作れます。

![ゲーム開発](/images/rork-max/games.png)

ARKit、SceneKit、Metalにフルアクセスし、60fpsでネイティブ動作する3Dゲームやポケモンgo風のARゲームまで構築可能です。


## 従来のiOS開発との比較

**Rork Maxは単なる便利ツールにとどまらず、開発フロー全体を変えうるプロットフォームです。**

### 従来のiOS開発

1. MacBookを用意する
2. Xcodeをインストールする
3. Apple Developer Program（年間$99）に登録する
4. Provisioning Profileを設定する
5. コードを書く
6. ビルド・テスト
7. App Store Connectで申請

### Rork Maxの場合

**Rork Maxはこれを全部消しました。**

1. プロンプトを書く
2. クラウドのMacがSwiftUIでコードを生成
3. 本物のiOSシミュレーターがブラウザにストリーミング
4. iPhoneに接続してワンクリックでインストール
5. Apple Developer Program（年間$99）に登録する
5. 2クリックでApp Store申請完了

| 項目 | 従来のiOS開発 | Rork Max |
| :--- | :--- | :--- |
| **必要なもの** | Mac + Xcode + Developer Account | ブラウザ + Developer Account|
| **環境構築** | 数時間 | 0分 |
| **リリースまで** | 数日〜数週間 | 数分 |


## 技術的な仕組み

Rork Maxの仕組みは技術的にも非常に面白いです。

### クラウドMac

**Rorkは数百台のMacを24時間稼働させているそうです。これにより、ユーザーがメッセージを送った瞬間、1台のMacが割り当てられ、XcodeとiOS SDKがロードされた状態で待機しています。**

AIエージェントがSwiftUIでアプリを書き、ビルドし、エラーを読み、修正し、再ビルドする。**iOS開発者が毎日やっていることと同じサイクルを、数分で完了します。**

### iOSシミュレーターのストリーミング

![ストリーミング](/images/rork-max/streaming.png)

プレビューは、**クラウド上のMacで動作する本物のiOSシミュレーター**です。FaceTimeと同じ低遅延プロトコルでブラウザにストリーミングされます。タッチ入力が数ミリ秒でシミュレーターに届くため、すべてのアニメーション、すべてのジェスチャーが、本物のiPhoneとまったく同じ挙動で動作します。

> ブラウザからネイティブiOSアプリを作るのは不可能とされてきました。コンパイルにはMac、テストにはApple純正のSimulator、配布にはXcodeが必要です。だから私たちはAppleの開発スタックを全部クラウドに移しました。あなたが意識する必要はありません。


## App Store申請

![App Store申請](/images/rork-max/editor-preview.png)

App Storeへの申請もRorkから直接できます。

- **ワンクリック申請**: Apple IDで一度サインインすれば、それ以降はワンクリックで申請可能
- **TestFlight対応**: テスターをメールで招待し、ビルド状況をリアルタイムで追跡できる
- **TestFlightリンク**: 準備完了時にリンクが自動生成される

App Store ConnectやProvisioning Profileの煩雑な設定は一切不要です。


## 原動力は「Claude Opus 4.6」

Rork Maxの開発能力を支えているのが、Anthropic社の最新AIモデル**Claude Opus 4.6**です。

Opus 4.6は特にコーディング能力において飛躍的な進化を遂げています。

- **高度な計画能力と自己修正**: 複雑なタスクを分解し、自らエラーを修正しながら開発を進める
- **大規模コンテキスト**: 100万トークンのコンテキストウィンドウで巨大なプロジェクト構造を把握
- **エージェント機能**: コード生成だけでなく、ツール呼び出しや外部サービス連携を自律的に実行

Swiftは言語仕様が複雑で、バージョンごとの変更も大きいです。Opus 4.6の高いコーディング能力があるからこそ、モダンなSwiftUIコードの安定した生成が可能になっています。


## 私がRork Maxに注目する理由

前回の記事でRorkを紹介して以来、このプラットフォームの進化を追い続けてきました。Rork MaxがSwiftネイティブに踏み込んだことは、単なるアップデートではなく**パラダイムシフト**だと感じています。

### React Nativeの壁を超えた

これまでのAIアプリビルダーは、どれもReact Nativeの枠内での競争でした。Rork Maxはその枠を壊し、**ネイティブSwiftという新しい土俵**を作りました。

### 参入障壁が消えた

従来のiOS開発は「Mac + Xcode」という高い参入障壁がありました。Rork Maxは、これらをすべてゼロにしました。**必要なのはブラウザだけ**です。

### Agent Skillsとの相乗効果

前回の記事や[Skills-Orchestration Developmentの記事](https://zenn.dev/nogu66/articles/skill-orchestration-development)で紹介したように、RorkはAgent Skillsを積極的に活用しています。SwiftUIに対しても同様のSkillsシステムが機能しているおり、ネイティブ開発においても品質の均質化が期待できます。

### Rorkのエンジニアスキルが高い

Rorkは自社でエージェントを開発しています。それを加味すると、スキルオーケストレーションをはじめとしたエージェントの優秀さ、すばやい機能追加などメンバーのスキルが高いことを感じる場面が多々あります。

![投稿](/images/rork-introduction/post.png)

また、Founding Engineerとして、ccusageの開発者 ryoppippiさんが入社されていることも驚きの1つではあります。彼によって、かなり日本人フレンドリーなプラットフォームになっていることはいうまでもありません。

https://x.com/ryoppippi/status/2026493790232654220?s=20



## まとめ

Rork Maxは、iOS開発の常識を覆す存在です。

- **ネイティブSwiftコード**を直接生成する、Web上初のSwiftアプリビルダー
- **すべてのAppleプラットフォーム**に対応（iPhone, iPad, Watch, TV, Vision Pro）
- **クラウドMac + FaceTimeプロトコル**による本物のiOSシミュレーターのストリーミング
- **環境構築0分、必要なのはブラウザだけ**
- **2クリックでApp Store申請**

これは「便利なツールが出た」という話ではありません。**iOS開発の構造が変わった**という話です。

アイデアはあるけれど技術的な壁に阻まれてきた方、MacBookなしでiOSアプリを作りたい方にとって、Rork Maxはまさに黒船です。



### **この記事が参考になったら、ぜひXでフォローしてください！**
https://x.com/_nogu66

質問や感想があれば、お気軽にDMやリプライで教えてください。


## 参考リンク

- [Rork Max公式サイト](https://rork.com/max)
- [Rork公式サイト](https://rork.com/?ref=nogu)
- [お前はまだRorkを知らない（前回記事）](https://zenn.dev/nogu66/articles/rork-introduction)
- [Skills-Orchestration Developmentのすゝめ](https://zenn.dev/nogu66/articles/skill-orchestration-development)
- [Hacker News: Every AI app builder outputs React Native. I chose real Swift instead.](https://news.ycombinator.com/item?id=47071286)
- [Anthropic: Introducing Claude Opus 4.6](https://www.anthropic.com/news/claude-opus-4-6)
