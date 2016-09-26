+++
date = "2016-09-26T11:23:10-03:00"
title = "GeoNB Mobile"

+++

I was messing around with [GeoNB](http://www.snb.ca/geonb1/), checking
out what it was built on top of with the hope that maybe there was a way
to get some data out of it programmatically. The underlying data is very
open, with the government of New Brunswick releasing it in a number of
different formats.

Before going that route too far, I thought it would be neat to try using
[OpenLayers](http://openlayers.org/) to display the data if possible. It
ended up being very easy to modify one of the existing examples to work
with the ArcGIS APIs that are supporting the GeoNB site. You can check
out the result below:

<div style="height: 500px">
  <!--<script async src="//jsfiddle.net/nickspacek/f3hsdqkL/1/embed/result/"></script>-->
  <iframe width="100%" height="500"
    src="//jsfiddle.net/nickspacek/f3hsdqkL/3/embedded/result/"
    allowfullscreen="allowfullscreen" frameborder="0"></iframe>
</div>

The yellow outlining is provided by the GeoNB server's parcel boundaries
data. Next steps are adding in the parcel information lookup and display.
