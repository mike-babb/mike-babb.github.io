---
layout: post
title: "Seattle's neighborhoods"
date: 2025-04-09
categories: Leaflet, web map, local data, socio-spatial boundaries
---

For quite some time I've wanted a web map that shows the [boundaries of Seattle's neighborhoods](/media/seattle_nhoods/neighborhood_map.html)

Over the course of my journeys through Seattle, I am sometimes curious about a neighborhood's boundaries. Or even the name of a neighborhood. While I know the general boundaries of most neighborhoods (`Ballard`, `Fremont`, `Downtown`, and `Pioneer Square`, for example), I often wonder about the *exact* neighborhood boundaries. Is my mental-map correct? Often, we know what area we're in when navigating socially produced space, but those borders and boundaries between spaces can be fuzzy. In the map linked to above, the large neighborhoods outlined in magenta contain the smaller neighborhoods outlined in green. For the most part, the smaller neighborhoods conform to my mental map of the "neighborhood boundaries". Some boundaries are different than what I thought. For example, I thought the southern boundary of the `Greenwood` neighborhood was further north: N 85TH ST as opposed to N 75TH ST. And what I think of as `Capitol Hill` is actually a neighborhood called `Stevens` and `Capitol Hill` is a district. While there is no `Central District`, there is a `Central Area`. And I tend to think of `West Seattle` as one big neighborhood and not a collection of neighborhoods. An example of the trade-off between time-in-space and the distance decay of geographic knowledge.

Both the large district file and the small neighborhood file feature alternate names, when available, for the respective areas. The alternate names can be viewed by clicking on the labels. For example, clicking on the label for `Minor` shows the alternate names of `Central District` and `Squire Park`. Clicking on the label for the `North Central` district shows the names for the neighborhoods and the alternate names. These data from the City of Seattle show historic and current names, but do not (yet) show the changing names of neighborhoods and new names. For example, where is `Frelard`? (And how is it pronounced?) (edit 2025/09/09: I recently heard this neighborhood called `Balmont`. I like that much better.) Most people would probably say it's a place in between `Fremont` and `Ballard` as people tend to think that `Fremont` and `Ballard` share a boundary. I certainly did. But, as always, geo-social spatial data tell stories that do not necessary conform to our own, precise, lived experience. According to the map linked to above, there is no ~~`Frelard`~~ `Balmont` area. What would be the ~~`Frelard`~~ `Balmont` area is the `West Woodland` neighborhood. Let's look at `Lower Queen Anne` as an example of a changing name. On the base map, this area is called `Uptown` which, is indeed, an alternate name of `Lower Queen Anne`. But that area will always be `Lower Queen Anne` to me. As a final note about the data, while all of the smaller neighborhoods can be aggregated to larger districts, some larger districts have the same name as the smaller neighborhoods: `Interbay`, `University of Washington`, and `Seward Park`, for example.

Both datasets where downloaded from the City of Seattle:  
[Large Districts](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-districts/about)  
[Small Neighborhoods](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-neighborhoods/about)  

The district and neighborhood boundaries originate from the [Seattle City Clerk's Office Geographic Indexing Atlas](https://clerk.seattle.gov/~maps/nmaps/fullcity.htm).

This [passage](https://data-seattlecitygis.opendata.arcgis.com/datasets/SeattleCityGIS::neighborhood-map-atlas-districts/about) describes the origin and purpose of the boundaries: 
> "The original atlas is designed for subject indexing of legislation, photographs, and other documents and is an unofficial delineation of neighborhood boundaries used by the City Clerks Office. Sources for this atlas and the neighborhood names used in it include a 1980 neighborhood map produced by the Department of Community Development, Seattle Public Library indexes, a 1984-1986 Neighborhood Profiles feature series in the Seattle Post-Intelligencer, numerous parks, land use and transportation planning studies, and records in the Seattle Municipal Archives. Many of the neighborhood names are traditional names whose meaning has changed over the years, and others derive from subdivision names or elementary school attendance areas."

This [page from the City Clerk](https://clerk.seattle.gov/~maps/nmaps/aboutnm.htm) specifically answers this *Frequently Asked Question*:
> "Q: Why doesn't this map show my neighborhood correctly?
>
> A: There is no one "correct" Seattle neighborhood map. Representation of neighborhoods in this atlas can never meet all expectations for several reasons:
> * Different City departments and non-City entities define neighborhoods differently based on many factors;
> * Familiar neighborhood boundaries and City planning areas and names change over time;
> * The records being indexed using this atlas date from the 1800's to present, and so no one set of boundaries and names will ever perfectly match all records; and,
> * At any point in time there may be many conceptions of what defines a neighborhood and how it is named." 

Great explanations!

The data on the map above underwent minimal processing. For both the larger districts and the smaller neighborhoods I performed the following tasks:
* Standardized column names.
* Created LineString boundaries from Polygons.
* Exported the data from a GeoPackage file to a GeoJSON file.
* Extracted centroids from the Polygons to help with label placement.
* Created a series of inner-ring buffers in increments of 10 meters. 

The centroids were used to fix the labels in place so they are always visible. The inner-ring buffers were used to help delineate the boundaries and increase the visual legibility of the maps. This is how I achieved having the green neighborhood boundaries follow the magenta larger district boundaries (which follow streets and water boundaries). I'll post a link to the git repo showing how I created the inner-ring buffers. 

For a version 2.0: Label placement. I'm using [Leaflet](https://leafletjs.com/) to make the [map](media/seattle_nhoods/neighborhood_map.html). The near-entirety of my map-making career has involved ArcGIS, qGIS, R, and Python. With those tools, I can center a label quite easily. But with Leaflet and javascript, I'm not sure how to do that. Always more to learn, of course.

Happy map viewing! If you have any questions about the boundaries, please let me know. While I won't change any boundaries, I'm curious if you think anything is exceptionally out of place.