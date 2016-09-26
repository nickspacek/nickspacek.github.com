---
layout: post
title: "Spring Boot web application"
description: "Some experiences with Spring Boot"
category: spring
tags: ['spring-boot', 'spring-mvc']
---
{% include JB/setup %}

So I tried out Spring Boot in a new project. I have to say that I like the
idea of making Spring more accessible to a broader audience. I did come
across a few things that really sucked up some time.

### Serving up JSPs

In Spring MVC it's pretty standard to have your View based on JSPs. There are
other engines you can plug in to display your views of course, but most people
are used to JSPs. Support is standard in JEE/Servlet land anyways. Plus they
don't really require any unexpected dependencies or much configuration at all.
Usually.

I had a heck of a time figuring out why my application was saying it couldn't
find the index.jsp I had faithfully stuck in my **/src/main/webapp/WEB-INF**
directory, and configured as such in the `ApplicationContext`. I headed to
Google looking for 'spring mvc "No mapping found for HTTP request"' but to my
chagrin came up pretty empty. Finally in an unrelated post (that I can no
longer find) someone had a code snippet like this:

    static class WebConfiguration extends DelegatingWebMvcConfiguration {
      // ...

      @Override
      protected void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
        configurer.enable();
      }
    }

As it turns out, the default servlet is not enabled by default, meaning that
only requests matching the dispatcherServlet are handled (and these only
include Spring Controllers and the like). The default servlet is responsible
for handling other requests, such as static content and the contents of the
WEB-INF folder (internally only).

So with that solved, I ran into my next problem.

### Rendering JSPs

Now my JSPs were not getting rendered, they were only showing the file
contents. This one didn't take as long to track down, only a hour or so. The
embedded Tomcat being used by Spring Boot (the default servlet container) does
not include JSP rendering by default. To include it, you need to have the
Tomcat embedded Jasper library on your classpath (it is automatically
detected). You can do this via Maven like so:

    <dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-jasper</artifactId>
        <scope>provided</scope>
    </dependency>

And there we have it. Hopefully this is useful to someone else.
