---
title: JavaScriptリファレンスを高速検索するKeySnailプラグイン
author: azu
layout: post
permalink: /2011/0606/res2830/
SBM_count:
  - '00014<>1355420365<>14<>0<>0<>0<>0'
  - '00014<>1355420365<>14<>0<>0<>0<>0'
  - '00014<>1355420365<>14<>0<>0<>0<>0'
dsq_thread_id:
  - 322932727
categories:
  - KeySnail
tags:
  - javascript
  - KeySnail
  - リファレンス
  - 検索
---
[JSReference][1]というFIrefoxアドオンである[KeySnail][2]上で動くプラグインの紹介

このプラグインは[Chemr-js][3]のように先にリファレンスサイトのインデックスのキャッシュを作っておいて、複数のリファレンスからまとめて検索をすることができるプラグインです。



動画だと対応サイトが少ないですが、現在は以下のサイトに対応しています。   
(最新の対応サイトリストは[JSReference at master from azu/KeySnail-Plugins &#8211; GitHub][1]を参照してください)

*   [developer.mozilla.org][4]
*   [jp.developer.mozilla.org][5]
*   [www2u.biglobe.ne.jp/~oz-07ams/prog/ecma262r3/][6]
*   [api.jquery.com][7]
*   [es5.github.com][8]
*   [msdn.microsoft.com][9]

ECMAScriptの仕様書、MDCのドキュメント、jQueryのAPIドキュメント、IEのJavaScriptリファレンスなどを同時に引けるので結構便利です。[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="image" src="http://efcl.info/wp-content/uploads/2011/06/image_thumb8.png" border="0" alt="image" width="640" height="116" />][10]

対応サイトもSITEINFO的なものを書けば増やせるので、[JSReference at master from azu/KeySnail-Plugins &#8211; GitHub][1]を参考に見てみるといいです。

プラグインをインストールするとプラグインマネージャーにドキュメントが表示されるので、そこに使い方が書いてありますが簡単に説明すると二つのコマンドが追加されます。

<table border="1" cellspacing="0" cellpadding="2" width="446">
  <tr>
    <td width="200" valign="top">
      JsReferrence-open-prompt
    </td>
    
    <td width="244" valign="top">
      JsReferrenceで検索を開始する
    </td>
  </tr>
  
  <tr>
    <td width="200" valign="top">
      JsReferrence-reIndex
    </td>
    
    <td width="244" valign="top">
      JsReferrenceのインデックスを作り直す
    </td>
  </tr>
</table>

このコマンドをKeySnailの設定メニューや_keysnail.jsファイルに直接書き込むなどでショートカットに割り当てて使います。

[<img style="background-image: none; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="image" src="http://efcl.info/wp-content/uploads/2011/06/image_thumb9.png" border="0" alt="image" width="240" height="88" />][11]   
設定画面の場合

<div>
  <pre id="codeSnippet" class="csharpcode">key.setGlobalKey(['C-b', 'j'], function (ev, arg) {
    ext.exec(<span class="str">"JsReferrence-open-prompt"</span>, arg, ev)<span class="rem">;</span>
<span class="rem">}, 'JsReferrenceのプロンプトを開く', true);</span>
key.setGlobalKey(['C-b', 'r'], function (ev, arg) {
    ext.exec(<span class="str">"JsReferrence-reIndex"</span>, arg, ev)<span class="rem">;</span>
}, 'JsReferrenceののインデックスを作り直す', <span class="kwrd">true</span>);</pre>
</div>

<div>
  _keysnail.jsファイルに書き込まれる内容。
</div>

<div>
</div>

<div>
  これらのコマンドは引数を受け取ることができて、ドメイン(上のリストで書かれている<a href="http://es5.github.com/">es5.github.com</a>といったサイトの固有なもの)を配列で渡すことで、それぞれそれらのサイトを対象にした動作になります。
</div>

<div>
  デフォルトだとすべてのサイトを対象するので、ドメインを指定したものを_keysnail.jsで複数のショートカットに割り当てれば、グループに分別でプロンプトから検索するなども可能です。
</div>

<div id="codeSnippetWrapper">
  <pre id="codeSnippet" class="csharpcode">// 二つのサイトを候補にする - JavaScript
key.setGlobalKey(['C-b', 'l'], function (ev, arg) {
    ext.exec(<span class="str">"JsReferrence-open-prompt"</span>, [<span class="str">"developer.mozilla.org"</span>, <span class="str">"www2u.biglobe.ne.jp/~oz-07ams/prog/ecma262r3/"</span>], ev)<span class="rem">;</span>
<span class="rem">}, 'JsReferrenceのプロンプトを開く', true);</span>
// msdn.microsoft.comのインデックスだけを再構築する
key.setGlobalKey(['C-b', 'r'], function (ev, arg) {
    ext.exec(<span class="str">"JsReferrence-reIndex"</span>, [<span class="str">"msdn.microsoft.com"</span>], ev)<span class="rem">;</span>
}, 'JsReferrenceのプロンプトを開く', <span class="kwrd">true</span>);</pre>
</div>

<div>
  また、これはKeySnailの設定になりますが、<a href="https://github.com/mooz/keysnail/wiki/Customizing-(Japanese)">Customizing (Japanese) &#8211; GitHub</a>を読んで、プロンプトの設定をしてC-Enterで連続的にサイトを開くなどできるようにするととても便利になります。
</div>

<div>
</div>

<div>
  KeySnailのプロンプトはとてもできがいいので、前から言っていますがこれのためだけにKeySnailを使うのもありだと思います。<a href="https://github.com/mooz/keysnail/wiki/plugin">Plugin</a>のHatebnailのはてなブックマーク検索やすべてのタブからGrep検索する事ができる<a href="https://gist.github.com/raw/905297/find.ks.js">Find</a>などはものすごくプロンプトと相性がいいです。
</div>

<div>
  リファレンスは何度も見ると思うので、この部分を早くできるようになるとストレスが減ってとてもいいので是非試してみてください。
</div>

<div>
</div>

<div>
  右クリックからインストール→<a href="https://github.com/azu/KeySnail-Plugins/raw/master/JSReference/js-referrence.ks.js">https://github.com/azu/KeySnail-Plugins/raw/master/JSReference/js-referrence.ks.js</a>
</div>

*   [KeySnail][2]
*   [JSReference at master from azu/KeySnail-Plugins &#8211; GitHub][1]
*   [KeySnailプラグイン開発の方法とデバッグ | Web scratch][12]

 [1]: https://github.com/azu/KeySnail-Plugins/tree/master/JSReference
 [2]: https://github.com/mooz/keysnail/wiki/keysnail-japanese
 [3]: http://subtech.g.hatena.ne.jp/cho45/20100901/1283268146
 [4]: http://developer.mozilla.org
 [5]: https://developer.mozilla.org/ja
 [6]: http://www2u.biglobe.ne.jp/%7Eoz-07ams/prog/ecma262r3/
 [7]: http://api.jquery.com
 [8]: http://es5.github.com/
 [9]: http://msdn.microsoft.com/en-us/library/yek4tbz0%28v=VS.94%29.aspx
 [10]: http://efcl.info/wp-content/uploads/2011/06/image8.png
 [11]: http://efcl.info/wp-content/uploads/2011/06/image9.png
 [12]: http://efcl.info/2011/0402/res2453/