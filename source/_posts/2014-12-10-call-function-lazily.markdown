---
layout: post
title: "Call function lazily"
date: 2014-12-10 10:19:10 +0800
comments: true
categories: JavaScript
---

某些场景下，在某些模块还未初始化完毕时就调用该模块的函数，可能会导致错误。这时候就需要延迟调用函数，等待该模块初始化完毕先再调用。

<!-- more -->

*. setTimeout 方法
	
	ready = false;
	
	this.func_to_be_called = function(params) {
		if (!ready) {
			setTimeout(function() {
				func_to_be_called(params);
			}, 100);
		}
	};
	
	var init = function() {
		// XXX
		
		ready = true;
	};
	
*. 缓存调用函数对象方法

    var ready = false;
    var waitings = [];
    var addWaiting = function (fn, param, cb) {
        waitings.push({
            fn: fn,
            param: param,
            cb: cb
        });
    };
    var noticeWaiting = function () {
        $.each(waitings, function (index, waiting) {
            waiting.fn(waiting.param, waiting.cb);
        });
        waitings = [];
    };
	
	this.func_to_be_called = function(params) {
		if (!ready) {
            addWaiting(function (params) {
                _this.func_to_be_called(params);
            }, params, null);
            return;
        }
	};
	
	var init = function() {
		// XXX
		
		ready = true;
		noticeWaiting();
	};
