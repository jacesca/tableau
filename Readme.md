# Tableau 2022 A-Z: Hands-On Tableau Training for Data Science
Project visible at [Tableau Jacesca's Profile](https://public.tableau.com/app/profile/jacesca/)<br>
Material can be found [here](https://www.artofvisualization.com/pages/tableau).

Tool to boost the *skills in data science (capacity and Ability to Understand the domain knowledge)*


# 1: Let's started

A simple map to show profit by state.

> Data source: [map SuperStoreUS-2015.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-SuperStoreUS-2015.xlsx)


# 2: A basic bar chart

| Data | Conceptual | Visualisation |
|---|---|---|
| Connect to csv | Calc field | Barchart |
| | | Colours |
| | | Labels |
| | | Formatting |
| | | Exporting |

* Tableau divides the fields into Dimensions and Measures.

*Challenge*
It is end of the financial year and that means time for annual bonuses!
The store operates in three regions and only the top performing employee in each region qualifies for a bonus.
Find out which three employees are eligible to get a bonus for this year.
Employees are meausere on total value of sales($)

> Data source: [OfficeSupplies.csv](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-OfficeSupplies.csv)

*Tips*:
* Click & hold on a column field, and when it is over the colors press ctrl and when the plus sign is visible let it go, then move the color category below the marks.


# 3: Timeseries, Aggregation, and Filters

| Data | Conceptual | Visualisation |
|---|---|---|
| Excel file | Timeseries as measures | Line chart |
| Data extracts | Timeseries as dimensions | Shapes |
| | Aggregation | Show me |
| | Granularity | Area chart |
| | Filter | Highlighting |
| | Quick filter | |

* Data Extract over Live Connection: Your data is constantly being updated and you want to work with a static file when building your dashboard.
* Values are always aggregatted at the level of granularity of the worksheet.

> Data source: [Long-Term-Unemployment-Statistics.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-Long-Term-Unemployment-Statistics.xlsx)


# 4: Mapas and Scatterplots

| Data | Conceptual | Visualisation |
|---|---|---|
| Data joins | Hierarchies | Map |
| | Filter on multiple sheets | Circles on a map |
| | Dashboard: adding charts | Scatterplot |
| | Dashboard: quickfilter | Dashboard: layout |
| | Dashboard: filter action | |
| | Dashboard: Highlight action | |

* Hierarchies are required each time they are presen in the Dimensions, so Tableau can know about them for you to build the visualization.
* Main difference between Action-filter and Action-Highlight: When you use Action-Filter you are removing data from analysis before it is illustrated on the visualization, when you use Action-Highlight first all of the data is visualised and only after that the action is applied. This can lead to discrepancies in results.

> Data source: [AmazingMartEU2.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-AmazingMartEU2.xlsx)


# 5: Joining, Blending and Relationships

| Data | Conceptual | Visualisation |
|---|---|---|
| Join theory | Calc field in a blend | Dual axis charting |
| Blending data | | |
| Joining vs blending | | |

* Types to cope data:
    * Joining
        * Created at the phisical level.
        * To go into the physical level, we need to double click into an individual table on the logical level.
    * Blending
        * A smart left join made on the fly. 
        * It occurs at the granularity view.
        * Aggregation happens before blending.
        * Use it when different dimensionality or different source. 
        * Custom blend can be controled through the Data menu.
        * Blends are unique to each worksheet.
    * Relationships
        * Data model has 2 layers: logical layer and physical layer.
        * Relationships are more flexible than joins.
        * Tables are treated as separate, however you can combine fields on the fly.
        * Tableau will automatically connect the data at the right level of aggregation.
* For Dual axis: dual axis on the left, sincronize axis on the right.

*When to use it*
| Joins | Blends |
| ----- | ------ |
| Combining data at row level. | Datasources have different levels of granularity. |
| | Datasources come from different systems. |

> Data source:
>* [map SuperStoreUS-2015.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-SuperStoreUS-2015.xlsx) 
>* [Airline-Comparison.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-Airline-Comparison.xlsx)
>* [Brazilian-E-commerce-Dataset](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-Brazilian-E-Commerce-Dataset.zip), taken from [Kaggle.com](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)


# 6: Storytelling

| Data | Conceptual | Visualisation |
|---|---|---|
| | Geographic roles | Filled map |
| | Table calculations | Pie chart |
| | Bins | Distributions |
| | Parameters | Treemap |
| | | Storyline |

* Indicators can be hided.
* Parameters easy to create from the parameter left-bottom side area (right click - create parameter)
* To show a bar chart of cases by age:
    * Add age field to columns.
    * Change it to dimension.
    * Add cases to rows.
    * Change thw quick table calculations (right click on the cases field) to percent of total.
* To create bins: right click on the field >> Create >> Bins >> Set a name and size.
* To create a parameter to adjust the bins in our histogram:
    * Click right on the white space in left panel.
    * Select Create parameter.
    * Set the name, data type, select kist in allowable values, set minimum, maximum, and step size.
    * Click right on the created parameter and select show parameter.
    * Click right on the field bins we need to link and select edit.
    * Click on the size of bins and select the created parameter.
* Story creations: 
    * Worksheets and dashboards can be used as pages in a storyline, but cannot be combined on one page.
    * When you change the value of a parameter on one page of the storyline, this is not changed on the remaining pages.
* To set geographic roles: Right click the appropriate field and select the appropriate geographic role.
* Customer segmentation dashboards are used for: 
    * understanding how customers are segmented acorss different geographies.
    * making better business decisions.
    * delivering a better customer experience making it tailored and relevant.
* In treemaps, the main visual element is the box.

> Data source: [UK-Bank-Customers.csv](UK-Bank-Customers.csv)


# 7: Data Preparation

| Data | Conceptual | Visualisation |
|---|---|---|
| Data interpreter | | |
| Pivot | | |
| Splitting columns | | |
| Metadata grid | | |
| Fixing map errors | | |

* Data cleaning:
    * It can be hidden columns from datasource
    * To tranfrom from computer-readaable to human-readeable: select the columns -> Click right -> pivot.
* Split, select column -> Click right -> split and set configuration (e.g. ' ' as separator and only last)
* For unknown values: Edit locations, filter exclude, or default value/position.

> Data source: [PersonalVehicleSalesGlobal.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-PersonalVehicleSalesGlobal.xlsx)


# 8: Clusters
* For maps, it is important to align the location when we only have the city names (map >> edit locations).
* For regions not recognized a map: we can select the field >> click right >> Geographic role >> Create from >> select the associated field.
* Highlighters can be added from the fields (in details). Click right >> show highlighter.
* Clusters used for segmentation (Left panel >> Analytics tab >> Double click on Cluster)
* To add trends (line tendency): Left panel >> Analytics tab >> Trend line (Model). 
* To avoid trends is recalculated twice: Right click on any trend lines >> Edit All trend lines >> Unmark show recalculated line for highlighted or selected data points.

*Covered*
* How to create custom territories via Groups.
* How to create custom territories via Geographic Roles.
* How to use highlighters in Tableau.
* How to perform clustering analysis in Tableau.
* How to use domain knowledge to add external datasets into our analysis.
* How to create cross-database joins.
* How to combine regression modeling with clustering.
* How to save clusters for further analytics. 


*Challenge*
You are a Data Scientist working for a laundry-pickup services startup. This is a small company and they can not compete with bigger companies. The strategy is to build a network in the smaller cities.

The company already had a presence in 140 locations and recelty opened stores in 10 new cities. The company also has two separate sales regions.

Tasks:
1. Identify which of the 2 sales regions is performing better:
    * Average revenue per city.
    * Average Marketing spend per city (less is better).
    * Average ROMI (Return on Marketing Investment) per city (revenue/marketing spend)
2. Identify which of the 10 new locations has the best potential for the company to invest more funds into marketing.

> Data source: 
>* [StartupExpansion.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-StartupExpansion.xlsx)
>* [US-Cities-Population.csv](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-US-Cities-Population.csv)


# 9: PDF, Unions, Spatial files & Data Integrity
* To make unions, hold on the second table and move it over the fist one until UNION shadow appears.
* To read pdf, the "Cleaned with Data Interpreter" option will be help full (Mark it!).
* When reading pdf some field may be splitted to merge them: select the column fields >> click right >> select merge...
* Sometime when reading a table in pdf file, the total row is also included, to remove it: on the data source tab select filter add from the right up corner >> click the add button >> select the field to set the condition >> click ok button >> set the value (e.g. select from list, none, look for the total, mark it) >> mark exclude >> click ok button >> click ok button again.
* Tableau can connect to 4 different spatial type fles:
    * Shapefiles: 
        * Common extensions: .shp (shape format), .shx (shape index format), .dbf (attribute format). 
        * Other allowed extensions: .prj, .sbn and .sbx, .fbn and .fbx, .ain and .aih, .ixs, .mxs, .atx, .shp.xml, .cpg, .qix 
        * Developed by the Environmental System Resource Institute.
    * MapInfo tables: 
        * Allowed extensions: .tab, .dat, .map, .id, (or .mid/.mif)
    * KML (keyhole markup language): 
        * Allowed extensions: .kml
    * GeoJson: 
        * Allowed extensions: .geojson
* There are 3 main types of maps in Tableau:
    * **Polygon map** (filled map): polygons depicting the shape and or the outline of a specific area on the map. We can use dimensions and measures to color those polygons.
    * Point map: we use the latitude and longitude points within a map to a location. We can enrich it with dimension and measures in terms of color and sizing.
    * Line map: Connects different points on the map to be able to show direction or actual distances between points on your map.
* Tableau has some built in geographic roles to define these as city, country, state zip codes, airports, area codes, and more. But be aware that some times these roles are not enough: ex. School disticts, parks, etc. (here is where additional spatial data is required).
* To read spatial files:
    * Open a new connection
    * Spatial files
    * Select the appropriate format and look for the file.
    * On the sheet, look for the geometric filed and drag it into your map/sheet.
    * Drag the name into details, so when your mouse is over, you can see the name of the area in the map.
* To customize the map layer:
    * Go to menu Map >> Background Layers
    * Customize options on the left panel (e.g. mark County Borders)
* To show a scale in the map:
    * Click Map >> Map Options
    * Select units and mark show map scale
* To keep the same color scale across different applied filters, we can customize color as follow:
    * Click on colour.
    * Select edit colours.
    * Click on Advanced.
    * Select Start and End as required.
    * Click on ok button.
* Tips: On data source tab, we can change the type of a field by right click on the type in the header of the field and selecting the new type associated (including geographic role).
* Tips: when there is missing data points in drawing the map, validate location (Edit location) to match the country with what geographic points are referring.
* Tips: to select just the top 5: move the field to filter >> Select Top tab >> Select By field >> set top and number >> select field and measure >> click ok button.


*Challenge 1*
(For educational purposes only)
* Analyse crime incidents occurring at New York City (NYC) parks. This is in support of their efforts to lobby for safer parks. We need to design an attegtion-grabbing visualization which they will use to motivate for more police patrols in NYC public parks.
* Analyse the crime incidents reported to the New York police department (NYPD), which gave occured at NYC parks during the first quarter of 2018, The data is in PDF format.
* Central park is not included.
* Results need to be displayed using a map, including the actual park layout and size.
* Tooltips and filtering per borough are required.

*Challenge 2*
(For educational purposes only)
* Analyse average salary across industries for the State of New York:
    * Average annual salary by county displayed on a map.
    * Top 5 highest earning industries by county.
    * Time series analysis of average annual salary by County.
* Do not separate graph on different sheets.
* Do not work with a dashboard.
* All information need to be contained within a single sheet with pop-up charts while the map is being explored.
* Data manipulation required to apply:
    * Just select county in Area Type.
    * Change name from Area to Count.
    * Change name from NAICS Title to Industry.
    * Change type of County to County Geographic Role.
    * Change tyoe of NAICS to string.
    * Select just NAICS that have 2 char lengths, we only need high levels (2 chars) not low levels (3 chars). To do this: create a calculated field (len) and then add a new filter on the data source.
    * Hide Establishments, Average Employment and Total Wage.

Data source:
* [Section 9 Challenge I](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-Section-9-Challenge-I.pdf)
* [NYC Park Crime Stats](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-nyc-park-crime-stats-q1-2018.pdf)
* [NYC Parks and Public Spaces – Spatial Files](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-NYC-Parks-and-Public-Spaces-Spatial-Files.zip)
* [Section 9 Challenge II](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-Section-9-Challenge-II.pdf)
* [Employment and Wages Annual Data](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P1-quarterly-census-of-employment-and-wages-annual-data-beginning-2000.csv)