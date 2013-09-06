---
layout: post
title: "Another reason for 406 in Spring 3.2 and Jackson 2"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Just as a quick note, make sure your POJO actually has some fields. I was
racking my brain, examining my config, and Googling fiercely when I
discovered that the reason I kept getting a 406 in my Spring MVC 3.2 project
was because I had just created a placeholder POJO with no fields.

Arg.
