---
layout: post
title: "Identifying Seattle's Discontinuous Streets"
date: 2025-01-01
categories: geospatial analysis, street network, GeoPandas, NetworkX, webmap
---

# Visualizing Street Discontinuities
I just [published](https://github.com/mike-babb/seattle_streets) a project on identifying Seattle's discontinuous street network. Briefly, streets in Seattle start, stop, and resume. A street will run for a few blocks, stop, and then resume with the same name. While I know this happens throughout the city, I was curious if it was common or not and I wanted to visualize the gaps in each named street. After working on this intermittently for the past six months, I was able to create this map:  
<img src="https://raw.githubusercontent.com/mike-babb/seattle_streets/main/graphics/ex_02_overall.png" alt="overall" width="500" height="565"/>  

[SEE THIS PAGE FOR AN INTERACTIVE MAP OF THE ADDED STREETS](/media/discontinuous_streets.html)

The red lines are the missing/added connections between streets and the black lines are the existing streets with discontinuities. This map was a lot of fun to make and it was incredible to see represented visually what I long sensed about navigating the city: the streets are disconnected, a little chaotic, and getting around this city can be challenging. When I first started this project, I had assumed that I could create a solution using only geospatial tools. That proved to be complicated - if not impossible - as it required a lot of guess-and-check proceedures to see if the correct segments were being joined. After some trial and error, I realized that I was quasi-recreating known graph analysis techniques so I turned to NetworkX to help with the analysis. And in doing so, the analysis became much easier, much quicker, and required a lot less code. It's always nice when that happens. Right tool for the right job, as they say...

Several facts about these added streets:

* 2,497 roads in the study area | 1,933 road miles
* 1,357 roads without discontinuities | 421 road miles  
* 1,140 roads with discontinuities | 1,512 road miles  
* 3,643 segments added across 1,140 roads | 834 miles   
* Average added segment length: 0.25 miles
* Median added segment length: 443 feet  

I'll encourage those interested to take look at the project's [README.md](https://github.com/mike-babb/seattle_streets/blob/main/README.md) or this [slide deck](https://github.com/mike-babb/seattle_streets/blob/main/seattles_disconnected_streets_2024_11_20.pptx) for more detailed information on the data driving this project, the python libraries ([GeoPandas](https://geopandas.org/en/stable/getting_started/introduction.html) and [NetworkX](https://networkx.org/), in particular) and techniques I used to identify the gaps in Seattle streets. To that end, the code and the data used to identify the disconnected streets is available for those curious. 