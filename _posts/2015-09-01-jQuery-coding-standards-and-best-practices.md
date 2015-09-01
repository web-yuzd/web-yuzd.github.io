---
layout: post
title: "jQuery编程的最佳实践"
description: "jQuery编程的最佳实践"
category: ['jQuery', 'code']
tags: ['技巧']
---
{% include JB/setup %}

jQuery是我们工作中经常用到的库，如何更好的使用jQuery，更好的提升网页的性能，一直都是我们需要面对的问题，下面是收藏的一些关于jQuery编程的最佳实践，记录下来，以供自己以后能够反复阅读，避免再掉进相同的坑里。。。

### 加载jQuery

1.坚持使用CDN来加载jQuery，这种别人服务器免费帮你托管文件的便宜干嘛不占呢，国内的可以使用百度CDN。

    <script type="text/javascript" src="//apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
     
    <script>window.jQuery || document.write('<script src="js/jquery-1.11.0.min.js" type="text/javascript"><\/script>')</script>


2.安全起见，最好还是提供一个本地备份以便在无法从远程CDN服务器获取jQuery时网站也能工作，如上面代码所示。[详情见此](https://css-tricks.com/snippets/jquery/fallback-for-cdn-hosted-jquery/),css-tricks网站上讲的关于本地备份jQuery。

3.使用裸协议的URL（也就是说去掉http:或者https:），如上面代码展示的那样。

4.如果可能，尽量将你的javascript和jQuery代码放到页面底部。

5.该使用哪个版本？

* 如果你想兼容IE678请表用2.x的版本
* 针对极少数不用考虑兼容性的幸运儿，极力推荐使用最新版本的jQuery
* 当从CDN服务器加载jQuery时，最好把版本写全（比如1.11.0而不是1.11或者直接写个1）
* 千万莫重复加载

6.如果你同时还使用了其他JS框架诸如Prototype, MooTools, Zepto云云，因为他们也使用了$符号，所以你就表再用美刀符号来进行jQuery 编码了，而请用“jQuery”代替。并且调用$.noConflict()保证不会有冲突出现。

7.要检测浏览器对一些新特性是否支持，请用[Modernizr](http://modernizr.com/)。

### 关于变量

1.jQuery类型的变量最好加个$前缀。

2.时常将jQuery选择器返回的内容存进变量以便重用。

	var $products = $("div.products"); // 慢
	var $products = $(".products"); // 快

3.使用驼峰命名

### 关于选择器

1.尽量ID选择器。其背后机理其实是调用原生的document.getElementById()，所以速度较其他选择器快。

2.使用类选择器时表指定元素的类型。

	var $products = $("div.products"); // 慢
	var $products = $(".products"); // 快

3.ID父亲容器下面再查找子元素请用.find()方法。这样做快的原因是通过id选择元素不会使用Sizzle引擎。

4.多级查找中，右边尽量指定得详细点而左边则尽量简单点。[了解更多](http://learn.jquery.com/performance/optimize-selectors/)

	// 丑陋
	$("div.data .gonzalez");
	 
	// 优化后
	$(".data td.gonzalez");

5.避免冗余。

	$(".data table.attendees td.gonzalez");
	 
	// 好的方式：去掉了中间的冗余
	$(".data td.gonzalez");

6.指定选择的上下文。

	// 劣质的代码：因为需要遍历整个DOM来找到.class
	$('.class');
	 
	// 高品代码：因为只需在指定容器范围内进行查找
	$('.class', '#class-container');

7.表使用万能选择器。

	$('div.container > *'); // 差
	$('div.container').children(); // 棒

8.警惕隐式的万能选择器。省略的情况下其实使用的就是*号通配符。

	$('div.someclass :radio'); // 差
	$('div.someclass input:radio'); // 棒
 
9.ID已经表示唯一了，背后使用的是document.getElementById()，所以表跟其他选择器混搭了。

	$('#outer #inner'); // 脏
	$('div#inner'); // 乱
	$('.outer-container #inner'); // 差
	$('#inner'); // 干净利落，后台只需调用document.getElementById()

### DOM操作相关

1.操作任何元素前先将其从文档卸载，完了再贴回去。

	var $myList = $("#list-container > ul").detach();
	//...一大堆对$myList的处理
	$myList.appendTo("#list-container");

2.代码里将HTML组织好后再一次性贴到DOM中去。

	// 这样不好
	var $myList = $("#list");
	for(var i = 0; i < 10000; i++){
	    $myList.append("<li>"+i+"</li>");
	}
	 
	// 这样好
	var $myList = $("#list");
	var list = "";
	for(var i = 0; i < 10000; i++){
	    list += "<li>"+i+"</li>";
	}
	$myList.html(list);
	 
	// 但这样更好
	var array = []; 
	for(var i = 0; i < 10000; i++){
	    array[i] = "<li>"+i+"</li>"; 
	}
	$myList.html(array.join(''));


3.不要处理不存在的元素。

	// 无良的做法：jQuery后台要跑完三个函数后才会知道这个元素其实根本不存在
	$("#nosuchthing").slideUp();
	// 应该这样
	var $mySelection = $("#nosuchthing");
	if ($mySelection.length) {
	    $mySelection.slideUp();
	}

### 事件相关

1.一个页面只写一个文档ready事件的处理程序。这样代码既清晰好调试，又容易跟踪代码的进程。

2.表用匿名函数来做事件的回调。匿名函数不易调试维护测试和复用。

	$("#myLink").on("click", function(){...}); // 表这样
	 
	// 这样
	function myLinkClickHandler(){...}
	$("#myLink").on("click", myLinkClickHandler);

3.处理文档ready事件的回调也表用匿名函数，匿名函数不易调试维护测试和复用

	$(function(){ ... }); // 糟糕的做法：无法利用此函数也无法为其写测试用例
	 
	// 好的做法
	$(initPage); // 抑或 $(document).ready(initPage);
	function initPage(){
	    // 这里你可以进行程序的初始化了
	}

4.进一步，最好也将ready事件的处理程序放到外部文件中引入到页面，而页面中内嵌的代码只需调用即可。

	<script src="my-document-ready.js"></script>
	<script>
	    // 初始化一些必要的全局变量
	    $(document).ready(initPage); // 抑或 $(initPage);
	</script>

5.千万表写内联到HTML的JS代码，这是调试的梦魇！应该总是用jQuery来绑定事件自带程序，这样也方便随时动态地取消绑定。

	<a id="myLink" href="#" onclick="myEventHandler();">my link</a> <!--不好 -->
	```
	```javascript
	$("#myLink").on("click", myEventHandler); // GOOD

6.如果可能尽量在绑定事件处理程序时使用一个命名空间，这样可以方便地取消绑定而不会影响其他绑定。

	$("#myLink").on("click.mySpecialClick", myEventHandler); // 不错
	// 之后，让我们优雅地解除绑定
	$("#myLink").unbind("click.mySpecialClick");

### 异步操作

1.直接用$.ajax()而表去用.getJson() 或 .get(),因为jQuery内部还是将其转为前者

2.表对HTTPS站点使用HTTP去发起请求，最好干脆就表指定（将HTTP或者HTTPS从你的URL中移除）

3.表在链接里面嵌参数，请使用专门的参数设置来传递

	// 不易阅读的代码...
	$.ajax({
	    url: "something.php?param1=test1&param2=test2",
	    ....
	});
	 
	// 更易阅读...
	$.ajax({
	    url: "something.php",
	    data: { param1: test1, param2: test2 }
	});

4.尽量指明数据类型以便你自己清楚要处理什么样的数据（见下方会提到的Ajax模板）

5.对于异步动态加载的内容，最好使用代理来绑定事件处理程序。这样的好处是对于之后动态加载的元素事件同样有效。
	
	$("#parent-container").on("click", "a", delegatedClickHandlerForAjax);

6.使用Promise模式。

	$.ajax({ ... }).then(successHandler, failureHandler);
	 
	// 抑或
	var jqxhr = $.ajax({ ... });
	jqxhr.done(successHandler);
	jqxhr.fail(failureHandler);

7.标准的Ajax模板一分。

	var jqxhr = $.ajax({
	    url: url,
	    type: "GET", // 默认为GET,你可以根据需要更改
	    cache: true, // 默认为true,但对于script,jsonp类型为false,可以自行设置
	    data: {}, // 将请求参数放这里.
	    dataType: "json", // 指定想要的数据类型
	    jsonp: "callback", // 指定回调处理JSONP类型的请求
	    statusCode: { // 如果你想处理各状态的错误的话
	        404: handler404,
	        500: handler500
	    }
	});
	jqxhr.done(successHandler);
	jqxhr.fail(failureHandler);

### 动画与特效

1.保持一个始终如一风格统一的动画实现

2.紧遵用户体验，表滥用动画特效

* 使用简洁的显示隐藏，状态切换，滑入滑出等效果来展示元素
* 使用预设值来设置动画的速度’fast’，’slow’，或者400（中等速度）

### 插件相关

1.始终选择一个有良好支持，完善文档，全面测试过并且社区活跃的插件

2.注意所用插件与当前使用的jQuery版本是否兼容

3.一些常用功能应该写成jQuery插件。一分jQuery插件的编写模板

### 链式句法

1.除了用变量将jQuery选择器返回的结果保存，还可以利用好链式调用。

	$("#myDiv").addClass("error").show();

2.当链式调用多达3次以上或代码因绑定回调略显复杂时，使用换行和适当的缩进来提高代码的可读性。
	
	$("#myLink")
	    .addClass("bold")
	    .on("click", myClickHandler)
	    .on("mouseover", myMouseOverHandler)
	    .show();

3.对于特别长的调用最好还是用变量保存下中间结果来简化代码。

### 其他

1.使用对象字面量来传递参数

	$myLink.attr("href", "#").attr("title", "my link").attr("rel", "external"); // 糟糕：调用了三次attr
	// 不错，只调用了一次attr
	$myLink.attr({
	    href: "#",
	    title: "my link",
	    rel: "external"
	});

2.表将CSS与jQuery杂揉

	$("#mydiv").css({'color':red, 'font-weight':'bold'}); // 不好
	
	
	.error {/* 不错 */
	    color: red;
	    font-weight: bold;
	}
	
	$("#mydiv").addClass("error");


3.时刻关注官方Changelog，表使用摒弃了的方法。

4.适时地使用原生javascript。一些与此有关的性能比较
	
	$("#myId"); // 多少还是会逊色于...
	document.getElementById("myId");
