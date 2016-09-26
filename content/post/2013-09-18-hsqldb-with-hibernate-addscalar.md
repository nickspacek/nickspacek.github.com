---
categories:
- legacy hibernate unit testing
date: 2013-09-18T00:00:00Z
description: ""
tags:
- hibernate
- hsqldb
title: 'HSQLDB with Hibernate: addScalar'
url: /2013/09/18/hsqldb-with-hibernate-addscalar/
---

{% include JB/setup %}

To continue this series, I just have another little cautionary bit of advice
regarding using `addScalar` with your `createSQLQuery(...)` operations. In
MySQL, a query like this:

{{< highlight sql >}}
SELECT obj.name, other.name, third.name
FROM obj, other, third
{{< / highlight >}}

Will give the full name of those columns in the "result set metadata" that
Hibernate accesses. So when you use `addScalar`, you can just say:

{{< highlight java >}}
.addScalar("obj.name")
.addScalar("other.name")
.addScalar("third.name")
{{< / highlight >}}

However, in other database engines the columns might come back in the metadata
as `[ name, name, name ]`; when you try to use `addScalar` with the full path,
you will get an error. (I don't believe that just calling `addScalar` once with
"name" will apply to each of the three occurrences either, but I haven't
checked).

The way I solved it for HSQLDB isn't rocket science:

{{< highlight sql >}}
SELECT obj.name objName, other.name otherName, third.name thirdName
FROM obj, other, third
{{< / highlight >}}
