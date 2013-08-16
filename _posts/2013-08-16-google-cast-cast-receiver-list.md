---
layout: post
title: "Google Cast: cast-receiver-list"
description: ""
category: 
tags: []
---
{% include JB/setup %}

I've been playing around with the [Google Cast API](https://developers.google.com/cast/)
a little bit, specifically the
[Chrome Sender API](https://developers.google.com/cast/chrome_sender).

One thing any application will have in common is retrieving the list of
available senders and displaying them for the user to select from. As I
was playing with the API I decided to extract the code out into a module
and make it available for others to use.

In the beginning I was using jQuery for DOM manipulation, so the first
incaranation of the plugin uses jQuery. Since then I started playing
with AngularJS, having had only a little bit of experience with it. So
I thought it would be interesting to build a plugin for it as well.

[Here's the project page](https://github.com/nickspacek/cast-receiver-list).
Currently, there's only a very brief example of how to  use the plugins
and both still need lots of work. They're mostly there for a POC and as
some sample code to get started with the Chrome Sender API.

