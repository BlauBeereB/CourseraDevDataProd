---
title: "Coursera Developing Data Products Week 2"
author: ""
date: "19 Juli 2020"
output: html_document
---

```{r label = "setup", include = FALSE}
knitr::opts_chunk$set(echo = FALSE)
knitr::opts_chunk$set(warning = FALSE)
```

## Random points on a world map

This map visualizes random points on a world map in a clustered fashion and 
with generic popup names.

```{r label = "MyMap"}
library(leaflet) 

num_pts <- 1000
my_pts <- data.frame(lat = runif(num_pts, min = -60, max = 80), 
                     lng = runif(num_pts, min = -180, max = 180), 
                     name = paste0("Random Point ", 1:num_pts))
my_pts %>% 
  leaflet() %>% 
  addTiles() %>% 
  addMarkers(lat = my_pts$lat, lng = my_pts$lng, popup = my_pts$name, 
             clusterOptions = markerClusterOptions())
```

