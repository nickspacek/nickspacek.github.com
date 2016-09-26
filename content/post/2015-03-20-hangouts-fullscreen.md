---
date: 2015-03-20T00:00:00Z
description: ""
tags: []
title: Hangouts Screen Share in Full Screen
url: /2015/03/20/hangouts-fullscreen/
---

{% include JB/setup %}

**Edit**: I came across [this extension](https://chrome.google.com/webstore/detail/toggle-fullscreen-in-hang/eekfhcmpmchbhkdeplplcljcggddkffb?hl=en)
which I assume accomplishes something similar, nice.

So I was messing around in a Hangouts session today trying to increase the
other user's screen share size, and I noticed a few HTML elements that
controlled the size. I discovered that you can easily resize the video feed.

The best approach would be an extension to handle finding the proper elements
and also hooking into some events, but a simple PoC can be seen below:

{{< highlight javascript >}}

var leftId = ':v8.Sh';
var sizeIds = [leftId, ':v8.Wh', ':v8.Xh', ':v8.Th'];
var height = window.innerHeight + 'px';
var width = window.innerWidth + 'px';

function resize(id) {
    var el = document.getElementById(id);
    el.style.width = width;
    el.style.height = height;
}

function shift(id) {
    var el = document.getElementById(id);
    el.style.left = '0px';
}

sizeIds.forEach(resize);
shift(leftId);

{{< / highlight >}}
