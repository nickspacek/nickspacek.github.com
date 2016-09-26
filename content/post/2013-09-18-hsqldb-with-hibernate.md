---
categories:
- legacy hibernate unit testing
date: 2013-09-18T00:00:00Z
description: ""
tags:
- hibernate
- hsqldb
title: 'HSQLDB with Hibernate: User lacks privilege or object not found'
url: /2013/09/18/hsqldb-with-hibernate/
---

{% include JB/setup %}

I'm currently working to add unit tests to a project which currently has no
tests for its database query layer. Normally I wouldn't worry too much, but
there are some nasty queries that have cropped up over the years that could
benefit from some testing.

This project uses Hibernate and the custom queries are written mainly in some
MySQL-specific language. Part of the problem with adding tests has been that
the hbm2ddl tool hasn't been able to reliably generate the database schema due
to some strange approaches to ID generation and other MySQL-specific code.

I've managed to get the hbm2ddl operation running somewhat and am tackling
issues as they arise. After getting some basic tests to run, I decided to go
after one of the methods using custom SQL (in Hibernate lingo, createSQLQuery).
One issue that took a while to figure out was this join syntax:

{{< highlight sql >}}
SELECT * FROM TableA a
JOIN TableB b USING (tableId)
{{< / highlight >}}

Even though TABLEA and TABLEB both have the tableId column, I was getting
"User lacks privilege or object not found: TABLEB.TABLEID". Changing to this
syntax solved the problem:

{{< highlight sql >}}
SELECT * FROM TableA a
JOIN TableB b USING (a.tableId = b.tableId)
{{< / highlight >}}
