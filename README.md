# bkjs
バックアップ



# dh19_4_JavaScript

・[Swiper（スライドショー）](#Swiper) <br>
・[ハンバーガーメニュー](#ハンバーガーメニュー) <br>
・[ピュアJavaScript](#素のJavaScriptに触れてみよう！) <br>

<br>
<br>

# Swiper
JavaScriptのスライドショー制作のためのライブラリです。

<img src="http://hareumi.com/dhjs/swiper2.png" width="400px">
<br>

参考 <br>
公式サイト https://swiperjs.com/  <br>
ガリガリコード https://garigaricode.com/swiper/
<br>

## 1、使用するcssとjsの読み込み

    <link rel="stylesheet" href="https://unpkg.com/swiper/css/swiper.min.css">
    <script src="https://unpkg.com/swiper/js/swiper.min.js"></script>
    
<br>

## 2、HTMLの記述

クラス名は原則いじらないようにしましょう。class="swiper-slide"のdiv内に画像を入れましょう。
	
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide"><img src="ここにパス"></div>
            <div class="swiper-slide"><img src="ここにパス"></div>
            <div class="swiper-slide"><img src="ここにパス"></div>
            <div class="swiper-slide"><img src="ここにパス"></div>
        </div>

        <!--<div class="swiper-button-prev"></div>-->
        <!--<div class="swiper-button-next"></div>-->
    </div>

<br>

## 3、cssでサイズ調整
    .swiper-container {
        width: 800px;
        height: auto;
    }
    .swiper-container img{
      width: 100%;
      height: auto;
    }
    @media screen and (max-width: 768px) {
      .swiper-container{
        width: 100%;
      }
    }

## 4、JavaScriptの記述

### デフォルト

    var swiper = new Swiper('.swiper-container');
    
### オプション autoPlay
    
    var swiper = new Swiper('.swiper-container', {
    speed: 1000,
    autoplay: {
      delay: 3000,
      /*最後のスライドまで行くと最初のスライドに戻って再生し続ける*/
      stopOnLastSlide: false,
      /*  ユーザーがスライダーを操作した後も自動再生し続ける*/
      disableOnInteraction: false,
      /* 最初のスライドから順に再生する */
      reverseDirection: false
    }
    });
  
### オプション 3枚スライド
    
    var swiper = new Swiper('.swiper-container', {
    effect: 'coverflow',
    slidesPerView: 3,
    autoplay: {
      delay: 3000,
      stopOnLastSlide: false,
      disableOnInteraction: false,
      reverseDirection: false
    },
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev'
    }
    });
    

<br>
<br>
<br>
<br>
<br>

# ハンバーガーメニュー
<img src="http://hareumi.com/dhjs/defolt.png" width="200px"><img src="http://hareumi.com/dhjs/active.png" width="200px">


    <!-- ボタン部分 -->
    <button id="btn">
        <span></span>
    </button>
    
    
    <!-- メニュー部分 -->
    <nav class="navigation">
      <ul class="nav-list">
        <li><a href="">Home</span></a></li>
        <li><a href="">About</span></a></li>
        <li><a href="">WORKS</span></a></li>
        <li><a href="">CONTACT</span></a></li>
      </ul>
    </nav>
    
# spanタグを使って、CSSで線を作る
    
    
<img src="http://hareumi.com/dhjs/btn1.jpg" width="100px">


    /* 中央の線 */
    button span{
        background: #1E1E1E;
        width: 40px;
        height: 2px;
        display: block;
        position: absolute;
        top: 18px;
        right:18px;
        margin: 0 0 0 -13px; /* 位置調整用 */
    }
    
<img src="http://hareumi.com/dhjs/btn2.jpg" width="100px">

    /* 上下の線 */
    button span:before,
    button span:after{
        background: #1E1E1E;
        width: 100%;
        height: 100%;
        display: block;
        content: "";
        position: absolute;
        left: 0;
        top: 0;
    }

    /* 上下の線の位置調整 */
    button span:before{
      transform: translate(0,13px);
      transition:0.3s all;
    }
    button span:after{
      transform: translate(0,-13px);
      transition:0.3s all;
    }


<img src="http://hareumi.com/dhjs/btn3.jpg" width="100px">



    /* 傾けた後の動き */
    button.open span{
      background: rgba(0,0,0,0);
    }
    button.open span:before{
      transform: rotate(45deg);
    }
    button.open span:after{
      transform: rotate(-45deg);
    }
    

    
# JavaScriptの記述
    
    $("#btn").on("click", function () {
	    $(this).toggleClass('open');
	    $(".navigation").toggleClass("is_active");
    });
    
<br>
<br>
<br>
<br>
<br>



# 素のJavaScriptに触れてみよう！
素のJavaScriptのことを「ピュアjs」や「バニラjs」などと呼びます。<br>
バニラjsで変数と関数について学びましょう！また。<br>
今までjQueryで書いていたものをバニラjsに書き換えてみましょう！
<br>

## 変数
データを一時的にパソコンのメモリに保存する箱。<br>
簡単に例えると「万能なコップ」。「ミネラルウォーター」や「コーラ」が入れられる。<br>
そしてjsの変数には、なぜかコップに「東京都」などが入れられる笑<br><br>

    // bodyの背景を変更してみる
    document.querySelector("body").style.backgroundColor = "red";
    
    // 変数を使ってみる
    var bgColor = "black";
    
    // bgColorが変数
    document.querySelector("body").style.backgroundColor = bgColor;
    
    
    // letとconstが新バージョンES2015（ES6）から使用可能に！
    
    /* varとほぼ同じだが、同じ名前を使えない、スコープ外で使えない https://techacademy.jp/magazine/14872 */
    let bgColor = "black";
    
    /* 二度と値を変更できない */
    const BG_COLOR = "black"; 
    

使い所参考（アコーディオン いけん求める）
https://lab.sonicmoov.com/wp-content/uploads/demo/marizo/201507_accordion/#demo01



    
## 関数
複数の処理をひとまとめにして実行できるようにする機能。<br>
例えると「自動販売」のようなもので、「コインを入れて、ボタンを押すと、何かが出てくる」<br>
ような仕組み。<br>
解説参考: https://kitsune.blog/function

    // カフェの設定でいきます。
    
    // 宣言
    function order(){
        alert("おはようございます、コーヒーを一杯どうぞ");
    }
    
    // 実行
    order();  // "おはようございます、コーヒーを一杯どうぞ"
    
    
    
    // 引数ありver
    var drink = "カフェラテ";
    
    // 宣言
    function order(drink){
        alert("おはようございます + drink + を一杯どうぞ");
    }
    
    // 実行
    order(drink); // "おはようございます、カフェラテを一杯どうぞ"
    
    
    // 返り値（return）
    let drink = "コーヒー";
    
    function getPrice(coffee){
        let price = 290;
        return price;
    }
    
    // コーヒーの値段
    let coffeePrice = getPrice(drink);
    alert(coffeePrice); // 290

    
関数のメリットでWebSpeechで説明
<img src="http://hareumi.com/jskouza/sutaba.png" width="150px">

    
    // アロー関数で書いてみよう！
    let order = () => {
        alert("おはようございます、コーヒーを一杯どうぞ");
    }
    order();
    
    
    // 引数ありver
    let drink = "カフェラテ";
    let order = (drink) => {
        alert("おはようございます、"+  drink +" を一杯どうぞ");
    }
    order(drink);
    
    
    
ES6のコードを変換（トランスパイル）<br>
https://barikanblog.com/javascript-es6-babel/






# Animate.cssの使い方

![歴史](http://hareumi.com/jskouza/animate.png "サンプル")

[公式サイト]https://daneden.github.io/animate.css/

クラス名をつけるだけで簡単にcssアニメーションをしてくれる人気のライブラリです。
animatedクラスと、好きな動作のクラスを書くだけ。

    <!-- <head>タグ内に記述 -- >
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.css">
    
    <div class="animated bounce">ここにテキストやimgタグ</div>
    
[使い方参考サイト](https://lab.sonicmoov.com/markup/css/animate-css/)


<br><br><br>



## ピュアJsを書いてjQueryのありがたみを知る。  
jQueryのありがたみを知りましょう！



### addClass
    /* ピュアjs */
    document.querySelector("#target").classList.add("bounce");
    
    /* jQuery */
    $("#target").addClass("bounce");
    
### onClick
    /* ピュアjs */
    document.querySelector("#btn").addEventListener("click", function(){
 	    document.querySelector("#target").classList.add("tada");
    });
    
    /* jQuery */
    $("#btn").on("click",function(){
        $("#target").addClass("tada");
    });
    
    
    
参考 : 注意！IE11で使えない最新JavaScritコード（ES6）2018年9月24日
https://blog.capilano-fw.com/?p=1273

