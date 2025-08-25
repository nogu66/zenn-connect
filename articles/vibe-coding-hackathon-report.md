---
title: " イベントレポート：「Vibe Coding: 1-Day Ship Challenge」ハッカソン"
emoji: "🚀"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["ハッカソン", "Shipaton", "AI", "RevenueCat"]
published: true
---

## はじめに
先日、川崎の Fujitsu Uvance Kawasaki Tower で開催された「Vibe Coding: 1-Day Ship Challenge 🚀」というハッカソンに参加してきました。

この記事は、
- **ハッカソンや短期間でのアプリ開発に興味がある方**
- **AIコーディングツール（特にClaude）の活用法を知りたい方**
- **アイデアを素早く形にするプロセスを覗いてみたい方**
に向けて書いています。

わずか4時間という制限の中で、どのようにアイデアを出し、アプリとして形にしていったのか。その具体的なプロセスと、開発を強力にサポートしてくれたAIの活用術について、余すところなくお伝えします。

## 参加したハッカソン「Vibe Coding: 1-Day Ship Challenge 🚀」について
今回参加したのは、その名の通り「バイブスでコーディングする」をテーマにした、1日でプロトタイプを開発しきるイベントです。

![集合写真](/images/vibe-coding-hackathon-report/hackathon-visual.png)

このハッカソンは、RevenueCatが主催する世界的なハッカソン「SHiPATON 2025」の公式日本ハブとしても位置づけられており、当日は多くのエンジニアが集まり、熱気にあふれていました。

![shipaton](/images/vibe-coding-hackathon-report/shipaton.png)
https://www.shipaton.com/

競争よりも「創造と学習」に重きを置いているのが特徴で、和やかな雰囲気の中で、それぞれのアイデアを形にすることに集中できる素晴らしい環境でした。

また、開発タイムの前にはバイブコーディングのハンズオンも行われ、バイブコーディングの概要から効果的な実装方法も学ぶことができました。

### 当日のタイムスケジュール
- **12:30:** 開場
- **13:00:** スタート
    - イベント概要説明
    - 「Shipaton 2025」 & RevenueCat紹介
    - 技術ハンズオン (Expo, Bolt, RevenueCat SDK)
- **14:00:** 開発タイム
    - アイデアをカタチに！メンターがサポートします
- **18:00:** 成果発表会
    - 1チーム3分で、つくったものを自慢しよう！
- **19:00:** オーディエンス賞 投票＆結果発表
- **19:10:** 懇親会
    - 軽食を片手に、参加者やメンターと交流しましょう！
- **21:00:** 終了

## Vibe Codingハンズオン：AIを活用した高速開発の基礎
開発タイムの前に、MeltingHackのSaeさん（[@arventurist](https://x.com/arventurist)）によるVibe Codingのハンズオンが行われました。

https://x.com/arventurist

このセッションでは、4時間のという短い時間でアプリを開発するためのバイブコーディング手法がが紹介されました。ここでは、その内容を詳しくレポートします。

### Vibe Codingとは？
![Vibe Codingって何？](/images/vibe-coding-hackathon-report/IMG_7357.png)

Vibe Codingとは、**AIがコードを生成し、人間がPM（プロダクトマネージャー）の役割を担う**という新しい開発スタイルです。

AIを単なる「コードの執筆者」として活用し、人間は製品マネージャーとして的確な指示を出すことに集中します。これにより、以下のようなメリットが生まれると説明されていました。

- **開発スピードの爆発的向上**: 従来の数週間かかる開発が、わずか数時間で完了する。アイデアから実装までの時間を劇的に短縮できる。
- **コード品質の向上**: AIは最新のベストプラクティスを常に学習しており、一貫性のある高品質なコードを生成してくれる。
- **チーム全体の生産性向上**: 開発者はより創造的な問題解決に集中でき、ビジネス価値の創出に注力できる。

### どのようなツールがあるのか？
ハンズオンでは、Vibe Codingを実現するための様々なツールが紹介されました。

![バイブコーディングツール](/images/vibe-coding-hackathon-report/IMG_7359.jpg)


#### ローコード・ノーコードツール
UIや簡単なロジックをGUIや自然言語で生成するツールです。
- Lovable、v0、Framer、AI Galileoなど

#### フルIDE
AI機能が深く統合された独立した開発環境です。
- Cursor、Windsurf、Kiro、Boltなど

#### 既存のIDEの拡張 or CLI
既存のIDEやターミナルに追加して利用するタイプです。
- GitHub Copilot、Claude、Amazon CodeWhispererなど

#### 完全自立型 Agent
開発タスク全体を自律的に計画・実行するエージェントです。
- Devin、Manus、Devikaなど

### どのように進めるか？
Vibe Codingのプロセスでは、人間は以下の3つのフェーズでAIと協業することをオススメしていました。

![Vibe Codingの３フェーズ](/images/vibe-coding-hackathon-report/IMG_7361.jpg)

#### 1. 調査 & 仕様書作成
- 市場調査からユーザーニーズ分析までを網羅的に実行する。
- アプリの詳細な要件定義、技術仕様書を作成する。

#### 2. 仕様ごとにアプリ実装
- 仕様書のセクション単位で、段階的にアプリを実装していく。
- セクションごとにGitでバージョン管理を行う。

#### 3. 網羅的な実装完了
- 仕様の考慮漏れや不具合を調整する。
- コード負債の削除やコードの品質向上を図る。

### どのように流れを進めるのか？ - 全体像
開発の全体像は、以下の7つのステップで構成されているとのことです。

![Vibe Codingの流れ](/images/vibe-coding-hackathon-report/IMG_7362.jpg)


1.  **アイデアの壁打ち & 市場調査**: AIを「思考パートナー」として活用する。
2.  **網羅的な技術仕様書作成**: AIと一緒に「詳細な仕様書」を作成する。
3.  **0からアプリ実装**: 計画を「セクションごと」にAIに実装させる。
4.  **バックエンド接続**: Firebase/Supabaseなどを接続する。
5.  **課金機能統合**: RevenueCat SDKなどを導入する。
6.  **βアプリ配布**: Expo Application Services (EAS)などを活用する。
7.  **発表 & フィードバック**: 4時間で作り上げたアプリを発表し、フィードバックを得る。

Saeさんからは、以下のようなディレクトリ構成で仕様書を管理する例が紹介されました。
```
project-docs/
├── 00_project_overview/
│ ├── 01_requirements.md
│ ├── 02_product_vision.md
│ └── 03_glossary.md
│
├── 01_architecture/
│ ├── 01_system_overview.md
│ ├── 02_mobile_architecture.md
│ ├── 03_state_management_zustand.md
│ ├── 04_data_flow_and_layers.md
│ ├── 05_navigation_design.md
│ ├── 06_realtime_and_ws.md
│ ├── 07_error_handling_policy.md
│ ├── 08_security_design.md
│ ├── 09_performance_and_optimization.md
│ └── 10_environment_and_secrets.md
│
├── 02_backend_integration/
├── 03_feature_specs/
├── 04_design_system/
├── 05_testing_quality/
├── 06_build_release/
├── 07_operational_runbook/
└── 99_appendix/
```

ハッカソンにおいて、自分もディレクトリ構成でプロジェクト文書を作成したことで、かなりスムーズに開発を進められた実感があります。

## 開発したアプリ：「Climb You」- 登山のようにタスクをこなすアプリ

今回のハッカソンでは、Myon（[@Myon_dev](https://x.com/Myon_dev)）さんのアイデアに全乗っかりさせてもらいました。

そこで、ゲーミフィケーション要素を取り入れたタスク管理アプリを作成しました。（作成したが、完成してはいない）
![Climb You](/images/vibe-coding-hackathon-report/IMG_7382.jpg)


## 開発した方法

### 開発ツール

開発には、AIコーディングアシスタントのClaude CodeとWindsurfを活用しました。

![開発環境](/images/vibe-coding-hackathon-report/dev-env.png)

### プロジェクトドキュメント

アプリの要望をもとに、ハンズオンの章で紹介したディレクトリ構成のドキュメントを作成しました。今後の拡張性も考慮し、現時点では使用しないファイルも仮で配置しています。

このプロジェクトドキュメントは、Claude Codeで作成することで、より詳細な仕様を網羅的に作成することができました。

![project-doc](/images/vibe-coding-hackathon-report/project-doc.png)

### デザインプロセス

デザイン面では、チーム内での認識齟齬をなくすため、早い段階からビジュアルでのすり合わせを重視しました。これによって、迅速にデザインの調整を加えることができました。

また、UI/UXのインスピレーションを得るために[Mobbin](https://mobbin.com/)を参考にし、優れた既存アプリのアイデアを取り入れています。
![project-doc](/images/vibe-coding-hackathon-report/mobbin.png)

Mobbinを参考にすることにより、感覚的であったデザインアイデアがより具体的な仕様にすることができました。

## まとめ

今回のハッカソンでは、残念ながら時間内にアプリを完成させることはできませんでした。
しかし、4時間という極端に短い時間でアイデアを形にするプロセスを経験できたことは、今後の開発に必ず活きてくると確信しています。

また、他のチームが開発したユニークなアプリの数々に大きな刺激を受け、自分自身の新しいアプリのアイデアも浮かびました。
この熱量を冷ますことなく、今回の経験をもとにSHiPATONに提出するアプリを完成させ、一日でも早くリリースを目指したいと思います。

開発の進捗はX（旧Twitter）で「Build in Public」として発信していくので、ぜひチェックしていただけると嬉しいです。

https://x.com/_nogu66/status/1959610244520464552

https://x.com/_nogu66
