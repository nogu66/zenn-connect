---
title: "react-router-dom v6でのルーティング"
emoji: "🧭"
type: "tech"
topics:
  - "react"
published: true
published_at: "2023-04-29 22:46"
---

React Routerは、Reactアプリケーションでのルーティングを容易にするためのライブラリです。
V6にアップデートされたことによりV5と少し実装方法が変更になってしまったので、記事にまとめました。

## インストール

最初に、react-router-dom v6をインストールする必要があります。npmを使用して、以下のコマンドを実行します。

```
npm install react-router-dom@next
```

## ルーティングの基礎

ルーティングを使用するには、`<Router>`コンポーネントを使用する必要があります。以下の例では、`<Router>`コンポーネントを使用して、`/`と`/about`の2つのパスに対応する2つのコンポーネントをレンダリングしています。

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}
```

## ネストされたルーティング

react-router-dom v6では、ルーティングをネストすることができます。以下の例では、`/users`パスに対応する`Users`コンポーネントをレンダリングし、その中に`/users/:userId`パスに対応する`User`コンポーネントをレンダリングしています。

V6での書き方

```jsx
function Users() {
	const {userId} = useParams();

  return (
    <div>
        <p>UserID {userId}です</p> 
    </div>
  );
}

function User() {
  let { userId } = useParams();
  return <h3>User ID: {userId}</h3>;
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/users/:userId" element={<Users />} />
      </Routes>
    </Router>
  );
}
```

V5での書き方

```jsx
function Users(props) {
  return (
    <div>
      <p>UserID {props.userId}です</p> 
    </div>
  );
}

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/" element={<Home />} />
        <Route path="/users" element={<Users />} />
        <Route
	  exact
	  path="/restaurants/:userId"
	  render={({ userId }) =>
	  <Foods
	      userId={userId}
          />
	</Switch>
    </Router>
  );
}

```

## まとめ

react-router-dom v6は、Reactアプリケーションでのルーティングを簡単にするための優れたライブラリです。このドキュメントでは、v6でのルーティングの基礎とネストされたルーティングについて説明しました。
