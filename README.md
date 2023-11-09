# 2023年後期「JavaScript基礎」授業課題

## 授業内コード
1. 10月5日（木）はじめの一歩
2. 10月5日（木）GitHub　リポジトリ作成
3. 10月12日 (木) 文字列の連結、変数，定数、複合代入演算子、DOM操作
4. 10月19日　(木)　配列、for文、テンプレートリテラル
5. 10月26日　（木）その他のdocumentの取得と挿入、イベント
6. 11月2日　（木）　classlistととにかくイベント
7. 11月9日　（木） 条件分岐

## 11月9　日
- 条件分岐

### 　右左

```js
const left = document.querySelector(".leftZone");
const right = document.querySelector(".rightZone");
console.dir(left);
const widthsize = window.innerWidth; //現在のブラウザの横幅
console.log(widthsize);
//以下から記述していきます。
document.body.addEventListener("click", function (event) {
    console.log(event.clientX)
    let hantei = widthsize / 2;
    console.log(hantei);
    if (hantei > event.clientX) {
        let i = 0;
        i++;
        const left_li = document.createElement("li");
        left_li.textContent = "左"
        left.appendChild(left_li);
    } else {
        let i = 0;
        i++;
        const right_li = document.createElement("li");//エレメントを作る
        right_li.textContent = "右"
        right.appendChild(right_li);//追加
    }
});//insertAdjacentHTML("beforeend")でもできる
```

## 11月2日
-

### ノード操作演習
```js
//画像ファイル名は、配列から取得します。
const fujiImg_list = ["mt-fuji001.jpg", "mt-fuji002.jpg", "mt-fuji003.jpg"];

// 画像のタグ<img>要素を変数に取得
const mt_img = document.querySelector(".photo img");

//富士山のボタン全てを querySelectorAll で変数に取得
const mtFujiBtn = document.querySelectorAll(".image-fuji");
console.log(mtFujiBtn);

//NodeList なので for 文でそれぞれのボタンに click イベントを登録する。(addEventListener)
mtFujiBtn[0].addEventListener("click", function () {
    mt_img.setAttribute("src", "images/mt-fuji001.jpg")
});

mtFujiBtn[1].addEventListener("click", function () {
    mt_img.setAttribute("src", "images/mt-fuji002.jpg")
});

mtFujiBtn[2].addEventListener("click", function () {
    mt_img.setAttribute("src", "images/mt-fuji003.jpg")
});
```

### 背景

```js
const bodyelement = document.querySelector("body");
console.dir(bodyelement);
let counter = 0;
const color_array = ["pink", "blue", "orange", "green", "tomato"]; //配列
bodyelement.addEventListener("click", function () {//bodyelementがクリックされたとき
    console.log(counter);
    bodyelement.style.backgroundColor = color_array[counter]; //bodyelementの中のstyleの中のbackgroundColorを配列から選ぶ
    counter++;//counter = counter + 1
});
```

### ダンサー

```js
const dacingBtn = document.querySelector(".dancing");
const stopBtn = document.querySelector(".stop");
const changeBtn = document.querySelector(".change");
const dancer = document.querySelector(".imgArea img");//要素の取得
dacingBtn.addEventListener("click", function () {//dacingBtnをクリックされたとき
    dancer.setAttribute("class", "dance")        //dancerのclassをdanceに変える
});
stopBtn.addEventListener("click", function () {  //removeAttribute
    dancer.removeAttribute("class")              //dancerのclassを削除する
});
changeBtn.addEventListener("click", function () {
    dancer.setAttribute("src", "images/ballet_woman.png") //dancerのsrc属性を変更する
});
```

## 10月26日
- innerHTML
- querySelectorAll
- イベント

### 文字色、文字の大きさをclassから変更

```js
<p><span>JavaScript</span>（ジャバスクリプト）とは、プログラミング言語のひとつである。</p>
<button class="redder">赤くなる</button>
<button class="bigger">大きくなる</button>
//element.setAttribute("class","??")
const text = document.querySelector("p span");
const Btnr = document.querySelector(".redder");
const Btnb = document.querySelector(".bigger");
Btnr.addEventListener("click", function () {//クリックされたときテキストのクラスをredTextにする
    text.setAttribute("class", "redText")
});
Btnb.addEventListener("click", function () {
    text.setAttribute("class", "bigText")
});
```

### 文字の色変更

```js
const redBtn = document.querySelector(".red");//レッドの取得
const text = document.querySelector(".text");//テキストクラスの取得
const textSpan = document.querySelector(".text span");//テキストの中のスパンを取得
redBtn.addEventListener("click", function () {
    console.dir(text)
    text.style.color = "#ff0000";
    textSpan.innerText = "赤";
});
```

### 関数を作らずに処理

```js
//例）「ブラウザで発生する主なイベント」から"resize"（サイズが変更する）タイミングで console に文字が発生するようにします。
//resizeは、DOM内にはありませんのでwindowで取得します。
window.addEventListener("resize", function () {
//ここに処理を書きます。
console.log("サイズが変わりました。");
});
```

### 関数有りの処理

```js
<button id="btn">ハンドラを起動する</button>
function showMessage() {
  alert("ハンドラが起動しました！");
}
let btn = document.querySelector("button");
btn.addEventListener("click", showMessage);//加える＋イベント＋リスト
```

### getElementsByClassName

```js
const class_element = document.getElementsByClassName("pool_b");
console.log(class_element);//指定されたclass名の要素
```

### getElementsByTagName

```js
const tag_element = document.getElementsByTagName("li");
console.log(tag_element);//指定されたタグ名の要素
```

### getElementById

```js
const id_element = document.getElementById("toparis");
console.log(id_element);//id属性を取得したいとき
```

### querySelectorAll

```js
const nations_list = document.querySelectorAll("ul li");
//もしくは、document.querySelectorAll("#toparis li");などでも可
console.log(nations_list);
//querySelectorAllを使うことで配列の中に入るので一つ一つ取得する必要がない
```

### innerHTML

```js
  const sweetpotatos = document.querySelector(".imo");
  //innerHTMLプロパティで、中身を確認
  console.log(sweetpotatos.innerHTML);
  //innerHTMLに文字列でHTMLのタグを代入する。
  sweetpotatos.innerHTML = "<li>べにはるか</li>";//appendchaildを使わなくてもinnerHTMLでできる
```

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
<script>
</script>
</body>
</html>
```

### フロントエンドロードマップ

フロントエンドエンジニアに必要なスキルの[ロードマップ](https://roadmap.sh/frontend)がある。