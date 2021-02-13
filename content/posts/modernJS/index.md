---
title: "Modern JavaScript ABC"
date: 2021-02-13T19:47:36+09:00
draft: false

summary: "Basic grammar and functions of modern JavaScript. Written in Japanese."

resources:
- name: "featured-image"
  src: "greg-rakozy-vw3Ahg4x1tY-unsplash.jpg"
- name: "featured-image-preview"
  src: "greg-rakozy-vw3Ahg4x1tY-unsplash.jpg"

tags: ["code","js"]
categories: ["Memo"]

lightgallery: true
---

<br>

## Intro :newspaper:
- I'm starting to study the front end, so I'll write quick note about the basics of `Modern JavaScrip`(ES6) .
- You can read more about it [here](https://developer.mozilla.org/en-US/).
- This article is written in `Japanese` as this is just a memo.

<br>

## 型 / Type

- `var`
上書き、再宣言可能

- `let`
上書き可能

- `const`
全て不可

{{< admonition type=note >}}
#### 基本的に`const`を利用する

**`const`はオブジェクト(辞書型)や配列の値は変更できる**
```js
const val5 = ['dog', 'cat'];
val5[0] = 'bird';
val5.push('hedgehog');
console.log(val5);
```
```
["bird", "cat", "hedgehog"]
```
#### このように、`0番目の値`が変更可能で`push()`による値追加も可能
{{< /admonition >}}

<br>

## テンプレート文字列 / Template literals

- Pythonの`f"{name}"`のようなもののJS版
- 文字列の囲みを **\` \`** にする
- 変数を置く場所は、`${}`


```js
const name = 'Ryuya';
const age = 21;
const message = `私の名前は${name}です。年齢は${age}歳です。`;
console.log(message);
```

```
私の名前はRyuyaです。年齢は21歳です。
```

<br>

## アロー関数 / Arrow function

- 変数に関数を当てられる
- 色々省略して書くこともが出来る
- `Python`だと`Lambda`らへんが似ているかも(?)  

<br>

**ただの入力された文字列を返す関数**
```js
const strFunc = (str) => {
  return str;
}
console.log(func("アロー関数です。"));
```
```
アロー関数です。
```

{{< admonition type=tip >}}
#### `return`や`{}`を省略して書くことが出来る。

上の例だと、以下で同様の関数が実装可
```js
const strFunc2 = (str) => str;
```
<br>

引数が二つでも同様
```js
const sumFunc = (num1, num2) => {
  return num1 + num2;
};

//省略版
const sumFunc2 = (num1, num2) => num1 + num2;
```

{{< /admonition >}}

<br>

## 分割代入 / Destructuring assignment

- 配列やオブジェクトから値を別個の変数に代入出来る
- 説明が難しいので、以下コードを参照


### 通常
  ```js
  const myProfile = {
    name: "Ryuya",
    age: 21,
  };
  const message1 = `名前は${myProfile.name}です。年齢は${myProfile.age}歳です。`;
  console.log(message1);
  ```
  ```
  名前はRyuyaです。年齢は21歳です。
  ```
### 分割を使用
```js
const {name, age} = myProfile;
const message2 = `名前は${name}です。年齢は${age}歳です`;
console.log(message2);
```
このように`myProfile`を省略出来る。

### 配列でも
```js
const myProfile = ["Ryuya", 21];
const [name, age] = myProfile;
const message2 = `名前は${name}です。年齢は${age}歳です`;
console.log(message3);
```

<br>

## デフォルト引数 / Default argument

- 普通のデフォルト引数、引数が指定されていないときに、それが代入される。

```js
const sayHello = (name = "Gest") => console.log(`Hello! ${name}!`);
sayHello();
```
```
Hello! Gest!
```

<br>

## スプレッド構文 / Spread syntax (...)

- 特殊な構文で応用的に色々出来る
- 反復可能オブジェクト(Iterable的な)を展開できる

<br>

### 基礎的な利用
```js
const arr1 = [1,2];
console.log(...arr1);
```
```
1 2
```
<br>

### 引数として当てる

  - 通常
    ```js
    const sunFunc = (num1, num2) =>  console.log(num1 + num2);
    sunFunc(arr1[0],arr1[1]);
    ```
    ```
    3
    ```

  - **スプレッド構文 使用**
    ```js
    sunFunc(...arr1);
    ```
      このように、二つの引数を一度に与えることが出来る。

<br>

### まとめる

例えば、`[1,2,3,4,5]`の配列があった場合、`[1], [2], [3,4,5]`への分割を以下の様に行うことが出来る。

```js
const arr2 = [1,2,3,4,5];
const [num1, num2, ...arr3] = arr2;
console.log(arr3);
```
```
[3, 4, 5]
```

<br>

### 結合
```js
const arr4 = [10, 20];
const arr5 = [30, 40];

const arr6 = [...arr4, ...arr5];
```
```
[10, 20, 30, 40]
```

<br>

### コピー
- `copy()`のように、コピーすることも出来る。
- コピーなので、オリジナルは参照されない。

```
const newArr4 = [...arr4];
```

<br>

## Map
- `for`を回してくれるもの
- 第二引数でindexをとれる

<br>

1. **`for`の場合**
    ```js
    for (let i = 0; i < nameArr.length; i++){
      console.log(`${i+1}: ${nameArr[i]}`);
    }
    ```
    ```
    1: Bob
    2: Jack
    3: Tom
    ```

2. **`map`を使うと**
    ```js
    const nameArr2 = nameArr.map((name) => {
      return name;
    })
    console.log(nameArr2);
    ```
    ```
    ["Bob", "Jack", "Tom"]
    ```

3. **`map` & `アロー関数` で美しく**
    ```js
    nameArr.map((name, index) => console.log(`${index+1}: ${name}`));
    ```
    ```
    1: Bob
    2: Jack
    3: Tom
    ```

<br>

## Filter
- 名前の通り、filterを掛けられる。  
<br>

奇数のみを取り出す関数
```js
const numArr = [1,2,3,4,5];
const newNumArr = numArr.filter((num)=>{
  return num % 2 === 1;
})
console.log(newNumArr);
```
```
[1, 3, 5]
```

<br>

## 三項演算子 / Conditional (ternary) operator
- 安定の三項演算子
- `?`前で条件式、`?`以降が`true`時の結果。 `:`移行が`false`時の結果。
```js
const val1 = 1 > 0 ? 'true' : 'false';
console.log(val1);
```
```
true
```
<br>

{{< admonition type=tip >}}
##### `.toLocaleString()`というメソッドで3桁区切りができる。

```js
const num = 1300;

const formattedNum = typeof num === 'number' ? num.toLocaleString() : 'Please enter number';
console.log(formattedNum)
```
`num`が数値の場合、区切られた値が返る。そうでない場合、`Please enter number`が返ってくる。  
今回は数値なので以下が結果  
```
1,300
```

{{< /admonition >}}

<br>

## `&&` `||` の真実
- ここでは、`&&`や`||`が実際どういう意味なのかを示す。

<br>

### `||`は左側が`false` -> 右側を返す

`null`は`false`扱いなので以下の結果になる
```js
const num = null;
const fee = num || 'unknown';
console.log(fee);
```
```
unknown
```
なお、`const num = 100;`の場合は、`100`が結果として返ってくる。

<br>

### `&&`は左側が`true` -> 右側を返す
```js
const num2 = 111;
const fee2 = num2 && 'Something';
console.log(fee2);
```
```
Something
```
