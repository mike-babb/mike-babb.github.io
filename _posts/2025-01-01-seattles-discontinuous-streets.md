---
layout: post
title: "Identifying Seattle's Discontinuous Streets"
date: 2025-01-01
categories: geospatial analysis, street network, GeoPandas, NetworkX, webmap
---

# Visualizing Street Discontinuities
I just [published](https://github.com/mike-babb/seattle_streets) a project identifying and visualizing Seattle's discontinuous street network. Briefly, streets in Seattle start, stop, and resume. A street will run for a few blocks, stop, and then resume with the same name. While this happens throughout the city, I was curious as to how common or not it is and I wanted to visualize the gaps in each named street. After working on this intermittently for the past six months, I was able to create this map:  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_02_overall.png" alt="overall" width="500" height="565"/>  

[SEE THIS PAGE FOR AN INTERACTIVE MAP OF THE ADDED STREETS](/media/discontinuous_streets.html)

In the image above, the red lines are the missing/added connections between streets and the black lines are the existing streets with discontinuities. (In the interactive map, there are green lines representing continuous streets). This map was a lot of fun to make and it was incredible to see represented visually what I long sensed about navigating the city: 
the streets are disconnected, a little chaotic, and getting around this city can be challenging. When I first started this project, I had assumed that I could create a solution using only geospatial tools. That proved to be complicated - if not impossible - as it required a lot of guess-and-check proceedures to see if the correct segments were being joined. After some trial and error, I realized that I was quasi-recreating known graph analysis techniques so I turned to NetworkX to help with the analysis. And in doing so, the analysis became much easier, much quicker, and required a lot less code. It's always nice when that happens. Right tool for the right job, as they say...

Several facts about these added streets:

* 2,497 roads in the study area || 1,932 road miles: see these graphics for a comparison of [miles](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/barplot_miles.png) and [road segments](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/barplot_segment_count.png)  
* 1,362 roads without discontinuities || 437 road miles  
* 1,135 roads with discontinuities || 1,495 road miles  
* 3,632 segments added across 1,135 roads || 832 miles   
* Average of ~3.2 segments added per uniquely named road
* Average added segment length: [~0.23 Miles (histogram of the added segments)](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/histogram_ALL_streets.png)  
* Median added segment length: ~443 Feet
* Greatest number of segments added: [14 (1ST AVE NW, 30TH AVE S, 35TH AVE S, W RAYE ST)](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_04_most_added_segments.png)
* Longest segment: ~5 Miles:  [7TH PL S (10 longest segments)](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_05_longest_added_segments.png)
* Shortest segment: ~4 Feet: [SW Cloverdale ST ](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_06_shortest_segment.png)

I particularly like the image of SW Cloverdale ST because it exemplifies how connectivity is in part a function of mode of travel. Clearly, a pedestrian can navigate around that barrier while a vechicle cannot.

I'll encourage those interested to take look at the project's [README.md](https://github.com/mike-babb/seattle_streets/blob/main/README.md) or this [slide deck](https://github.com/mike-babb/seattle_streets/blob/main/seattles_disconnected_streets_2024_11_20.pptx) for more detailed information on the data driving this project, the python libraries ([GeoPandas](https://geopandas.org/en/stable/getting_started/introduction.html) and [NetworkX](https://networkx.org/), in particular) and techniques I used to identify the gaps in Seattle streets. To that end, the code and the data used to identify the disconnected streets is [available](https://github.com/mike-babb/seattle_streets/blob/main/README.md). 

# [Known issues and errata](#known-issues-and-errata)
The goal of this project is to identify the discontinuities in streets is Seattle. A discontinuity presents differently depending on the mode of transporation in question: streets are a lot more accessible to pedestrians and bicycles than a car. A good way to think about these discontinuities is how they would appear as if navigating Seattle roadways in a vehicle. Accordingly, a component of the initial data processing involved removing the following road types: alleys, trails overpasses, interstates, state routes, rail, flyovers, streetcars, extensions, turns, highway ramps, and walkways. Some of these roads are not accessible by vehicle. And some of these roads are few in number and short in distance. Expect, of course, for the interstates and state routes. But those are largely continuous (and not that interesting for this project).

In this version of the project, I determined a unique street to be a combination of direction prefix (or suffix), street name, and street type. Under this schema, W GALER ST is not the same as GALER ST which is not the same as E GALER ST. While a street named GALER runs east to west across the city, there are not (yet) connections between W GALER ST and GALER ST or connections between GALER ST and E GALER ST. Something to address in v2.0. 

As is often the case with geospatial data, there are minor discrepancies between data sources pertaining to the same area. The webmap is from [OpenStreetMap](https://www.openstreetmap.org/) and the street network data is from the [City of Seattle](https://data-seattlecitygis.opendata.arcgis.com/datasets/783fd63545304bdf9d3c5f2065751614_0/explore). Far more often than not, the data align geospatially. However, sometimes the data do not align. These instances are rare and often the degree of misalignment is small. A solution is to use only data from OpenStreetMap. Perhaps for v2.0 I'll use data from OpenStreetMap. 

Current connectivity is mostly street-end to street-end because that is usually the shortest distance between two disconnected segments. Sometimes, however, the shortest edge connecting two discontinuous street segments is not street-end to street-end but street-end to mid-point. This is rare, but it has been observed upon visual inspection. [NetworkX](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.centrality.degree_centrality.html#networkx.algorithms.centrality.degree_centrality) provides tools to help refine identification of street-end to street-end connectivity. Definitely something to incorporate in v2.0.

Over the course of panning around the completed map and looking at added segments, I noticed odd connections between streets. The two images below are examples of this phenomenon.
<p float="left">
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_08_15th_ave_w.png" alt="15TH AVE W" width="319" height="400" /> 
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_09_sw_florida_st.png" alt="SW FLORIDA ST" width="597" height="400" />
</p>

This odd connectivity is because of data processing artifacts left in the original dataset from the City of Seattle. For 15TH AVE W, the three artifacts are to the west, east, and north of the actual road. For SW FLORIDA ST, there are two artifacts: one to the south and one to the nortwest of the actual road. These short segments are usually less than 50 feet. My sense is that these erroneous artifacts were created during an initial digitizing process. But that's only speculation. Other maps do not show segments with those names. This [file](https://raw.githubusercontent.com/mike-babb/seattle_streets/main/data/streets_to_remove.txt) tracks these erroneous artifacts. As of January 10, 2025, I have found 12 short segments and I have removed them for v1.0 and I will do so going forward. I include this text and example graphics to help inform end-users about a potential source of odd-looking connectivities. If you find any more odd segments, drop me a line and let me know. 

Finally, if anything looks execptionally out of place or you have additional questions, please let me know. I am happy to address issues and provide additional clarifying information.