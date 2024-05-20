# San Francisco building footprints and Soft Story properties intersecting with seismic hazard zones

These maps accompany [The Frisc's article on Soft Story Buildings](https://thefrisc.com/to-recover-from-a-major-earthquake-sf-needs-housing-now-not-just-later-e2de82084be).

These zoomable slippy maps of San Francisco overlays [population density to seismic hazard zones](https://burritojustice.github.io/frisc/soft_story/density).

_Update: HERE unfortunately shut down the Data Hub / XYZ mapping service in 2023, so the map comparing [building footprints in seismic hazard zones along with properties tagged in the city's Soft Story Retrofit program](https://burritojustice.github.io/frisc/soft_story/footprints) is offline until I find a new custom map tile service. Thank god for GIFs..._

![density and soft story gif](screenshots/density_and_soft_story.gif)

The [seismic hazard vs population density map](https://burritojustice.github.io/frisc/soft_story/density) shows 
- all census blocks of San Francisco below map zoom level 14, using a Viridis plasma color palette to show differences in density
- it brings in seismic hazard zones at z14 (blue/teal: liquefaction, green: landslide)
- clips out just the census blocks that intersect seismic hazard zones at z15
- shows estimated population per block at z16
- there are 1797 census blocks that intersect seismic hazard zones, for a total of 271,418 people, and 136,680 [housing units](https://www.census.gov/quickfacts/fact/note/US/HSG010219)

The [San Francisco Soft Story map](https://burritojustice.github.io/frisc/soft_story/footprints) shows 
- seismic hazard zones below zoom level 15, with teal/blue for liquefaction and yellow/orange for landslides
- at zoom 15, building footprints within seismic hazard zones become visible, along with Soft Story properties with a "Non-Compliant" status are marked as red dots
- at zoom 16, white dots become visible that indicate properties that have been marked as "Work Complete, CFC issued"
- there are also a few yellow dots that represent buildings that are "Work Complete, No CFC issued yet".) 
- these San Francisco datasets were accessed at the beginning of February 2022

These maps are served using Tangram and Tilezen vector tiles. Intersections and density calculations were wrangled in QGIS and data was tiled via HERE Data Hub (formerly known as XYZ). 

## Notes

- Unlike California's seismic hazard zone data, San Francisco's data was not tagged by type of hazard (liquefaction vs landslide). Unfortunately, California's latest dataset [does not yet contain new data for most of San Francisco](https://maps.conservation.ca.gov/cgs/informationwarehouse/regulatorymaps/). However, the feature IDs of the San Francisco dataset show a likely division between landslides (IDs below 300) and liquefaction (IDs above 300), and these seem to match geographic features where these risk are most likely, so we've run with this assumption.
- Population density for the Census blocks was derived via area calcualtions using QGIS.


## Data sources

These maps take data from several sources:

- San Francisco's Soft Story Retrofit database
  - https://sfgov.org/sfc/esip/soft-story
  - https://data.sfgov.org/Housing-and-Buildings/Soft-Story-Properties/beah-shgi
- [San Francisco's building footprints](https://data.sfgov.org/Geographic-Locations-and-Boundaries/Building-Footprints/ynuv-fyni)
- [map of seismic hazard zones in San Francisco](https://data.sfgov.org/City-Infrastructure/San-Francisco-Seismic-Hazard-Zones/7ahv-68ap)
- 2020 Census Block geometries with population estimates via [Census Reporter](https://censusreporter.org/user_geo/3f6e12cd367089ec55787de253a4f0ec/)

Static versions of the extracted clipped data sources are all in this repo's [/data directory](https://github.com/burritojustice/frisc/tree/main/soft_story/data).

[Screenshots](https://github.com/burritojustice/frisc/tree/main/soft_story/screenshots) for posterity, for [when, like tears in rain, these maps eventually die](https://www.youtube.com/watch?v=QefqJ7YhbWQ).

![soft story gif](screenshots/soft_story_seismic_hazards.gif)

![density gif](screenshots/pop_density_census_blocks_seismic_hazards_smooth.gif)



