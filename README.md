# 2023年後期「JavaScript基礎」授業課題

## 授業内コード
1. 10月5日（木）はじめの一歩
2. 10月5日（木）GitHub　リポジトリ作成
3. 10月12日 (木) 文字列の連結、変数，定数、複合代入演算子、DOM操作
4. 10月19日　(木)　配列、for文、テンプレートリテラル

## 10月19日
- 配列
- for文

### htmlに入れる

```js
const element = document.querySelector(".recipe");//dl要素を取得
const lilast = document.createElement("dd");//dd要素を作る
lilast.textContent = "3分待ってできあがり";//ddの中に３分待って出来上がりを入れる
element.appendChild(lilast);//lilastをhtmlに入れる
```

### 配列

```js
const name_list = ["松田", "田中", "中山", "山本", "本田"];//[]で閉じれば配列になる、添字は0から始まる
console.log(name_list);//確認用
```

### for文

```js
const fruits = ["りんご", "もも", "バナナ"];

for (let i = 0; i < fruits.length; i++) {// for(初期化処理; 条件式; 増分処理){処理}    fruits.lengthで配列の数を取得している
    const element = document.querySelector("#fruitslist");//elementの宣言、#fruitslist要素を取得
    const lilast = document.createElement("li");//lilastの中に<li></li>の作成
    lilast.textContent = fruits[i];//lilastにりんご、もも、バナナを入れる
    element.appendChild(lilast);//appendChildでhtmlに反映される
}
```

### テンプレートリテラル

```js
console.log(`7✕${i + 1}=${7*(i + 1)}`);
```


## 10月12日

- リテラルと演算子
- 文字列の連結
- 変数と定数
- 複合代入演算子
- リストを操作するDOM操作のスクリプト

### 文字列の計算

```js
//文字鉄の連結
console.log("ABC" + "DEF"); //文字列　+ 文字列
console.log("円周率は" + 3.14 + "です"); //文字列 + 数値
console.log("計算結果:" + 123 + 456); //文字列 + 数値の計算
console.log(123 + 456 + "となりました。") //数値の計算 + 文字列
console.log("計算結果:" + (123 + 456)); //文字列 + (数値の計算)
console.log("2" - 1); //文字列　- 数値
console.log("2" * 3); //文字列　* 数値
console.log("2" / 4); //文字列　/ 数値
```

### 変数の宣言・代入
```js
let a; //変数の宣言 //ES6 = 2015
a = 10; //値の代入(数値型)
console.log(a);

a = "Hello"; //値の再代入(文字列型)
console.log(a);

//let a = "World"; //変数の宣言と代入を同時に行っています。更に再宣言なので、エラーとなります。

//定数の宣言
const PI = 3.14;
console.log(PI);

//再代入
//PI = 3.1415926535;
//const PI;
```

### 複合代入演算子
```js
let n = 5;
n = n + 2;
console.log(n);

let n2 = 5;
n2 += 2; //複合代入演算子 n2 = n2 + 2と同じ。
console.log(n2);
```

### インクリメント
```js
let n3 = 5;
n3++; //インクリメント1足す
console.log(n3);
```

### メロンを加える
```js
//ul要素を取り入れる
const element = document.querySelector("ul");
console.log(element);

//selectorってCSSのセレクターなので、
const element2 = document.querySelector("#fruitslist");
console.log(element2);

//classも行ける？
const element3 = document.querySelector(".listbox__list");
console.log(element3);


//新しい要素を作るli
const lilast = document.createElement("li");
console.dir(lilast); //dirに変更。オブジェクトの中身が見える
lilast.textContent = "メロン";
console.log(lilast);//<li>メロン</li>←こうなる
```

## 10 月 5 日

- インターネットの基本について理解する。
- Web の基本的な仕組みを理解する。
- Web サーバーの役割について理解する。
- 開発環境の構築
- JavaScript を書く場所

### JavaScript を書く場所

1. HTML ファイルの中
1. 外部 JS ファイルの中
1. ブラウザのコンソール

基本は、外部 JS ファイルを読み込むが、HTML 内に各場合は、`</body>`の上に書く。

```html
<!doctype html>
<html lang=ja>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>演習</title>
</head>
<body>
</script>
</body>
</html>
```

### フロントエンドロードマップ

フロントエンドエンジニアに必要なスキルの[ロードマップ](https://roadmap.sh/frontend)がある。