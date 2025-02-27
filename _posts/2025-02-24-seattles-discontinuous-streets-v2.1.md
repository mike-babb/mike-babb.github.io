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

# [Known issues and errata](#known-issues-and-errata)
The goal of this project is to identify the discontinuities in streets is Seattle. A discontinuity presents differently depending on the mode of transporation in question: streets are a lot more accessible to pedestrians and bicycles than a car. A good way to think about these discontinuities is how they would appear as if navigating Seattle roadways in a vehicle. Accordingly, a component of the initial data processing involved removing the following road types: alleys, trails overpasses, interstates, state routes, rail, flyovers, streetcars, extensions, turns, highway ramps, and walkways. Some of these roads are not accessible by vehicle. And some of these roads are few in number and short in distance. Expect, of course, for the interstates and state routes. But those are largely continuous (and not that interesting for this project).

In this version of the project, I determined a unique street to be a combination of direction prefix (or suffix), street name, and street type. Under this schema, W GALER ST is not the same as GALER ST which is not the same as E GALER ST. While a street named GALER runs east to west across the city, there are ~~not (yet)~~ now connections between W GALER ST and GALER ST and connections between GALER ST and E GALER ST. ~~Something to address in v2.0.~~ *This has been addressed in v2.0!*

As is often the case with geospatial data, there are minor discrepancies between data sources pertaining to the same area. The webmap is from [OpenStreetMap](https://www.openstreetmap.org/) and the street network data is from the [City of Seattle](https://data-seattlecitygis.opendata.arcgis.com/datasets/783fd63545304bdf9d3c5f2065751614_0/explore). Far more often than not, the data align geospatially. However, sometimes the data do not align. These instances are rare and often the degree of misalignment is small. A solution is to use only data from OpenStreetMap. Perhaps for v2.0 I'll use data from OpenStreetMap. 

Current connectivity is mostly street-end to street-end because that is usually the shortest distance between two disconnected segments. Sometimes, however, the shortest edge connecting two discontinuous street segments is not street-end to street-end but street-end to mid-point. This is rare, but it has been observed upon visual inspection. [NetworkX](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.centrality.degree_centrality.html#networkx.algorithms.centrality.degree_centrality) provides tools to help refine identification of street-end to street-end connectivity. ~~Definitely something to incorporate in v2.0.~~ *This has been addressed in v2.0!*

Over the course of panning around the completed map and looking at added segments, I noticed odd connections between streets. The two images below are examples of this phenomenon.
<p float="left">
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_08_15th_ave_w.png" alt="15TH AVE W" width="319" height="400" /> 
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_09_sw_florida_st.png" alt="SW FLORIDA ST" width="597" height="400" />
</p>

This odd connectivity is because of data processing artifacts left in the original dataset from the City of Seattle. For 15TH AVE W, the three artifacts are to the west, east, and north of the actual road. For SW FLORIDA ST, there are two artifacts: one to the south and one to the nortwest of the actual road. These short segments are usually less than 50 feet. My sense is that these erroneous artifacts were created during an initial digitizing process. But that's only speculation. Other maps do not show segments with those names. This [file](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/data/streets_to_remove.txt) tracks these erroneous artifacts. ~~As of January 10, 2025, I have found 12 short segments and I have removed them for v1.0 and I will do so going forward.~~ I include this text and example graphics to help inform end-users about a potential source of odd-looking connectivities.*For v2.0, I have removed streets with the `segment type != 1`. This has removed hundreds of these stubby segments and made more consistent connectivies.*

For both v1.0 and especially v2.0, the connectivity is somewhat arbitrary. The rules for within-sector connectivity are based on street name, type, and direction prefix/suffix. This leads to a specific, straightforward connecivity logic. For cross-sector connecivity, only street name and type were considered. While this has created some odd connecivitions, I tried to be internally consistent and line up the various cross-sector connectivities based on a quasi-grid structure. Finally, if anything looks execptionally out of place or you have additional questions, please let me know. I am happy to address issues and provide additional clarifying information.