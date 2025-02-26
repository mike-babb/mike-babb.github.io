---
layout: post
title: "Seattle's Discontinuous Streets: version 2.1"
date: 2025-02-24
categories: geospatial analysis, street network, GeoPandas, NetworkX, webmap
---

I [finished](https://github.com/mike-babb/seattle_streets) my project on identifying and visualizing Seattle's discontinuous street network!  
[SEE THIS PAGE FOR AN INTERACTIVE MAP OF V2 OF THE ADDED STREETS](/media/discontinuous_streets_v2.html)  
[SEE THIS PAGE FOR AN INTERACTIVE MAP OF V1 OF THE ADDED STREETS](/media/discontinuous_streets.html)  

See this [page](https://mike-babb.github.io/blog/2025/01/01/seattles-discontinuous-streets) for information on version 1.0.

The major change in version 2.0 is that I added the connections between city sectors. For example, there are now connections between W GALER ST and GALER ST and connections between GALER ST and E GALER ST.  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_12_overall_v2.png" alt="overall" width="500" height="443"/>  

In the image above, the blue lines are the cross-sector connections and the red lines are the within-sector connections. The connections across the various salt and fresh water bodies really stands out and emphasizes the quasi-grid structure as seen in Seattle's streets. That being said, Galer is probably a little hard to see in that image, so here it is by itself.  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_11_galer_v2.png" alt="overall" width="500" height="150"/>  

Version 2.0 of this project also features outlines of the various city sectors. The city sectors were created based on the street direction prefix and suffix.When hovering on a segment, all other segments are made transparent and the city sectors can been. 

The minor bump to version 2.1 features modest tweaks to the control flow and a great deal of added documention. The project's [README.md](link) describes the process and the output in great detail. There are also histograms of the different types of added segments. I'll include some highlights about the added within-sector (red) and cross-sector (blue) below:

* 2,453 uniquely named roads in the study area | 1,890 road miles: see these graphics for a comparison of [miles](/graphics/barplot_miles.png) and [road segments](/graphics/barplot_segment_count.png)  
* 1,145 roads without discontinuities | 312 road miles  
* 1,308 roads with discontinuities | 1,578 road miles  
* 3,617 within-sector segments added across 1,103 roads | 833 miles  
* 410 cross-sector segments added across 313 roads | 824 miles
* Average of ~3.3 within-sector segments added per uniquely named road  
* Average of ~1.3 cross-sector segments added per uniquely named road  
* Average added within-sector segment length: ~0.23 Miles  
* Average added cross-sector segment length: ~2.0 Miles  
* Median added within-segment length: ~448 Feet  
* Median added cross-segment length: ~1.1 Miles  
* Greatest number of within-sector segments added: [14 1ST AVE NW](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_14_most_added_segments_v2.png)  
* Longest within-sector segment: ~5 Miles:  [7TH PL S (10 longest added segments)](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_15_longest_added_segments_v2.png)  
* Shortest within-sector segment: ~4 Feet: [SW CLOVERDALE ST ](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_06_shortest_segment.png)  


