---
title: "Gemini APIのGoogle Maps Groundingで位置情報認識AI応答を実現する"
emoji: "🗺️"
type: "tech"
topics: ["gemini", "googleapi", "googlemaps", "ai", "api"]
published: false
---

こんにちは、noguです。

https://x.com/_nogu66

## はじめに

生成AIを活用したアプリケーション開発において、「近くのおすすめのカフェは?」「この場所のレストランの営業時間は?」といった位置情報に関する質問への回答は、常に課題となってきました。一般的なLLMは学習データに基づいた知識しか持たず、最新の店舗情報や正確な地理データにアクセスできないため、曖昧または古い情報を返してしまうことがありました。

この課題を解決するのが、**Google Maps Grounding**です。

### この記事の対象読者

- 位置情報を活用したAIアプリケーションを開発したい方
- Gemini APIを使った実用的なアプリケーションを構築したい方
- Google Mapsのデータと生成AIを組み合わせたサービスに興味がある方

### この記事のスコープ

この記事では、Gemini APIの**Google Maps Grounding**機能の基本的な使い方と実装方法を解説します。網羅的なAPIリファレンスではなく、実践的な実装例とユースケースに焦点を当てています。

### この記事で得られること

- Google Maps Groundingの仕組みと利点の理解
- 実際のコードを使った実装方法
- 位置情報ベースのAIアプリケーションの構築手法
- サービス利用時の注意点とベストプラクティス

## 課題：AIの位置情報応答の精度と鮮度

従来の生成AIモデルには、位置情報に関するクエリに対して以下のような課題がありました。

1. **情報の鮮度**: 学習データの時点での情報しか持たず、最新の店舗情報や営業時間を提供できない
2. **情報の精度**: 具体的な住所、電話番号、評価などの詳細情報が不正確
3. **検証可能性**: 回答のソースが明確でなく、情報の信頼性を確認できない
4. **パーソナライゼーション**: ユーザーの現在地に基づいた適切な提案ができない

これらの課題により、旅行プランナーやローカルガイド、レストラン推薦などのアプリケーション開発が困難でした。

## 解決策：Google Maps Grounding

**Google Maps Grounding**は、Gemini APIの生成能力とGoogle Mapsの豊富かつ最新のデータを統合する機能です。

### 主な特徴

1. **正確な位置情報認識**: 世界中の2億5,000万を超える場所に関するGoogle Mapsの広範なデータベースを活用
2. **パーソナライゼーション**: ユーザーの位置情報に基づいたカスタマイズされた推薦
3. **インタラクティブウィジェット**: Google Mapsウィジェットを埋め込むためのコンテキストトークンを提供
4. **検証可能なソース**: 回答の根拠となるGoogle Mapsのリンクを含む引用情報

## 実装方法

### 基本的な実装

まず、最もシンプルな実装例を見てみましょう。この例では、Google Maps Groundingを有効にして、位置情報に基づいたレストラン推薦を取得します。

```python
from google import genai
from google.genai import types

client = genai.Client()

prompt = "What are the best Italian restaurants within a 15-minute walk from here?"

response = client.models.generate_content(
    model='gemini-2.5-flash-lite',
    contents=prompt,
    config=types.GenerateContentConfig(
        # Google Maps Groundingを有効化
        tools=[types.Tool(google_maps=types.GoogleMaps())],
        # 位置情報を提供（この例はロサンゼルス）
        tool_config=types.ToolConfig(retrieval_config=types.RetrievalConfig(
            lat_lng=types.LatLng(
                latitude=34.050481, longitude=-118.248526))),
    ),
)

print("Generated Response:")
print(response.text)

# ソース情報の取得
if grounding := response.candidates[0].grounding_metadata:
    if grounding.grounding_chunks:
        print('-' * 40)
        print("Sources:")
        for chunk in grounding.grounding_chunks:
            print(f'- [{chunk.maps.title}]({chunk.maps.uri})')
```

#### ポイント解説

1. **ツールの有効化**: `tools=[types.Tool(google_maps=types.GoogleMaps())]` でGoogle Maps Groundingを有効化
2. **位置情報の指定**: `lat_lng` パラメータでユーザーの現在地を指定（オプションだが推奨）
3. **ソース情報**: レスポンスには `grounding_metadata` が含まれ、Google Mapsへのリンクや場所IDが提供される

### JavaScriptでの実装

Node.jsやブラウザ環境での実装例です。

```javascript
import { GoogleGenAI } from "@google/gnai";

const ai = new GoogleGenAI({});

async function generateContentWithMapsGrounding() {
  const response = await ai.models.generateContent({
    model: "gemini-2.5-flash",
    contents: "What are the best Italian restaurants within a 15-minute walk from here?",
    config: {
      // Google Maps Groundingを有効化
      tools: [{ googleMaps: {} }],
      toolConfig: {
        retrievalConfig: {
          // 位置情報を提供（この例はロサンゼルス）
          latLng: {
            latitude: 34.050481,
            longitude: -118.248526,
          },
        },
      },
    },
  });

  console.log("Generated Response:");
  console.log(response.text);

  // ソース情報の取得
  const grounding = response.candidates[0]?.groundingMetadata;
  if (grounding?.groundingChunks) {
    console.log("-".repeat(40));
    console.log("Sources:");
    for (const chunk of grounding.groundingChunks) {
      if (chunk.maps) {
        console.log(`- [${chunk.maps.title}](${chunk.maps.uri})`);
      }
    }
  }
}

generateContentWithMapsGrounding();
```

### Google Mapsウィジェットの表示

より豊かなユーザー体験を提供するため、レスポンスからGoogle Mapsウィジェットをレンダリングできます。

```python
from google import genai
from google.genai import types

client = genai.Client()

prompt = "Plan a day in San Francisco for me. I want to see the Golden Gate Bridge, visit a museum, and have a nice dinner."

response = client.models.generate_content(
    model='gemini-2.5-flash',
    contents=prompt,
    config=types.GenerateContentConfig(
        # ウィジェットを有効化
        tools=[types.Tool(google_maps=types.GoogleMaps(enable_widget=True))],
        tool_config=types.ToolConfig(retrieval_config=types.RetrievalConfig(
            lat_lng=types.LatLng(
                latitude=37.78193, longitude=-122.40476))),
    ),
)

print("Generated Response:")
print(response.text)

# ウィジェット用のコンテキストトークンを取得
if grounding := response.candidates[0].grounding_metadata:
    if widget_token := grounding.google_maps_widget_context_token:
        print('-' * 40)
        print(f'<gmp-place-contextual context-token="{widget_token}"></gmp-place-contextual>')
```

取得したトークンを使って、HTMLで以下のようにウィジェットを表示できます。

```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
<gmp-place-contextual context-token="取得したトークン"></gmp-place-contextual>
```

## 実践的なユースケース

### 1. 場所に関する詳細な質問への対応

特定の場所について、Google Mapsのレビューやデータに基づいた詳細な回答を取得できます。

```python
prompt = "Is there a cafe near the corner of 1st and Main that has outdoor seating?"

response = client.models.generate_content(
    model='gemini-2.5-flash-lite',
    contents=prompt,
    config=types.GenerateContentConfig(
        tools=[types.Tool(google_maps=types.GoogleMaps())],
        tool_config=types.ToolConfig(retrieval_config=types.RetrievalConfig(
            lat_lng=types.LatLng(
                latitude=34.050481, longitude=-118.248526))),
    ),
)
```

### 2. パーソナライズされた推薦

ユーザーの好みと位置情報に基づいた、カスタマイズされた推薦が可能です。

```python
prompt = "Which family-friendly restaurants near here have the best playground reviews?"

response = client.models.generate_content(
    model='gemini-2.5-flash',
    contents=prompt,
    config=types.GenerateContentConfig(
        tools=[types.Tool(google_maps=types.GoogleMaps())],
        tool_config=types.ToolConfig(retrieval_config=types.RetrievalConfig(
            lat_lng=types.LatLng(
                latitude=30.2672, longitude=-97.7431))),  # Austin, TX
    ),
)
```

### 3. 旅行プランの作成支援

複数の場所を組み合わせた、実用的な旅行プランを生成できます。

```python
prompt = "Plan a day in San Francisco for me. I want to see the Golden Gate Bridge, visit a museum, and have a nice dinner."

response = client.models.generate_content(
    model='gemini-2.5-flash',
    contents=prompt,
    config=types.GenerateContentConfig(
        tools=[types.Tool(google_maps=types.GoogleMaps(enable_widget=True))],
        tool_config=types.ToolConfig(retrieval_config=types.RetrievalConfig(
            lat_lng=types.LatLng(
                latitude=37.78193, longitude=-122.40476))),
    ),
)
```

## レスポンスの構造を理解する

Google Maps Groundingを使用すると、レスポンスに `groundingMetadata` フィールドが追加されます。

```json
{
  "candidates": [
    {
      "content": {
        "parts": [
          {
            "text": "CanteenM is an American restaurant with..."
          }
        ],
        "role": "model"
      },
      "groundingMetadata": {
        "groundingChunks": [
          {
            "maps": {
              "uri": "https://maps.google.com/?cid=...",
              "title": "Heaven on 7th Marketplace",
              "placeId": "places/ChIJ0-zA1vBZwokRon0fGj-6z7U"
            }
          }
        ],
        "groundingSupports": [
          {
            "segment": {
              "startIndex": 0,
              "endIndex": 79,
              "text": "CanteenM is an American restaurant..."
            },
            "groundingChunkIndices": [0]
          }
        ],
        "googleMapsWidgetContextToken": "widgetcontent/..."
      }
    }
  ]
}
```

### 主要なフィールド

- **groundingChunks**: Google Mapsのソース情報（URL、タイトル、プレイスID）
- **groundingSupports**: テキスト範囲とソースの対応関係（インライン引用に使用）
- **googleMapsWidgetContextToken**: Google Mapsウィジェットをレンダリングするためのトークン

## サービス利用時の注意点

### 1. ソースの帰属表示

Google Mapsのデータを使用する場合、必ず適切な帰属表示が必要です。

- Google Mapsのソースは、生成コンテンツの直後に配置
- ソースのタイトルとGoogle Mapsへのリンクを表示
- "Google Maps"のテキストは変更・翻訳不可

```html
<div class="GMP-attribution">
  <a href="ソースのURI">ソースのタイトル</a> - Google Maps
</div>
```

### 2. 禁止地域

以下の地域では、Google Maps Groundingを使用したアプリケーションの配布・販売が禁止されています。

- 中国、クリミア、キューバ、イラン、北朝鮮、シリア、ベトナムなど

### 3. 料金

- **$25 / 1,000件**のグラウンディングされたプロンプト
- 無料枠：1日あたり最大500件のリクエスト
- 通常のGemini APIの入出力トークン料金も別途発生

## ベストプラクティス

### 1. 位置情報は常に提供する

ユーザーの位置情報がわかっている場合は、必ず `latLng` パラメータで指定しましょう。これにより、最も関連性の高いパーソナライズされた結果が得られます。

```python
tool_config=types.ToolConfig(
    retrieval_config=types.RetrievalConfig(
        lat_lng=types.LatLng(latitude=35.6812, longitude=139.7671)  # 東京
    )
)
```

### 2. 必要な場合のみ有効化

Google Maps Groundingはデフォルトでオフです。パフォーマンスとコストを最適化するため、明確な地理的コンテキストがある場合のみ有効化しましょう。

### 3. ウィジェットで視覚的な体験を提供

可能な限り `enable_widget=True` を設定し、ユーザーに視覚的なGoogle Mapsの情報を提供しましょう。

### 4. レイテンシのモニタリング

会話型アプリケーションでは、グラウンディングによるレイテンシ増加に注意し、P95レイテンシをモニタリングしてください。

## 制限事項

- **モデルサポート**: Gemini 2.5 Flash-Lite、2.5 Pro、2.5 Flash、2.0 Flashのみ対応
- **マルチモーダル**: 現在、テキストとコンテキストマップウィジェット以外の入出力は未対応
- **デフォルト状態**: デフォルトではオフなので、明示的に有効化が必要

## おわりに

Google Maps Groundingは、位置情報を活用したAIアプリケーション開発における大きな課題を解決する強力な機能です。

### この記事のまとめ

- Google Maps Groundingは、Gemini APIとGoogle Mapsデータを統合し、正確な位置情報認識応答を実現
- 実装は簡単で、`tools` パラメータに `googleMaps` を指定するだけ
- ユーザーの位置情報を提供することで、パーソナライズされた推薦が可能
- 適切なソース帰属表示と料金体系の理解が重要

### 今後の展望

この機能を活用することで、以下のようなアプリケーションの開発が現実的になります。

- 会話型の旅行プランナー
- 位置情報ベースのパーソナルアシスタント
- ローカルビジネス向けの顧客サポートチャットボット
- フードデリバリーサービスのインテリジェントな推薦システム

位置情報とAIの組み合わせは、今後さらに進化していくでしょう。Google Maps Groundingは、その第一歩として非常に有望な選択肢です。

---

この記事が役に立ったら、Xをフォローしていただけると嬉しいです!

https://x.com/_nogu66

## 参考リンク

- [Google Maps Grounding 公式ドキュメント](https://ai.google.dev/gemini-api/docs/maps-grounding)
- [Gemini API 料金ページ](https://ai.google.dev/gemini-api/docs/pricing)
- [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript)
