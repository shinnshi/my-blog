---
title: 'React 公式チュートリアルを TypeScript で書いてみた'
date: '2020-06-28'
---React の公式チュートリアル[（ チュートリアル：React の導入~）](https://ja.reactjs.org/tutorial/tutorial.html)は、JavaScript で書かれていますが、TypeScript の入門としてリファクタリングしてみました。

・[完成した Git のリポジトリのリンク ](https://github.com/shinnshi/react-ts-tutorial)

## チュートリアルの準備

基本的にチュートリアル通りに進めていきますが、TypeScrip で書きやすくするためブラウザではなく、
ローカルで VScode を使って進めていきます。CRA コマンドに TS オプションを付けて新しいプロジェクトを作成してください。

```
npx create-react-app {プロジェクト名} --typescript

```

あとは、チュートリアル通りにブラウザからコピペで完成です。

・[ここまでのコード差分](https://github.com/shinnshi/react-ts-tutorial/commit/35a549ef5f486238818513cef8281801401c74cf)

## データを Props 経由で渡す

チュートリアル通りにデータを Props 経由で渡しながら、コンパイルエラーを直していきます。
エラーの出ている関数、メソッドの引数に型を付けていきます。

```
renderSquare(i: number) { return <Square /> }

```

・[ここまでのコード差分](https://github.com/shinnshi/react-ts-tutorial/commit/ea40124c966f7040282efa6c862c5170b91808fa)

## インタラクティブなコンポーネントを作る

Square クラスが受け取る Props に対して、interface で型をつけます。

```
interface SquarePropsInterface { value: number}

```

同じように、クラスの State に対しても、interface で型をつけます。

```
interface SquareStateInterface { value: string}

```

・[ここまでのコード差分](https://github.com/shinnshi/react-ts-tutorial/commit/a8ac811b4321870f87a500a88860212ce73f013c)

## ゲームを完成させる

ここから先は、interface か type を使って、型定義をしながらチュートリアル通りに、実装していけば良いです。チュートリアルに、リファクタが入ってきて、並行してやりにくくなるので、差分のコードは書きません。完成したコードを参照してください。

・[完成したコード](https://github.com/shinnshi/react-ts-tutorial/commit/004a151ed51a3e7e811798cfc0262eda43ea8b7a)

## 感想

TypeScript の入門として、久しぶりに公式チュートリアルをやりましたが、書いてる時に React のコードにも少し違和感がありました。

### Class Component を使っている

- 途中、Functional Component にリファクタが入ってきましたが、FunctionalComponent + Hooks 化してみるのも良いかも。

### 表示内容を作るメソッドを JSX から呼んでいる

- renderAnything(){}みたいなの。このチュートリアル以外のプロジェクトは、Redux や Hooks なんかで、state に変更を加えてそれを表示してた。JSX では state を表示するだけにした方が読み易い。

---

そんな感じで終わります。

Twitter : [@dev_shts](https://twitter.com/dev_shts)
