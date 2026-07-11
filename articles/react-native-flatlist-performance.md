---
title: "React NativeのFlatListが重い問題をパフォーマンス最適化で解決した"
emoji: "⚡"
type: "tech"
topics: ["reactnative", "flatlist", "パフォーマンス", "モバイル開発"]
published: false
---

こんにちは、noguです。

## はじめに

**この記事の対象読者**
- React NativeでFlatListを使っているが、スクロールがカクつく問題に悩んでいる人
- リスト表示のパフォーマンスを改善したい人
- React Nativeのレンダリングの仕組みを理解したい人

**この記事でわかること**
- FlatListがカクつく原因
- パフォーマンス改善に効く具体的なプロパティと設定
- `memo`・`useCallback`を使ったコンポーネント最適化の方法

**この記事で扱わないこと**
- FlashList（Shopify製の高性能リスト）への移行方法
- React Nativeのネイティブモジュール最適化

この記事を最後まで読むことで、FlatListのカクつきを解消し、滑らかなスクロール体験をユーザーに届けられるようになります。

---

## 「スクロールするたびにフレームが落ちる」

こんな経験はありませんか?

商品一覧や投稿フィードをFlatListで実装したとき、スクロールするたびに画面がカクつく。デバッグしてみると、JSスレッドの負荷が高くてフレームレートが60fpsを維持できていない。

具体的にはこんな状況です。

- アイテムのコンポーネントが1アイテムごとに再レンダリングされている
- 画像を含むアイテムが多く、スクロール時のメモリ使用量が高い
- `keyExtractor`を適切に設定せず、警告が出続けている

このカクつきがユーザー体験を大きく損ないます。特にリストは画面の中心にあることが多いため、ここのパフォーマンスがアプリ全体の印象を決定します。

**適切な最適化を施すことで、FlatListのスクロールは滑らかになります。**

---

## FlatListの何が重いのか

FlatListは内部的にScrollViewの上にReact Nativeのレンダリング層を乗せた仕組みです。何も設定しないと、スクロール中に次のことが起きます。

- 画面外のアイテムも含めて全コンポーネントが再レンダリングされる
- 新しいアイテムを表示するたびに新しいコンポーネントインスタンスを生成する
- 親コンポーネントの状態変化が全アイテムに伝播する

これらが合わさって、JSスレッドに大きな負荷がかかります。

---

## 解決策：5つの最適化

### 1. `keyExtractor` を必ず設定する

### What（何をするのか）
各アイテムに一意なキーを返す関数を設定します。

### Why（なぜ必要なのか）
キーがないとReact Nativeはどのアイテムが変わったか判断できません。その結果、リスト全体を再レンダリングします。

### How（どのように実装するのか）

```tsx
<FlatList
  data={items}
  keyExtractor={(item) => item.id.toString()}
  renderItem={renderItem}
/>
```

IDが文字列であれば `item.id` をそのまま返せます。数値の場合は必ず `toString()` を呼びます。

---

### 2. `renderItem` を `memo` と `useCallback` で最適化する

### What（何をするのか）
アイテムのコンポーネントを `React.memo` でラップし、`renderItem` を `useCallback` でメモ化します。

### Why（なぜ必要なのか）
親コンポーネントが再レンダリングされるたびに、新しい `renderItem` 関数が生成されます。FlatListはこの変化を検知して全アイテムを再レンダリングします。`useCallback` でメモ化すると、依存する値が変わらない限り同じ関数参照を保持します。

### How（どのように実装するのか）

```tsx
// アイテムコンポーネントをmemoでラップ
const ItemComponent = React.memo(({ item }: { item: Item }) => {
  return (
    <View style={styles.item}>
      <Text>{item.title}</Text>
    </View>
  );
});

// 親コンポーネント内でrenderItemをuseCallbackでメモ化
const renderItem = useCallback(({ item }: { item: Item }) => {
  return <ItemComponent item={item} />;
}, []); // 依存配列は適切に設定する

<FlatList
  data={items}
  keyExtractor={(item) => item.id.toString()}
  renderItem={renderItem}
/>
```

`React.memo` は `props` が変化したときだけ再レンダリングします。`useCallback` と組み合わせることで、無駄なレンダリングを防ぎます。

---

### 3. `getItemLayout` でアイテムの高さを事前計算する

### What（何をするのか）
全アイテムの高さが同じ場合、`getItemLayout` でその高さを事前に教えます。

### Why（なぜ必要なのか）
通常、FlatListはスクロール位置を計算するために各アイテムのレイアウトを実際に計算します。`getItemLayout` を設定すると、FlatListはこの計算をスキップできます。特に大量のアイテムがある場合に効果が出ます。

### How（どのように実装するのか）

```tsx
const ITEM_HEIGHT = 80;

<FlatList
  data={items}
  keyExtractor={(item) => item.id.toString()}
  renderItem={renderItem}
  getItemLayout={(data, index) => ({
    length: ITEM_HEIGHT,
    offset: ITEM_HEIGHT * index,
    index,
  })}
/>
```

アイテムの高さが可変の場合は設定できません。その場合は次の方法を組み合わせます。

---

### 4. `initialNumToRender` と `windowSize` を調整する

### What（何をするのか）
最初にレンダリングするアイテム数と、レンダリングウィンドウのサイズを設定します。

### Why（なぜ必要なのか）
デフォルト設定では画面外の多くのアイテムをレンダリングします。この範囲を小さくすると初期ロードが速くなり、メモリ使用量も減ります。

### How（どのように実装するのか）

```tsx
<FlatList
  data={items}
  keyExtractor={(item) => item.id.toString()}
  renderItem={renderItem}
  initialNumToRender={10}    // 初期表示アイテム数（デフォルト: 10）
  maxToRenderPerBatch={10}   // 一度にレンダリングするバッチサイズ
  windowSize={5}             // 画面の何倍分を保持するか（デフォルト: 21）
  removeClippedSubviews={true} // 画面外のビューをアンマウント（Androidで有効）
/>
```

`windowSize={5}` は画面の5倍分のアイテムをメモリに保持することを意味します。値を小さくするとメモリ使用量は減りますが、高速スクロール時に白い空欄が見えることがあります。プロジェクトに合った値を実機でテストしながら調整します。

---

### 5. 画像には `FastImage` を使う

### What（何をするのか）
`Image` コンポーネントの代わりに `react-native-fast-image` を使います。

### Why（なぜ必要なのか）
React Nativeの標準 `Image` はキャッシュ管理が非効率です。スクロールのたびに同じ画像を再取得・再デコードすることがあります。`FastImage` はキャッシュ管理が最適化されており、スクロール中の画像表示が滑らかになります。

### How（どのように実装するのか）

```bash
npm install react-native-fast-image
cd ios && pod install
```

```tsx
import FastImage from 'react-native-fast-image';

const ItemComponent = React.memo(({ item }: { item: Item }) => {
  return (
    <View style={styles.item}>
      <FastImage
        style={styles.image}
        source={{
          uri: item.imageUrl,
          priority: FastImage.priority.normal,
          cache: FastImage.cacheControl.immutable,
        }}
        resizeMode={FastImage.resizeMode.cover}
      />
      <Text>{item.title}</Text>
    </View>
  );
});
```

---

## 実際に使ってみた結果

### 適用前の状態
- スクロール中のフレームレート：約40fps
- Profilerで確認すると、スクロールのたびに全アイテムが再レンダリングされていた
- メモリ使用量：150MB超（画像50枚のリスト）

### 適用後の状態
- スクロール中のフレームレート：59〜60fps（体感で明らかに滑らか）
- 各アイテムの再レンダリング：propsが変化したときのみ
- メモリ使用量：80MB前後に改善

### 直面した課題と解決方法

**`removeClippedSubviews` でレイアウトが崩れた**
Androidで `removeClippedSubviews={true}` を設定したところ、スクロール後に一部のアイテムのレイアウトが崩れる現象が出ました。この問題は既知のバグで、`overflow: 'hidden'` を親ビューに設定することで解消しました。

**`windowSize` を小さくしすぎた**
`windowSize={2}` に設定したところ、少し速くスクロールするだけで白い空欄が見えるようになりました。`windowSize={5}` に戻すと解消しました。ユーザー体験とメモリ使用量のトレードオフを実機で確認することが重要です。

### 学んだこと

最も効果が高かったのは `React.memo` と `useCallback` の組み合わせです。これだけで再レンダリングの回数が大幅に減りました。次に効果があったのは `FastImage` への移行です。画像の多いリストでは、画像の取り回しがボトルネックになることが多いと実感しました。

---

## おわりに

FlatListのパフォーマンス最適化は、いくつかのポイントを押さえれば大きく改善できます。

- `keyExtractor` で一意なキーを設定する
- `React.memo` と `useCallback` でレンダリングを最適化する
- `getItemLayout` でレイアウト計算を省略する
- `windowSize` と `initialNumToRender` を実機でチューニングする
- 画像は `FastImage` に切り替える

### 今すぐ始めるには

1. まず `React.memo` と `useCallback` を適用する（最も効果が高い）
2. `keyExtractor` が正しく設定されているか確認する
3. React Native DevToolsのProfilerでレンダリング回数を計測する
4. 画像が多いリストは `FastImage` を導入する

パフォーマンス改善は「計測 → 原因特定 → 改善」のサイクルが重要です。まずはProfilerでどのコンポーネントが無駄にレンダリングされているかを確認してから、対処法を選んでください。

---

この記事が役に立ったら、Xをフォローしていただけると嬉しいです!

https://x.com/_nogu66

## 参考リンク

- [FlatList - React Native 公式ドキュメント](https://reactnative.dev/docs/flatlist)
- [react-native-fast-image](https://github.com/DylanVann/react-native-fast-image)
- [React Native Performance - 公式ガイド](https://reactnative.dev/docs/performance)
- [React.memo - React 公式ドキュメント](https://react.dev/reference/react/memo)
