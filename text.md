**やること**

- (目的) 自分で考えて値の取得出力ができるようになる
- chromeによるデバッグ  
- 簡単なDOMの操作
- 値の取得(デバッグで取得)  
- 値の出力(デバッグで取得)
- 学んだことの課題やって終わり


参考文献

柳井政和『[JavaScript　仕事の現場でサッと使える! デザイン教科書 (Webデザイナー養成講座)](http://amzn.to/2hYyzYW)』, 技術評論社, 2015.7


--

今回の授業でやることが把握できると、以下のコード内容が理解できるようになると思います。

**Ajax(Asynchronous JavaScript + XML)**

> 動的処理を実装するための技術としてAjaxと呼ばれる技術が存在します。
Ajaxは、Asynchronous（非同期）通信を可能とする技術でHTTPリクエスト、レスポンスのやり取りをJavaScriptが担当してくれます。Ajaxを実装することで動的にHTMLの一部を書き換えることができます。

**DIVE15_コメント機能**

`app/views/comments/index.js.erb` 

```
$("#comments_area").html("<%= j(render 'comments/index', { comments: @comment.blog.comments, blog: @comment.blog }) %>")
$(':text').val('')
```

--

**DOM**
DOMとは、「Document Object Model」の略称です。このDOMでは、Webページのタグの構造を、ツリー状のデータとして扱うことが出来ます。このツリー状の構造は、ファイルやディレクトリの階層構造に似ています。また、ツリー状の各部品のことは要素と呼びます。

```
<body>
	<h1>タイトル</h1>
	<div>
		<p>本文1本文1本文1本文1。</p>
		<p>本文2本文2<span>本文2</span>本文2。</p>
	</div>
</body>
```
![DOM](http://i.imgur.com/vNwlKfA.png)

**JavaScriptの記述**

２つの方法があります。

- htmlファイルの中で実行

`index.html` 

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Practice</title>
    <script>
    // コメント
    /*
    複数行のコメント
    複数行のコメント
    */
    var text = "コンソールに出力"; // 変数
	console.log(text); // Rubyのputsみたいな役割
	var text2 = "2回目のコンソールに出力";
	console.log(text2);
    </script>
  </head>
  <body>
  </body>
</html>
```

- JavaScriptを外部ファイルに書く（同じディレクトリにある場合を想定）

`index.html` 


```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Practice</title>
    <script src="main.js"></script>
  </head>
  <body>
  </body>
</html>
```

`main.html` 


```
// コメント
/*
複数行のコメント
複数行のコメント
*/
var text = "コンソールに出力";
console.log(text);
var text2 = "2回目のコンソールに出力";
console.log(text2);
```

--
**chromeによるデバッグ**

![DOM](http://i.imgur.com/U3AHwpp.png)
![DOM](http://i.imgur.com/f0Tdy7l.png)
![DOM](http://i.imgur.com/FA2VNuh.png)
--

**jQuery**

jQueryは、JavaScriptのライブラリです。JavaScriptのライブラリは、外部Javascriptファイルに便利な関数をパッケージしたものです。（説明追記）

**jQueryでできること**

1. セレクタを使ってDOMの要素を選択する。
2. 選択したDOMの要素を操作する。
3. 選択したDOMの要素に手軽にイベントを設定する。
4. 選択したDOMの要素をアニメーションさせる。
5. サーバーと手軽に通信する。

この授業では1. 2. を扱います。

**jQeryの入手**

- 公式サイトからDL

```
https://jquery.com/
```

- CDN(Content Delivery Network)の利用

```
<html lang="ja">
  <head>
    <meta charset="utf-8">
    <title>Input to page</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="main.js"></script>
    <link rel="stylesheet" href="default.css">
  </head>
  .
  .
  .
</html>  
```

--

**jQueryの基本構文 セレクタ編**

jQueryを使う最大の利点は、セレクタでDOM要素を選択して操作できることです。このセレクタでの選択は、かなり細かく指定できます。

> セレクタの細かい指定の方法 参考URL

> - [http://semooh.jp/jquery/api/selectors/](http://semooh.jp/jquery/api/selectors/) 
- [http://qiita.com/Thought_Nibbler/items/5d4fc40a4d4325128b24](http://qiita.com/Thought_Nibbler/items/5d4fc40a4d4325128b24)
- [http://www.detelu.com/blog/2011/11/jquery-selector-traversing/](http://www.detelu.com/blog/2011/11/jquery-selector-traversing/) 

  ![DOM](http://i.imgur.com/gEObO0k.png)

 **DOM要素の選択例**
 
 ```
$("form");       // HTMLの例：<form></form>
$(".className"); // HTMLの例：<div class="className"></div>
$("#formId");    // HTMLの例：<div id="formId"></div>
 ```
 
 **DOM要素を操作する関数**
 
 - 値の取得
 
jQuery構文  　         | 内容
--------------------- | -----------------
$("#target").text()   | 要素内の文字列を取得
$("#target").html()   | 要素内のHTMLを取得
$("#target").val()    | 要素内の値を取得（フォーム部品のみ）

 - 値の書き換え

jQuery構文  　             | 内容
---------------------     | -----------------
$("#target").text("値")   | 要素内の文字列を書き換え
$("#target").html("値")   | 要素内のHTMLを書き換え
$("#target").val("値")    | 要素内の値を書き換え（フォーム部品のみ）

**実践**

```index.html```

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Javascript Practice</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="main.js"></script>
    <link rel="stylesheet" href="default.css">
  </head>
  <body>
    <div class="viewarea">
      プログラムを書こう。
    </div>
  </body>
</html>

```

```default.css```

```
.viewarea {
  background: #2DA7E0;
  border: solid 1px;
  width: 400px;
  font-size: 12pt;
  padding: 10px;
}

```

--

**jQueryの基本構文 イベント編**

![DOM](http://i.imgur.com/mU6CFEw.png)

 ```
$("#button").click( function(){

	処理の内容
	
});
 ```
 1. id「button」の要素を選択して、
 2. この要素に「click」イベントを追加。
 3. 追加するイベントの内容は「function(){ 処理の内容 }」である。

**DOM読み込み後の処理**

次は、WebページのDOMの準備ができた直後に実行する処理の書き方です。いくつかの方法がありますので、その中から2つを示します。この処理は、それぞれjQueryの関数「ready()」と「$()」を利用します。

- 方法①

```
$(document).ready(function () {
    処理の内容
});

```

- 方法②

```
$(function () {
    処理の内容
});
```

この授業では、方法②を使ってプログラムを書きます。

**実践**

```index.html```

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Javascript Practice</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="main.js"></script>
    <link rel="stylesheet" href="default.css">
  </head>
  <body>
    <div class="viewarea" id="view">
      <p>プログラムを書こう。</p>
    </div>
    <div>
      <input type="button" id="execButton" value="実行">
    </div>
  </body>
</html>

```

```main.js```

```
$(function () {
    $("#button").click(function () {
      $(".viewarea").text("書き換えました。");
    });
});
```
--

**練習問題①**

[gif](http://i.imgur.com/oqPmSZn.gifv)

参考HTML

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Javascript Practice</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="main.js"></script>
    <link rel="stylesheet" href="default.css">
  </head>
  <body>
    <input type="text" id="text" value="">
    <input type="button" id="button" value="実行">
    <div class="viewarea" id="view">
      <p>プログラムを書こう。</p>
    </div>
  </body>
</html>
```

**練習問題②**

[gif](http://i.imgur.com/fySrPSZ.gifv)

