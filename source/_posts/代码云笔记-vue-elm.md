---
title: 代码云笔记-vue-elm
date: 2018-05-06 23:00:26
tags: codeNote 
categories: 
  - codeNote
---
## 关于localStorage

```
/**
 * 存储localStorage
 */
export const setStore = (name, content) => {
	if (!name) return;
	if (typeof content !== 'string') {
		content = JSON.stringify(content);
	}
	window.localStorage.setItem(name, content);
}

/**
 * 获取localStorage
 */
export const getStore = name => {
	if (!name) return;
	return window.localStorage.getItem(name);
}

/**
 * 删除localStorage
 */
export const removeStore = name => {
	if (!name) return;
	window.localStorage.removeItem(name);
}
```

## 关于px转换rem

```
(function(doc, win) {
    var docEl = doc.documentElement,
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function() {
            var clientWidth = docEl.clientWidth;
            if (!clientWidth) return;
            docEl.style.fontSize = 20 * (clientWidth / 320) + 'px';
        };
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
```
## 关于fastclick.js

FastClick 是一个简单，易于使用的JS库用于消除在**移动浏览器**上触发click事件与一个物理Tap(敲击)之间的300延迟。让你的应用程序更加灵敏迅捷。

```
import FastClick from 'fastclick'

if ('addEventListener' in document) {
    document.addEventListener('DOMContentLoaded', function() {
        FastClick.attach(document.body);
    }, false);
}
```

## 获取style样式

```
/**
 * 获取style样式
 */
export const getStyle = (element, attr, NumberMode = 'int') => {
    let target;
    // scrollTop 获取方式不同，没有它不属于style，而且只有document.body才能用
    if (attr === 'scrollTop') { 
        target = element.scrollTop;
    }else if(element.currentStyle){
        target = element.currentStyle[attr]; 
    }else{ 
        target = document.defaultView.getComputedStyle(element,null)[attr]; 
    }
    //在获取 opactiy 时需要获取小数 parseFloat
    return  NumberMode == 'float'? parseFloat(target) : parseInt(target);
} 
```
## 获取数据


```
import {
	baseUrl
} from './env'

export default async(url = '', data = {}, type = 'GET', method = 'fetch') => {
	type = type.toUpperCase();
	url = baseUrl + url;

	if (type == 'GET') {
		let dataStr = ''; //数据拼接字符串
		Object.keys(data).forEach(key => {
			dataStr += key + '=' + data[key] + '&';
		})

		if (dataStr !== '') {
			dataStr = dataStr.substr(0, dataStr.lastIndexOf('&'));
			url = url + '?' + dataStr;
		}
	}

	if (window.fetch && method == 'fetch') {
		let requestConfig = {
			credentials: 'include',
			method: type,
			headers: {
				'Accept': 'application/json',
				'Content-Type': 'application/json'
			},
			mode: "cors",
			cache: "force-cache"
		}

		if (type == 'POST') {
			Object.defineProperty(requestConfig, 'body', {
				value: JSON.stringify(data)
			})
		}
		
		try {
			const response = await fetch(url, requestConfig);
			const responseJson = await response.json();
			return responseJson
		} catch (error) {
			throw new Error(error)
		}
	} else {
		return new Promise((resolve, reject) => {
			let requestObj;
			if (window.XMLHttpRequest) {
				requestObj = new XMLHttpRequest();
			} else {
				requestObj = new ActiveXObject;
			}

			let sendData = '';
			if (type == 'POST') {
				sendData = JSON.stringify(data);
			}

			requestObj.open(type, url, true);
			requestObj.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
			requestObj.send(sendData);

			requestObj.onreadystatechange = () => {
				if (requestObj.readyState == 4) {
					if (requestObj.status == 200) {
						let obj = requestObj.response
						if (typeof obj !== 'object') {
							obj = JSON.parse(obj);
						}
						resolve(obj)
					} else {
						reject(requestObj)
					}
				}
			}
		})
	}
}
```

## 判断系统

```
//判断系统
        let u = navigator.userAgent;
        let isAndroid = u.indexOf('Android') > -1 || u.indexOf('Linux') > -1; //g
        let isIOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
        if (isAndroid) {
            this.system = 'Android';
        } else if (isIOS) {
            this.system = 'IOS';
        } else {
            this.system = 'pc';
        }
```

## 关于common.css

```
body, div, span, header, footer, nav, section, aside, article, ul, dl, dt, dd, li,
a, p, h1, h2, h3, h4, h5, h6, i, b, textarea, button, input, select, figure, figcaption, {
    padding: 0;
    margin: 0;
    list-style: none;
    font-style: normal;
    text-decoration: none;
    border: none;
    color: #333;
    font-weight: normal;
    font-family: "Microsoft Yahei";
    box-sizing: border-box;
    -webkit-tap-highlight-color:transparent;
    -webkit-font-smoothing: antialiased;
    &:hover{
        outline: none;
    }
}

html,body{
    height: 100%;
    width: 100%;
    background-color: #F5F5F5;
}

.clear:after{
    content: '';
    display: block;
    clear: both;
}

.clear{
    zoom:1;
}

.back_img{
    background-repeat: no-repeat;
    background-size: 100% 100%;
}

.margin{
    margin: 0 auto;
}

.left{
    float: left;
}

.right{
    float: right;
}

.hide{
    display: none;
}

.show{
    display: block;
}

.ellipsis{
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
```

## sass宏
```
// 背景图片地址和大小
@mixin bis($url) { 
	background-image: url($url);
	background-repeat: no-repeat;
	background-size: 100% 100%;
}

//边框圆角
@mixin borderRadius($radius) {
    -webkit-border-radius: $radius;
    -moz-border-radius: $radius;
    -ms-border-radius: $radius;
    -o-border-radius: $radius;
    border-radius: $radius;
}
//定位全屏
@mixin allcover{
	position:absolute;
	top:0;
	right:0;
}

//定位上下左右居中
@mixin center {  
	position: absolute;
	top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

//定位上下居中
@mixin ct {  
	position: absolute;
	top: 50%;
    transform: translateY(-50%);
}

//定位左右居中
@mixin cl {  
	position: absolute;
	left: 50%;
    transform: translateX(-50%);
}

//宽高
@mixin wh($width, $height){
	width: $width;
	height: $height;
}

//字体大小、行高、字体
@mixin font($size, $line-height, $family: 'Microsoft YaHei') {  
	font: #{$size}/#{$line-height} $family;
}

//字体大小，颜色
@mixin sc($size, $color){
	font-size: $size;
	color: $color;
}
```

