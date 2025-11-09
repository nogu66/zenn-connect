---
title: "Gemini APIの公式ドキュメント「Googleマップによるグラウンディング」を読む"
emoji: "🔍"
type: "tech"
topics: ["gemini", "googleapi", "googlemaps", "ai", "api"]
published: true
---

## はじめに

先日、Gemini APIに「**Google Maps Groundingによる豊富な地理空間データ**」というツールが追加されました。

### デモ動画
https://x.com/_nogu66/status/1986704742916235283?s=20

### デモアプリ
https://aistudio.google.com/apps/bundled/chat_with_maps_live?showPreview=true&showAssistant=true&utm_source=AISgaias&utm_medium=email&utm_campaign=API-tools

### この機能を使うことで出来るようになること
この機能を使うことで、以下のようなアプリの作成が可能になります。

1. **会話型の旅行プランナー**: 「サンフランシスコで1日観光したい。ゴールデンゲートブリッジを見て、美術館に寄って、美味しいディナーを食べたい」といった自然な会話から、Google Mapsの最新データに基づいた実用的な旅行プランを生成

2. **位置情報ベースのパーソナルアシスタント**: 「近くのイタリアンで、15分以内に歩いて行けるおすすめは？」といった質問に、現在地を考慮した正確な回答を提供

3. **ローカルビジネス向けの顧客サポートチャットボット**: 「この店の営業時間は？」「駐車場はある？」といった質問に、Google Mapsの最新情報を基に正確に回答

4. **フードデリバリーサービスのインテリジェントな推薦システム**: ユーザーの好みと位置情報を組み合わせて、最適なレストランを推薦

5. **場所に関する詳細な質問への対応**: 「1番通りとメイン通りの角にある、屋外席があるカフェはある？」といった具体的な質問に、Google Mapsのレビューやデータに基づいて回答

このように、位置情報とAIを組み合わせることで、これまで難しかった「正確で最新の地理情報を活用したアプリケーション」が簡単に構築できるようになりそうです。

この記事では、そのために必要な**Google Maps Groundingの仕組みと実装方法**を、公式ドキュメントを読みながら解説していきます。




### この記事の対象読者

- Gemini APIの新機能を知りたい人
- GoogleマップへのGemini統合に興味がある人
- AI×地図に興味がある人

### この記事のスコープ

この記事では、[公式ドキュメント](https://ai.google.dev/gemini-api/docs/maps-grounding?utm_source=AISgaias&utm_medium=email&utm_campaign=API-tools&hl=ja)の内容を解説します。

具体的には以下の内容を扱います：
- Google Maps Groundingの概要と仕組み
- 実装方法（JavaScript/Python）
- レスポンス構造の理解
- ベストプラクティスと注意点
- 料金と制限事項

一方で、詳細なAPIリファレンスや周辺知識（Google Maps APIの詳細設定など）は需要があれば別記事として扱います。

### この記事で得られること

- Google Maps Groundingの機能と仕組みの理解
- 実装時の具体的なコード例とポイント
- サービス利用時の注意点とベストプラクティス

## 基礎となる知識

### 概要
まず、Googleマップグラウンディングの概要は以下のとおりです。（公式ドキュメントより引用）

> Google マップによるグラウンディングは、Gemini の生成機能と Google マップの豊富で事実に基づいた最新のデータを関連付けます。この機能により、デベロッパーは位置情報を認識する機能をアプリに簡単に組み込むことができます。ユーザーのクエリにマップデータに関連するコンテキストが含まれている場合、Gemini モデルは Google マップを活用して、ユーザーが指定した場所や一般的なエリアに関連する、事実に基づいた最新の回答を提供します。
> - 正確な位置情報認識応答: Google マップの広範で最新のデータを活用して、地理的に特定のクエリに対応します。
> - パーソナライズの強化: ユーザーが提供した位置情報に基づいて、おすすめ情報や情報をカスタマイズします。
> - コンテキスト情報とウィジェット: 生成されたコンテンツとともにインタラクティブな Google マップ ウィジェットをレンダリングするためのコンテキスト トークン。- (公式ドキュメントより引用)

まとめると、Geminiの生成機能とGoogleマップの豊富なデータを組み合わせて、正確でパーソナライズされたデータを生成できるということです。また、地図としてのGoogleマップを描画するために必要な情報を合わせて取得することができます。

### Googleマップによるグラウンディングの仕組み

Google マップとのグラウンディングでは、Maps API を情報源として使用して、Gemini API を Google Geo エコシステムと統合しています。

ユーザーの入力に**地理に関するコンテキスト**が含まれている場合、**Gemini モデルは Google マップによるグラウンディング ツールを呼び出すことができます。**（例: 「近くのカフェ」、「サンフランシスコの美術館」など）

モデルは、提供された場所に関連する Google マップのデータに基づいて回答を生成できます。

![フローチャート](/images/read-gemini-api-aps-grounding/flowchart.png)

1. **ユーザーのクエリ**: ユーザーがアプリケーションにクエリを送信します。このクエリには、地理的コンテキストが含まれる可能性があります（例: 「近くのカフェ」、「サンフランシスコの美術館」など）。

2. **ツールの呼び出し**: Gemini モデルは、地理的な意図を認識して、Google マップのグラウンディング ツールを呼び出します。このツールには、ユーザーの latitude と longitude をオプションで指定できます。このツールはテキスト検索ツールで、Google マップでの検索と同様の動作をします。つまり、ローカル クエリ（「近くの」）では座標が使用されますが、特定のクエリやローカル以外のクエリでは、明示的な位置情報の影響を受けにくいです。

3. **データ取得**: Grounding with Google Maps サービスは、関連情報（場所、レビュー、写真、住所、営業時間など）について Google マップにクエリを送信します。

4. **グラウンディングされた生成**: 取得されたマップデータは、Gemini モデルの回答に反映され、事実の正確性と関連性が確保されます。

5. **回答とウィジェット トークン**: モデルは、Google マップのソースへの引用を含むテキスト レスポンスを返します。必要に応じて、API レスポンスに `google_maps_widget_context_token` を含めることもできます。これにより、デベロッパーはコンテキストに応じた Google マップ ウィジェットをアプリケーションにレンダリングして、視覚的な操作を実現できます。

## サンプル

### 実装全体
実装全体はこのようになります。
```js
import { GoogleGenAI } from "@google/gnai";

const ai = new GoogleGenAI({});

async function generateContentWithMapsGrounding() {
  const response = await ai.models.generateContent({
    model: "gemini-2.5-flash",
    contents: "What are the best Italian restaurants within a 15-minute walk from here?",
    config: {
      // Google マップで位置情報サービスをオンにする
      tools: [{ googleMaps: {} }],
      toolConfig: {
        retrievalConfig: {
          // 必要に応じて関連する場所のコンテキストを提供してください（これはロサンゼルスです）
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

### Googleマップツールの有効化

これはあくまでも**Geminiのツール**なので、実際にツールを呼び出しているのはこの部分です。

```js
// Google マップで位置情報サービスをオンにする
tools: [{ googleMaps: {} }],
toolConfig: {
  retrievalConfig: {
    // 必要に応じて関連する場所のコンテキストを提供してください（これはロサンゼルスです）
    latLng: {
      latitude: 34.050481,
      longitude: -118.248526,
    },
  },
},
```

#### ポイント解説

1. **`tools: [{ googleMaps: {} }]`**: Google Maps Groundingツールを有効化します。デフォルトではオフなので、明示的に有効化する必要があります。

2. **`toolConfig.retrievalConfig.latLng`**: ユーザーの位置情報をオプションで指定できます。指定することで、現在地等などのパーソナライズされた結果が得られます。

3. **ウィジェットの有効化**: より豊かなユーザー体験のため、ウィジェットを有効化することもできます。

```js
tools: [{ googleMaps: { enableWidget: true } }],
```

### レスポンス構造の理解

Google Maps Groundingを使用すると、レスポンスに `groundingMetadata` フィールドが追加されます。このフィールドには以下の情報が含まれます：

- **`groundingChunks`**: Google Mapsのソース情報（URL、タイトル、プレイスID）
- **`groundingSupports`**: テキスト範囲とソースの対応関係（インライン引用に使用）
- **`googleMapsWidgetContextToken`**: Google Mapsウィジェットをレンダリングするためのトークン（ウィジェットが有効な場合）

レスポンスの構造例：

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

### Google Mapsウィジェットの表示

レスポンスから取得した `googleMapsWidgetContextToken` を使用して、Google Mapsウィジェットを表示できます。

```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
<gmp-place-contextual context-token="取得したトークン"></gmp-place-contextual>
```

詳細については、[Maps JavaScript API を読み込む](https://developers.google.com/maps/documentation/javascript/load-maps-js-api?hl=ja)のドキュメントを参照してください。

## 公式ドキュメントから読み取れる重要なポイント

### ベストプラクティス

公式ドキュメントでは、以下のベストプラクティスが推奨されています。

#### 1. ソースの帰属表示

Google Mapsのデータを使用する場合、必ず適切な帰属表示が必要です。

- Google Mapsのソースは、生成コンテンツの直後に配置
- ソースのタイトルとGoogle Mapsへのリンクを表示
- "Google Maps"のテキストは変更・翻訳不可

```html
<div class="GMP-attribution">
  <a href="ソースのURI">ソースのタイトル</a> - Google Maps
</div>
```

#### 2. 位置情報の提供

ユーザーの位置情報がわかっている場合は、必ず `latLng` パラメータで指定しましょう。これにより、最も関連性の高いパーソナライズされた結果が得られます。

#### 3. 必要な場合のみ有効化

Google Maps Groundingはデフォルトでオフです。パフォーマンスとコストを最適化するため、明確な地理的コンテキストがある場合のみ有効化しましょう。

#### 4. エンドユーザーへの通知

Google Mapsのデータがクエリの回答に使用されていることを、特にツールが有効になっている場合は、エンドユーザーに明確に通知します。

#### 5. レイテンシのモニタリング

会話型アプリケーションでは、グラウンディングされたレスポンスのP95レイテンシが許容範囲内のしきい値に収まるようにして、スムーズなユーザーエクスペリエンスを維持します。

### 制限事項

公式ドキュメントでは、以下の制限事項が明記されています。

#### 1. 地理的範囲

現在、Google Mapsによるグラウンディングはグローバルで利用可能です。

#### 2. モデルのサポート

Google Mapsによるグラウンディングをサポートしているのは、以下の特定のGeminiモデルのみです：

- Gemini 2.5 Flash-Lite
- Gemini 2.5 Pro
- Gemini 2.5 Flash
- Gemini 2.0 Flash（2.0 Flash Liteは除く）

#### 3. マルチモーダル入力/出力

Google Mapsを使用したグラウンディングは、現在、テキストとコンテキストマップウィジェット以外のマルチモーダル入力または出力をサポートしていません。

#### 4. デフォルトの状態

Google Mapsによるグラウンディングツールはデフォルトでオフになっています。APIリクエストで明示的に有効にする必要があります。

#### 5. 禁止地域

以下の地域では、Google Maps Groundingを使用したアプリケーションの配布・販売が禁止されています：

- 中国、クリミア、キューバ、イラン、北朝鮮、シリア、ベトナムなど

### 料金とレート制限

Google Mapsによるグラウンディングの料金は、クエリに基づいています。

- **$25 / 1,000件**のグラウンディングされたプロンプト
- **無料枠**: 1日あたり最大500件のリクエスト

リクエストが割り当てにカウントされるのは、プロンプトが少なくとも1つのGoogle Mapsのグラウンディングされた結果（少なくとも1つのGoogle Mapsのソースを含む結果）を正常に返した場合のみです。

1つのリクエストからGoogle Mapsに複数のクエリが送信された場合、レート制限に対して1つのリクエストとしてカウントされます。

**注**: 通常、Google Mapsを使用したグラウンディングの割り当ては、基盤となるGeminiモデルのレート制限と一致します。

通常のGemini APIの入出力トークン料金も別途発生するため、コスト管理には注意が必要です。


## まとめ

この記事では、Gemini APIのGoogle Maps Grounding機能について、公式ドキュメントの内容を解説しました。

### 主なポイント

1. **機能の概要**: Geminiの生成機能とGoogle Mapsの豊富なデータを統合し、正確でパーソナライズされた位置情報認識応答を実現

2. **実装の簡単さ**: `tools: [{ googleMaps: {} }]` を指定するだけで有効化でき、位置情報を `latLng` で指定することでパーソナライズされた結果が得られる

3. **レスポンス構造**: `groundingMetadata` にソース情報やウィジェットトークンが含まれ、検証可能な回答と視覚的な体験を提供

4. **注意点**: 
   - 適切なソース帰属表示が必要
   - 料金は$25/1,000件（無料枠500件/日）
   - 特定のモデルのみサポート
   - 禁止地域での配布・販売は不可

5. **ベストプラクティス**: 
   - 位置情報は常に提供する
   - 必要な場合のみ有効化
   - エンドユーザーに通知
   - レイテンシをモニタリング

Google Maps Groundingは、位置情報を活用したAIアプリケーション開発における大きな課題を解決する強力な機能です。位置情報とAIの組み合わせは、今後さらに進化していくでしょう。

~~AI×地図について、1年半ほど前から調査と検討をしていた分野です。そのため、個人的には、Googleマップにやられたら...~~

## Xのフォローしてください
Xでも発信していますので、フォローしていただけるとうれしいです！
https://x.com/_nogu66

## 参考文献

- [Google Maps Grounding 公式ドキュメント](https://ai.google.dev/gemini-api/docs/maps-grounding?utm_source=AISgaias&utm_medium=email&utm_campaign=API-tools&hl=ja)
- [デモアプリ](https://aistudio.google.com/apps/bundled/chat_with_maps_live?showPreview=true&showAssistant=true&utm_source=AISgaias&utm_medium=email&utm_campaign=API-tools)
