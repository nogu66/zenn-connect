---
title: "個人開発したサービスが２日で3 万リーチした話"
emoji: "🚀"
type: "tech" # tech: 技術記事 / idea: アイデア
topics:
  [
    Typescript,
    Next.js,
    TailwindCSS,
    個人開発,
    Vercel,
    Solomaker,
    Dify,
    DeepSeek,
    Bolt,
    さとり構文,
    Cursor,
  ]
published: true
---

## はじめに

こんにちは、[nogu](https://x.com/_nogu66)です。

今回は、私が個人で開発したサービスが、公開からわずか 2 日間で 3 万リーチを達成するという、予想外の出来事についてお話ししたいと思います。

この短い期間で、多くの方々にサービスを知っていただき、実際に利用していただけたことは、私にとって大きな喜びであり、驚きでもありました。

この記事では、その過程や背景、そしてそこから得られた学びについて共有させていただきます。

まずは、以下の投稿をご覧ください。

![Xの投稿](/images/release-satorify-beta-version/post-1.png "@_nogu66の投稿")
https://x.com/_nogu66/status/1878042981997125780?ref_src=twsrc%5Etfw

![Xの投稿](/images/release-satorify-beta-version/post-2.png "@taishi_jadeの投稿")
https://x.com/taishi_jade/status/1878035585673347477?ref_src=twsrc%5Etfw

この投稿はいずれも、私が個人開発したサービスが 2 日で 3 万リーチを達成した際の投稿です。

この記事では、その過程や背景、そしてそこから得られた学びについて共有させていただきます。

**※どうやって、３万リーチしたのかを知りたい方は、この記事の最後をご覧ください。**

## サービスの概要

このサービスは、『さとり構文ジェネレーター』（通称：『Satorify』）[『さとり構文ジェネレーター』（通称：『Satorify』）](https://www.satorify.jp/)という X（旧 Twitter）でバズを連発する「さとり構文を」を誰でも簡単に作成することができるサービスです。[概要](https://www.solomaker.dev/products/069e7ef7-ea4b-46e1-a96e-da3ff1d59686)

「さとり構文」とは X（旧 Twitter）でバズを連発する「さとり([@satori_sz9](https://x.com/satori_sz9))」さんが考案した、短くても効果的な文章構造です。

https://www.satorify.jp/
さとり構文の詳細は[こちら](https://note.com/nogu66/n/n935806694006)でご覧いただけます。

## システム構成と使用技術

このサービスは、ユーザーが入力したテキストを、LLM（大規模言語モデル）を活用してさとり構文風に変換する機能を提供しています。これにより、誰でも簡単にさとり構文調の文章を生成することができます。

また、このサービスは、β 版のリリースということでかなりシンプルな構成となっています。

### システム構成

![システム構成図](/images/release-satorify-beta-version/satorify-architecture-diagram.png "Satorifyのシステム構成")

#### フロントエンド

- Next.js
- TypeScript
- TailwindCSS

#### サーバーサイド(API)

- Dify

#### ホスティング

- Vercel

#### LLM

- DeepSeek V3

### プロトタイピング

- Bolt

### エディタ

- Cursor

## 開発スケジュール

会社に勤めているため、終業時間外の朝昼夜の時間を使って開発しました。

とにかく、早く出すことを優先したため、以下のようなスケジュールで進行しました。

- １日目 要点定義、プロトタイピング
- ２日目 プロンプトエンジニアリング、Dify API 作成
- ３日目 デザイン修正、バクフィックス
- ４日目 デプロイ

## 機能

ベータ版のリリースでは、とくかく動くこと、LLM から精度の高い結果を得ることを優先しました。

そのため、以下のような機能を実装しました。

### ベータ版

- テキスト入力
  - 自由入力
  - 構文タイプの任意選択
- 「さとり構文」の生成
  - 3 つの改善提案
  - コピー機能

![画面](/images/release-satorify-beta-version/satorify-1.png "Satorifyのホーム画面")
![画面](/images/release-satorify-beta-version/satorify-2.png "Satorifyの生成画面")

### リリース版（予定）

- 改善案を 1 つ提示: シンプルかつ具体的な改善案を提供。
- 改善案のコピーおよび SNS 投稿ボタン: 改善案をそのままコピー、SNS でシェア可能。
- ユーザー登録機能: ユーザー体験をカスタマイズ可能。
- プレミアムプランの追加: より便利に使える有料プランが登場。
- プレミアムプラン特典
  - カスタマイズオプション: 構文のスタイルやトーンをユーザーごとに調整可能。
  - 保存と管理: 作成した構文を保存し、後で編集・再利用が可能。
  - 改善案へのフィードバック修正: 改善案を修正して、より良い文章を生成。

## おわりに

このようなサービスが１週間と経たずに、多くの方にリーチできたのは、[Solomaker](https://www.solomaker.dev/)のおかげです。

個人開発者は、アイディア段階でもいいので、ぜひ、[Solomaker](https://www.solomaker.dev/)にプロダクト登録することをオススメします。

ニーズの確認ができたり、早期のリーチができます。また、モチベーションにも継続的に繋がります。

## 宣言

[Satorify](https://satorify.com/)は、現在正式リリース準備中です。近日中にリリース予定ですので、お楽しみに！

ベータ版は以前として利用いただけますので、[Satorify](https://satorify.com/)をご利用ください。

[Satorify](https://satorify.com/)は、SNS の投稿の質を高め、文章を考える時間を最小化してくれるサービスです。SNS マーケにお悩みの方はぜひご活用でください。
