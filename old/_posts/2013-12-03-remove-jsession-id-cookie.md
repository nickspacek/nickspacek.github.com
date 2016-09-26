---
layout: post
title: "Remove JSESSION ID cookie"
description: ""
category: 
tags: ['bookmarklet', 'js']
---
{% include JB/setup %}

I made a simple little bookmarklet that will remove the JSESSIONID cookie (for
testing purposes). We are using it to test behavior of AJAX updates when the
session expires.

Here it is, drag to your bookmarks: <a href="javascript:!function(){function createCookie(name,value,days){if(days){var date=new Date;date.setTime(date.getTime()+24*days*60*60*1e3);var expires='; expires='+date.toGMTString()}else var expires='';document.cookie=name+'='+value+expires+'; path=/'}function readCookie(name){var nameEQ=name+'=';var ca=document.cookie.split(';');for(var i=0;i&lt;ca.length;i++){var c=ca[i];while(' '==c.charAt(0))c=c.substring(1,c.length);if(0==c.indexOf(nameEQ))return c.substring(nameEQ.length,c.length)}return null}function eraseCookie(name){createCookie(name,'',-1)}var target='JSESSIONID';if(null==readCookie(target)){alert('No cookie named '+target+' found');return}if(confirm('Do you want to delete the cookie named '+target+'?'))eraseCookie(target)}();">-JSESSIONID</a>

**This makes use of [Peter-Paul Koch's code from quirksmode.com](http://www.quirksmode.org/js/cookies.html)**
