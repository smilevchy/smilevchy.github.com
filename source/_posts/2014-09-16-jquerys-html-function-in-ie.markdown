---
layout: post
title: "Problem with JQuery's html() function in IE"
date: 2014-09-16 21:20:02 +0800
comments: true
categories: JQuery
---

    <div id="container">
    </div>
	<div id="btnArea">
        <input type="button" value="clear" id="clearBtn" />
        <input type="button" value="add" id="addBtn" />
    </div>
		
<!-- more -->
		
	<script>
		$(function() {
			var tempDom = $("<span>hello world</span>");
			$("#container").append(tempDom);

			$("#btnArea").delegate("#clearBtn", "click", function(evt) {
				$("#container").html("");
			});

			$("#btnArea").delegate("#addBtn", "click", function(evt) {
				$("#container").append(tempDom);               
			});
		});
	</script>	
	
上面那段代码在 Chrome、Firefox 下运行时，能够得到期望的结果，而如果在 IE 浏览器下运行时，其输出行为与预料中的不一样(此时 tempDom 的文本节点会被删除掉，感觉像在tempDom 上调用了 html())。
为了 hack 这个问题，可以写成，预先把节点保存起来，在需要的时候就 clone 该节点来进行操作。

即：
    
	<script>
		$(function() {
			var tempDom = $("<span>hello world</span>");
			$("#container").append(tempDom.clone());

			$("#btnArea").delegate("#clearBtn", "click", function(evt) {
				$("#container").html("");
			});

			$("#btnArea").delegate("#addBtn", "click", function(evt) {
				$("#container").append(tempDom.clone());               
			});
		});
	</script>

这样没有什么效率，可以改成按需显示隐藏的方式(前提是符合项目需求)。