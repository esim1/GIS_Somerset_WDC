# Warehouse and Distribution Center Development in Franklin, New Jersey

## Explore Franklin's Current and Proposed Warehouses/Distribution Centers
<br>
Toggle the layers to explore the proximity of current and proposed warehouses to residential, commercial, farmland, and other land uses. Parcels within 5,000 feet of an existing or proposed warehouse are shown on the map.
<br>
<iframe src="651_fall22_final_v3.html" height="500" width="1000"></iframe>
<br><i>NJ Office of GIS (2022), Franklin Township (2022)</i>
<br><br>

## Proposed Warehouses

About 60 percent of proposed warehouses in Franklin Township would require a non-industrial land use conversion. Proposed warehouse site plans would redevelop 71.9 acres of office buildings, 49.82 acres of solar panel fields, and 19.12 acres of greenfield.

![conversion final](https://user-images.githubusercontent.com/96669714/208326131-ea3eabc0-bbfa-4e15-b0c4-66f84d73c59a.png)
<br><i>NJ Office of GIS (2022), Franklin Township (2022)</i>
<br><br>
<img width="433" alt="Screen Shot 2022-12-18 at 7 51 40 PM" src="https://user-images.githubusercontent.com/96669714/208328755-c01a853a-3f75-4f24-9626-224f83ab8a3b.png">
<br><br>
## The Social Landscape of Industrial Redevelopment

Franklin's current and proposed warehouses (illustrated in red below) are located in block groups with lower income levels and lower population density. The densest population centers are in the neighboring municipalities of South Bound Brook and Manville.

![sm2](https://user-images.githubusercontent.com/96669714/208324555-b29d7bf6-1e2c-42dc-b723-6533f439cae0.png)
<br><i>American Community Survey (2015-2019) 5-Year Estimates; 2019 TIGER/Line Shapefiles</i>
<br><br>
## Final Project Response

I created a parcel-level dataset of current and proposed warehouses and distribution centers in Franklin, Somerset County, New Jersey as of December 2022 by gathering data from property tax records, satellite imagery, and site plans. I used property tax records from the Bloustein Local Government Research Center and the NJ Office of GIS. Property tax records from Somerset County and Middlesex County were last updated December 16, 2022. Property tax records and digital parcel maps were prepared by Somerset County, Middlesex County, and the NJ Treasury Department. Parcel records from the Bloustein Local Government Research Center were compiled using historic records from the NJ Treasury Department. I gathered data about proposed warehouses from site plans posted on Franklin Township's webpage on November 14, 2022. I created a table of proposed warehouses from PDF records and joined the data frame to the digital parcel map.

Property tax records were available in CSV format while the digital parcel map was available in a shapefile format. I used the union geoprocessing tool to combine parcels from Middlesex and Franklin Township. Then, I created a 5,000 foot buffer around current and existing warehouses to clip the combined parcel map. I then merged the combined parcel map with the data frame of property tax records. Finally, I subset the digital parcel file by property class (residential, commercial, farmland, and schools). I also created a 500 foot buffer for current and proposed warehouses to create layers for the interactive map where users can explore how warehouse uses overlap with neighboring land uses.

I used satellite data from Google Maps and Planet Labs to triangulate building uses in property tax data. I referenced satellite data from PlanetLabs taken on November 14, 2022.  Google Maps satellite imagery does not disclose the time period that images were taken. Google Street View images ranged from 2019 to 2022 depending on the location.

Tax records did not reliably categorize building uses for commercial and industrial parcels. I created a workflow to validate and re-categorize warehouse uses by comparing property tax records with satellite imagery and Google Maps. I reclassified 22 parcels that were not categorized as a warehouse in property tax records based on the presence of truck bays in satellite imagery and business listings on Google Maps. Additionally, I removed 9 parcels classified as warehouses because they had a very small lot size (below 20,000 sq. ft.) or Google Maps indicated that the property is not currently occupied by a distributor. Additionally, data quality errors in property tax records prevented property tax records from merging to the digital parcel map. I was able to re-match all warehouses by merging on the address field or updating the parcel ID.

Information about building area, not available in property tax records, was gathered from Microsoft’s Building Footprint dataset. Building footprints were generated from satellite imagery taken between July 2019 and October 2020. Hence,  building footprints for warehouses built after October 2020 may be inaccurate. Building footprints are missing for five warehouses. Building footprints were available in GeoJSON format for the United States. I clipped the national spatial dataset to Franklin Township using municipal boundaries from the Census Bureau.

I also gathered digital maps of municipal boundaries and block groups from the Census Bureau in shapefile format. After using the union command to combine block group and county subdivision maps for Somerset and Middlesex County. Then, I subset the county subdivision map to include municipalities neighboring Franklin Township’s industrial districts. I used the clip geoprocessing command to create a polygon of block groups encompassing Franklin and neighboring municipalities that span Somerset and Middlesex counties.

Data for the choropleth maps of population density and median household income were gathered from the American Community Survey (2015-2019) 5-Year Estimates. I gathered data using the Census API tool and restructured the data from a JSON to a pandas data frame. I gathered data at the block group level and merged to the block group map of Franklin and surrounding municipalities.

## References

Bloustein Local Government Research Center. (2022). “N.J. MOD IV Historical Database.” Last Updated 10/28/2022. Retrieved from: https://modiv.rutgers.edu/

Microsoft. (2018). “U.S. Building Footprints.” Retrieved from: https://github.com/Microsoft/USBuildingFootprints

NJ Office of GIS. (2022, November 28). “Parcels and MOD-IV of Middlesex County, NJ (fgdb download)” Last Updated 12/16/2022. Retrieved from: https://njogis-newjersey.opendata.arcgis.com/documents/cae0c9f99c28401cbb7b9c4364648ce9/about 

NJ Office of GIS. (2022, November 28). “Parcels and MOD-IV of Somerset County, NJ (fgdb download)” Last Updated 12/16/2022. Retrieved from: https://www.arcgis.com/home/item.html?id=333f558cfa6f4d3dbe14e4acf9dc633d 

Planet Team (2017). Planet Application Program Interface: In Space for Life on Earth. San Francisco, CA. https://api.planet.com.

Township of Franklin. (2022). “Planning Board Application Materials.” Accessed 11/05/2022. https://www.franklintwpnj.org/committees-commissions/planning-board/application-materials 

U.S. Census Bureau. (2019). American Community Survey, 5-Year Estimates. 

U.S. Census Bureau. (2019). 2019 TIGER/Line Shapefiles.
