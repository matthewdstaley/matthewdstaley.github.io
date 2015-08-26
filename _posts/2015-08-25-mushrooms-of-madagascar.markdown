---
layout: post
title:  "Mushrooms of Madagascar"
date:   2015-08-25 10:03:32
categories: jekyll update
---
"Mushrooms of Madagascar" is a master's thesis project at San Francisco State University. She has traveled to Madagascar and collected data on the fungal biodiversity found there in the rainforests. You can read more about at her blog, [http://jackieshay.weebly.com/][http://jackieshay.weebly.com/].

I helped create a data visualization map of GPS coordinate locations of the collection sites she visited. The code below to produce such a map is written below using R-Studio.

{% highlight ruby %}
install.packages("dismo")
install.packages("rgdal")
install.packages("XML")
install.packages("sp")
install.packages("raster")
install.packages("maptools")
install.packages("rgeos")
install.packages("RgoogleMaps")

library(RgoogleMaps)
library(rgeos)
library(maptools)
library(raster)
library(sp)
library(dismo)
library(rgdal)
library(XML)

LatCord = c(-21.15237,
            -21.15440,
            -21.14255,
            -21.15413,
            -18.55422,
            -18.53231,
            -18.53082,
            -18.55530,
            -18.11504,
            -19.00328,
            -17.38242,
            -19.01444)

LonCord = c(47.25183,
            47.25116,
            47.23409,
            47.25253,
            48.30201,
            49.07490,
            49.07559,
            47.31350,
            47.17074,
            47.08300,
            49.29103,
            47.101852)

c = c(mean(LatCord), mean(LonCord))


map.mada = GetMap(center = c,
                  zoom = 6,
                  size = c(640,640),
                  SCALE =2,
                  GRAYSCALE = FALSE,
                  maptype = "terrain")

PlotOnStaticMap(map.mada,
                lat = LatCord,
                lon = LonCord,
                zoom = 6, cex = 3,
                pch = 20,
                col = c(rep("maroon3",
                            length(LonCord)-3),
                            rep("olivedrab",3 )),
                FUN = points, add = F)

legend(x = 110, y = -100, title = "Sample Sites",
       legend = c("2014", "2006"),
       x.intersp = 1,
       y.intersp = .6,
       cex = 1.3,
       pch = 20,
       pt.cex = 3,
       col = c("maroon3", "olivedrab"))
text(x = 120, y=-313, cex = 0.75,
     labels = "Map produced by M.D.Staley")

{% endhighlight %}
