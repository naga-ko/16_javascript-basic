# 2023年後期「JavaScript基礎」授業課題

## 授業内コード
1. 10月5日（木）はじめの一歩
2. 10月5日（木）GitHub　リポジトリ作成
3. 10月12日 (木) 文字列の連結、変数，定数、複合代入演算子、DOM操作
4. 10月19日　(木)　配列、for文、テンプレートリテラル
5. 10月26日　（木）その他のdocumentの取得と挿入、イベント
6. 11月2日　（木）　classlistととにかくイベント
7. 11月9日　（木） 条件分岐
8. 11月30日 （木）関数
9. 12月7日　（木）関数、引数、戻り値、関数式、変数のスコープ
10. 12月14日 (木) コールバック関数、アロー関数
11. 1月11日　（木）フォーム、オブジェクトの操作

## 1月11日
- フォーム
- オブジェクトの操作

### オブジェクトの操作
```js
//chatGPTで
//「keyとプロパティの連想配列にしてください」とやると楽
const championship = {
    y2018: '大阪桐蔭',
    y2019: '履正社',
    y2020: '新型コロナ感染拡大の影響で中止',
    y2021: '智弁和歌山',
    y2022: '仙台育英',
    y2023: '慶応'
};
const selection = {
    2018: '大阪桐蔭',
    2019: '東邦',
    2020: '新型コロナ感染拡大の影響で中止',
    2021: '東海大相模',
    2022: '大阪桐蔭',
    2023: '山梨学院'
};
console.log("選手権優勝校:", championship.y2023);//ドット記法
console.log("選抜優勝校:", selection['2023']);//ブラケット記法

const hashira_list = { water: "鱗滝左近次", worm: "胡蝶しのぶ", flame: "煉獄杏寿郎", sound: "宇髄天元", love: "甘露寺蜜璃" };

//追加
hashira_list.rock = "悲鳴嶼行冥";
hashira_list.haze = "時透無一郎";
hashira_list.snake = "伊黒小芭内";
hashira_list.wind = "不死川実弥";

//代入
hashira_list.water = "冨岡義勇";
console.log(hashira_list);
```
### フォーム

```js
const Btn = document.querySelector('[type="submit"]');
Btn.addEventListener("click", function (event) {
    event.preventDefault();//これをつけないとリロードされたりして一瞬だけしか見えない
    const text = Number(document.querySelector(".num").value);//Numberをつけることで数値型になる
    if (text === 2) {                                 //valueでform取ることがデキる
        console.log("数値の2です");
    } else {
        console.log("違います。")
    }
    const kuku = document.querySelector(".kuku");
    for (let i = 0; i < 9; i++) {
        const liElm = document.createElement("li");
        liElm.textContent = text + "×" + (i + 1) + "=" + text * (i + 1);
        kuku.appendChild(liElm);
    }
})
```

## 12月14日
- コールバック関数
- アロー関数

### アロー関数

```js
//鳴き方を決めたい
const animal = (voice) => {//function()のかわりに "(関数名) =>"でOK
    return voice;
}
//関数animalの実行
console.log(animal("みゃあみゃあ"));

const thisElm = document.querySelector("p");
console.log(thisElm);

thisElm.addEventListener("click", (e) => {
    console.log("クリック");
    // console.log(this.textContent); //アロー関数を使うとthisが使えない
    console.log(e.target.innerText);
});
```
### コールバック関数
```js
//関数式1
const concatenateSpace = function (lastName, firstName) {
    return lastName + " " + firstName;
};

//関数式2
const useConcatenate = function (name, func) {
    let concatName = func(name[0], name[1]);
    console.log("結合結果：" + concatName);
};

let nameParam = ["長瀬", "光輝"];

//関数式2の実行（引数1、引数2）
useConcatenate(nameParam, concatenateSpace);

//結合結果：中田 雄二



//コールバック関数基本　※よく使う
//関数式1
const testFunc = function (func) {
    console.log("testFuncが実行されました");
    setTimeout(function () {//関数の実行を遅らせるため
        func();//関数の実行
    }, 2000);//2000ミリ秒（２秒）
};

//関数式2
const callback = function () {
    console.log("callbackが実行されました");
};

testFunc(callback);//関数を引っ張ってくることをコールバック関数
```

### 普通の関数

```js
const startBtn = document.querySelector(".startBtn");
const animalSpeed = [3, 4, 1, 3, 2];
const animals = document.querySelectorAll("li span");

// ここに関数animalsRunを作成してください。
const animalsRun = function (list) {
    for (let i = 0; i < list.length; i++) {
        list[i].style.transitionDuration = animalSpeed[i] + "s";
        list[i].classList.add("run");
    };
};

startBtn.addEventListener("click", function () {
    animalsRun(animals);
});
```

## 12月7日
- 引数
- 戻り値
- 関数式
- 関数のスコープ

### 変数のスコープ
```js
// グローバル変数の初期化※再代入可能にするためletを使う。
let global = "グローバル変数";

//関数funcの定義
const func = function () {
    //ローカル変数の初期化
    let local = "ローカル変数";
    //グローバル変数の表示
    console.log(global);
    //ローカル変数の表示
    console.log(local);
    global = "グローバル変数を再代入";
    console.log(global);
    // var global = "グローバル変数を再定義";
    // console.log(global);
}

if (global) {
    var local2 = "varは関数スコープ";
    let local3 = "letはブロックスコープ";
}
func();
//グローバルはvar global = "グローバル変数を再定義";で再定義されているので、undefinedになる。

//グローバル変数の表示
console.log(global);
//ローカル変数の表示は、関数funcの中で定義されているので、呼び出せない。
//varは関数スコープなので、if文の外で呼び出せる。
console.log(local2);
//letはブロックスコープなので、if文の外で呼び出せない。
console.log(local3);
```

### 戻り値
```html
<p>ケーキ（450円）の税込み価格</p>
<button class="takeOut">テイクアウト</button>
<button class="eatIn">イートイン</button>
<p>税込み価格は、<span class="taxIn"></span>円です。</p>
```
```js
const cake = 450;
const takeOutBtn = document.querySelector(".takeOut");
const eatInBtn = document.querySelector(".eatIn");
const result = document.querySelector("taxIn");

const calculation = function (cake, tax) {
    const result = cake + cake * tax;
    return result;//戻り値
}

takeOutBtn.addEventListener("click", function () {
    const price = calculation(cake, 0.08);
    result.innerHTML = price;
});

eatInBtn.addEventListener("click", function () {
    const price = calculation(cake, 0.1);
    result.innerHTML = price;
});
```

### 関数
```js
const nextStep = function () {
    if (count === 2) {
    count = 0;
    } else {
    count++;
    }
    imageArea.setAttribute("src", "images/" + fujiImg_list[count]);
};

//関数の実行
nextBtn.addEventListener("click", function () {
    nextStep();
});

//前の画像を表示
const preStep = function () {
    if (count === 0) {
    count = 2;
    } else {
    count--;
    }
    imageArea.setAttribute("src", "images/" + fujiImg_list[count]);
};

//関数の実行
preBtn.addEventListener("click", function () {
    preStep();//関数名と()で実行
});
```
## 11月30日
- 関数

### 配列を受け取る関数
```html
<div class="fnArea"></div>
```
```js
const member_list = ["チェウォン", "サクラ", "ユンジン", "カズハ", "ウンチェ"];
        const mugiwara_list = ["モンキー・D・ルフィ", "ナミ", "ロロノア・ゾロ", "ヴィンスモーク・サンジ", "ウソップ", "トニートニー・チョッパー", "ニコ・ロビン", "フランキー", "ブルック", "ジンベエ"];


        //.fnAreaに上記の配列の要素を<li>で追加する関数
        const memberarea = document.querySelector(".fnArea");
        const memberPush = function (members) {
            const ulElm = document.createElement("ul");//ulを作る
            for (let i = 0; i < members.length; i++) {
                const liElm = document.createElement("li");//liは毎回作る
                liElm.textContent = members[i];//liElmに呼び出されたものを入れる
                ulElm.appendChild(liElm);//ulにliを追加する
            }
            document.querySelector(".fnArea").appendChild(ulElm);//.fnAreaにulElmを入れる
        }

        //関数の実行
        memberPush(member_list);
        memberPush(mugiwara_list);
```
### テンプレートリテラル

```js
const yoshinoya = function (don, size, tuika, kin) {
            console.log(don + "の" + size + "、" + tuika + "で" + kin + "円");
            console.log(`${don}の${size} ,${tuika}で${kin}円`);//テンプレートリテラル
        }

        //関数の実行
        //複数の引数を読み込む場合は、,で区切る
        yoshinoya("牛丼", "並盛", "つゆだく", 388); //牛丼の並盛、つゆだくで 388 円
        yoshinoya("豚丼", "大盛", "たまご", 592); //豚丼の大盛、たまごで 592 円
```

### 処理を箱から出す感じ

```js
//関数の定義
function kuku(num) {
    for (let i = 0; i < 9; i++) {
        console.log(num + "✕" + (i + 1) + "=" + num * (i + 1));
    }
}

//関数の実行
kuku(5);//numに入る↑

//関数の定義
function showMessage(message) {
    console.log(message);
}

//関数式
const showMessage2 = function (message) {
    console.log(message);
}

//イベントで関数を使う
document.body.addEventListener("click", function () {
    showMessage("こんにちは");
});
```

### 下に書いてもできる

```js
function dogName() {
    console.log("私のうちの犬の名前は、ポチです。");
}

//関数の実行
dogName();
catName();
//関数の定義
function catName() {
    console.log("私のうちの猫の名前は、タマです。");
}
```
## 11月9日
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