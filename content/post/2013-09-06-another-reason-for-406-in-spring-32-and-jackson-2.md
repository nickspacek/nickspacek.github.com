---
date: 2013-09-06T00:00:00Z
description: ""
tags: []
title: Another reason for 406 in Spring 3.2 and Jackson 2
url: /2013/09/06/another-reason-for-406-in-spring-32-and-jackson-2/
---

{% include JB/setup %}

Just as a quick note, make sure your POJO actually has some fields. I was
racking my brain, examining my config, and Googling fiercely when I
discovered that the reason I kept getting a 406 in my Spring MVC 3.2 project
was because I had just created a placeholder POJO with no fields.

Arg.
