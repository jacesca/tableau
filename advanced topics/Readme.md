# 1: Advanced Tableau
Project visible at [Tableau Jacesca's Profile](https://public.tableau.com/app/profile/jacesca/).<br>
Material can be found [here](https://www.artofvisualization.com/pages/tableau-advanced).<br>
[Other resources for Tableau](https://sdsclub.com/tableau-2022-advanced-training-master-tableau-in-data-science/)

# 2: Group and sets (static vs dynamics)

| Hacks | Conceptual | Best practices |
|---|---|---|
| Defautl properties for fields | Groups vs Sets | Organize fields in folders |
| 2 dimensions or sets in Colour | Static sets and Dynamic sets | Drop lines |
| Reference lines | Combining sets (based on the same dimmensions) | Useful tooltips|
| Fix up color range so it doesn't start from certain value (degradation color) | Controlling sets with Parameters | |
| Dynamic texts in tooltips/titles | Creating sets via Formula | |

* Groups are used to combine multiple categories of one field into one category.
* Static sets are hard-coded, in contratst, Dynamic sets can be changed as the data and analysis requirements change.
* To add multiple fields into colour: you first select the desired fields through Ctrl or Shift and then drag them onto the colour button in one action.
* Sets + parameters are a powerful combination of techniques.

* Tips: To organize fields in the left panel area, click right on white space (better at the bottom) and then group by folder (default: group by DataSourceTable).
* To create groups: click-right on the field (left side panel) >> Create >> Group >> select what to group >> click Group >> Set a name for the group >> Unmark Include Others >> Apply >> Ok. Now you can use this new field in other charts as Bar or Pie.
    * A second method is to select the labels in a bar chart to group categories.
    * Notice that groups retaque all individual values to get the required measure e.g. avg. (not making avg of avg but avg of all the items included in the group).
* To create set: select the labels in the chart and click on the set icon and select create Set. 
    A second method is click right on the field >> Create >> Set 
* To create dynamic sets: Go to the field (please select unique keys) in the left panel >> right click >> create >> set >> on general tab: put a name, select use all >> set a condition or define the top criteria (choose the proper tab) >> click ok.
* Hack: To set the format property on a field (please select unique keys) so each time you use it, you do not need to go to format: right click on field >> Default properties >> Number format.
* On scatter plots to disagregate: go to menu >> analysis >> uncheck aggregate measures.
* Combined sets are only possible if each of them is based on the same dimension.
* To create combined sets: right click on one of the sets >> create combined set >> put a name >> set the 2 sets >> select combination type >> click ok.
* Hack: To reverse/flip a chart: right click on the axis to reverse >> edit axis >> mark reversed (scale) >> click ok.
* To add parameters to sets with defined condition, a formula with the condition referring the parameter need to be added, for that "by formula" option need to be selected in the condition tab of the set.
* To add multiples criteria to colour in a chart, select all the fields you want to be part of the criteria and move them together to colour.
* Parameters can be formatted also to express currency ($), thounsands (K), millions (M), etc.
* To add a reference line: right-click on the axis >> add reference line >> set the value to the correct parameter >> set label to value >> click ok.
* Drop lines (on scatter chart right click on empty space and select drop lines) shows you the reference to the selected point.

*Challenge:*
* The board are reviowing a thousand of startups and deciding on which ones they are going to invest.
* The criterion for selecting investments are:
    * High revenue
    * Low expenses
    * Top growth
* Task consist in identifying which business represent the best investment oportunity.

Steps:
1. Load files.
2. Create a set based on a unique key to express the top growing startup. (Use all and set the top criteria).
3. Create an scatter plot: expenses on rows and revenue on colums, disagregate them (Anaysis menu).
4. Create 2 sets (use same dimension), one to define the limit in the revenue and the other for expenses (set base on condition by field).
5. Create a combined (target quadrant) set of the 2 created in the previous step (shahred in both steps)
6. Drag the combined field over colour.
7. Reverse expenses axis (edit axis >> reverse) so the quadrant we are looking for is in the upper left column.
8. Create parameter for growth leaders (type: int, current value: 10, range: 5, 100, 1). 
9. Modify the top growing startup set to include the growth leader parameter (edit set >> by field >> select the parameter).
10. Create a hbar: name on rows, growth on columns, set a filter based on the top growing startup. Colour by top growing startup set. Show parameter: right-click on the growth leader parameter and show.
11. Create parameter to control the limits in expenses and revenue (set a name >> type: float, current value: 9M and 5M for the other, range: 0 - 16M, change type to int). Go to the scatter plot and show both parameters.
12. Modify the set created for revenue and expenses (condition by formula: "sum( [revenue] ) > sum ( [revenue cutoff parameter] )")
13. Create the dashboard: move the scatter plot (right) and the table (left down), and the 3 parameters (revenue cutoff, expenses cutoff, growth leaders) will be visible.
14. Go to the scatterplot and edit it: move the top growing set to shape (change and select the filled diamond for in and circle for out), then move together the target quadrant and the top growing set over the colour. Change colors (in-in: orange, in-out: blue, out-in: dark gray, and out-out: gray)
15. Make the hbar color similar to match with the scatterplot (growth leaders highlighted on scatterplot: orange and dark gray)

> Data source:
>* [Section 2 – The Challenge.pdf](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section2-The-Challenge.pdf)
>* [1000 Startups.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-1000-Startups.xlsx)

> Dashboard: [Target Quadrant](https://public.tableau.com/app/profile/jacesca/viz/A1-TheStartUpQuadrant/TheStartUpQuadrant)
> Dashboard: []()


# 3: Table Calculations
* Table calculation are conducted after aggregation has been performed. Eg. Quick label calculations (e.g. Running total, difference) and relative to (Previous, Next, First, Last), powerful tool in the possible calculation can be configured on a field in a chart.
* Calculated fields are evaluated at row level, table calculations are evaluated after aggregation.
* To get the calculations of sheet: click right on the sheet tab name >> duplicate as crosstab.
* Sometimes is important to reverse the axis to facilitate the analisis (for example exceed observations on negative measures).
* To adjust the graph into the sheet: select fit height on the icon: dropdown fit from the icon bar menu .
* To flip the chart: click on the swap icon on the bar menu. 

*Challenge:*
* Assess which of their coal reclaimer machines require maintenance in the upcoming month.
* A reclaimer type machine requires maintenance when within the previous month there was at least one 8 hour period when the average idle capacity was over 10%.
* Idle capacity is a utilization metric which is defined as:
$$ IdleCapacity = {(ActualTonnage - NominalCapacity) \over NominalCapacity} $$
* The provided dashboard needs to show the 5 machines that have exceeded this level and the recommendations to follow.

**Table calculations applied**

-- Follow the steps in this dashboard: [A3.2 New Metrics with Table Calculations](https://public.tableau.com/app/profile/jacesca/viz/A3_2NewMetricswithTableCalculations/IdleCapacityCalculation) --

1. Add timeline to column.
2. Add machine, metrics, tonnes to rows.
3. To set the difference: click right on tonnes >> quick table calculation >> Percent difference. 
4. To make the difference between the chart and the upper chart: click right on tonnes >> select compute using >> Table down.
5. Select all nominal capacity chart >> click right >> hide.
6. Drag the field with the table calculation to the dimensions & measures panel and set the name IdleCapacityNeg.
7. Right click on IdleCapacityNeg >> create >> calculated field: [Idle Capacity Neg] * -1, name it as IdleCapacityPercent
8. Drag IdleCapacityPercent to replace IdleCapacityNeg
9. Click on the y-axis >> add reference line >> set value as constant with -0.1.
    * If chart is swaped, the table down option is changed to table across option.
10. So far has been an implicit table calculation. To make it explicit: click on IdleCapacityPercent >> edit table calculation >> compute using: specific dimensions >> mark machine and metrics >> close.
11. Make explicit IdleCapacityNeg: Click-right on IdleCapacityNeg (dimension & measure pannel) >> Edit >> Default table calculation link >> compute using advance >> select machine and metrics >> click ok (3 times)

-- End --

12. To generate the 8 hours average, we are going to create a new calculated field (IdleCapacityWindowAverage), with the following formula: WINDOW_AVG([IdleCapacity], -7, 0). 7 previous hours + current (0 index) = 8 hours. Then set the Default Table Calculation to be explicit, in this case is not table down, because points are next to each, sol choose datetime as the compute using parameter only.
    * To calculate the moving average you need to validate enough data. If you donot have sufficient data, you have to tell tableau not to calculate it.
13. Click right on the graph to add trendlines.
    * if p-value is less than 0.05 is statistically significant. A p-value greater than 0.05 means that no effect was observed.
14. To avoid trend lines being calculated each time points are selected: right-click on trendline >> edit >> unmark show recalulated line for highlighted or selected data points.
15. Unmark command buttons on tooltip editor.
 
> Data source: 
>* [Section 3 – The Challenge.pdf](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section3-The-Challenge.pdf)
>* [Coal Terminal.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Coal-Terminal.xlsx)
>* [Images.zip](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section3-Images.zip)

> Dashboard: 
>* [Table Calculations](https://public.tableau.com/app/profile/jacesca/viz/A3_1-TableCalculations/TableCalculationsSummary)
>* [Metrics with Table Calculations](https://public.tableau.com/app/profile/jacesca/viz/A3_2NewMetricswithTableCalculations/IdleCapacityCalculation)


# 4: Data Preparation + Analytics in Tableau
* To create BoxPlots: 
    * Click on Analytics on the left panel >> drag the box-plot over the bar-circle chart and let it go.
* In trend lines, if you want to hide one in a multiple line chart, just click right on the space of the specific one space of the multiline chart >> trend lines >> unmark show trend lines.
* Some times it is necessary to make a blend join with a table based on the Quarter/Year, you can customize it in menu data >> blend relation >> modify it to add year and quarter from the date. If you need to have this blend relation in your dashboard, you need to drag the date, as many times as you define in the blend relationship, to detail button.
* To add forecast, just go to Analytics in left panel and drag the forecast model to the chart.

> Data source:
>* [Section 4 – The Challenge.pdf](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section4-The-Challenge.pdf)
>* [Competitor Research.csv](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Competitor-Research.csv)
>* [8501011 – Retail Turnover, State by Industry Subgroup.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-8501011-Retail-Turnover-State-by-Industry-Subgroup.xlsx)
>* [310104 – Australian Demographic Statistics.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-310104-Australian-Demographic-Statistics.xlsx)

> Dashboard: 
>* [BoxPlot](https://public.tableau.com/app/profile/jacesca/viz/A4_1-BoxPlot/NetProfitMargin)
>* [Forecast](https://public.tableau.com/app/profile/jacesca/viz/A4_2-Forecast/Finalpresentation)


# 5: Animations
* In a buble chart, you can customize order of the categories defined in color button following: localizing the proper field >> click right >> default properties >> sort >> sort by manual >> setting the orderd >> close.

> Data source:
>* [Section 5 – The Challenge.pdf](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section5-The-Challenge.pdf)
>* [Country Metadata.xls](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Country-Metadata.xls)
>* [Country Population.xls](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Country-Population.xls)
>* [Fertility Rate.xls](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Fertility-Rate.xls)
>* [Life Expectancy At Birth.xls](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Life-Expectancy-At-Birth.xls)

> Dashboard: [Animation](https://public.tableau.com/app/profile/jacesca/viz/A5-Animation/WorldDemographic)


# 6: More Table Calculations
* 3 types of LODs (Level of Calculation):
    - Include:
        - You have a higher level (e.g. state) will include all details (e.g. city) to bring it at the high level.
    - Exclude:
        - You are a lower level (e.g. city) and need to go to higher level (state) to bring some calculation back to lower level. (Exclude temporary the current level to go to higher level in order to get calculation from there to bring it back to lower level).
    - Fixed:
        - The fixed level of detail calculation will not care about the current level/granularity of visualization.
* When it is added a new dimension to the visualization, the level of granularity increases, level of aggregation decreases.
* The **ATTR()** function returns the value of the expression if it has a single value for all rows. Otherwise returns an asterisk. Nulls are ignored.

Steps:
1. Load file into Tableau.
2. Join listOrders with its details.
3. Create geography: drag country over >state, add city, and postal code.
    
* To ilustrate: Map Review Sheet:
    - Drag geography to the sheet.
    - Expand country and state (city last level on the map).
    - drag profit over label (sum).
    - click on order date >> show filter.
    - copy same profit from label to colour also (sum).
    - You can colpase to state to see changes.
    - **granularity**: profit presented by city and by date. If you colapse the geography field in detail to state, the profit will be recalculated to that level.

* To ilustrate: LODs (Include) sheet
    - Drag geography to the sheet.
    - Expand country and state (city last level on the map).
    - drag profit over label (avg).
    - copy same profit from label to colour also (avg).
    - Colapse to state.
    - Duplicate map, drag + ctrl longitud from columns to columns again.
    - The second map will be without LOD calculation.
    - Create calculated field: LOD INCLUDE city profit:
        - { INCLUDE [City]: SUM([Profit]) }
    - Drag the LOD field over color and label of the first map. Change measure to AVG.

* To ilustrate: ATTR Investigation:
    - Duplicate Map Review Sheet.
    - Drag city and country to tooltip they are shown with ATTR.
    -**ATTR**:
        - Returns the value of the expression if it has a single value for all rows. Otherwise returns an asterisk. Nulls are ignored.


* To ilustrate: LODs (Exclude) - 1 sheet
    - Duplicate Map Review Sheet.
    - Expand to city.
    - Adjust transparency to 80% and add a border in colour button.
    - Duplicate map (duplicate longitud in columns)
    - Create calculated field LOD EXCLUDE State Profit:
        - { EXCLUDE City: SUM([Profit]) }
    - Drag the calculated field over colour and tooltip to replace the previous.


* To ilustrate: LODs (Exclude) - 2 Proportion sheet:
    - Duplicate LODs (Exclude) - 1 sheet.
    - Remove the calculated field from colour and label in the first map. 
    - Drag the profit again to label button.
    - Double click on the field in label detail and write: 
        - SUM([Profit]) / ATTR([LOD EXCLUDE State Profit])
    - Copy this agg field to color and size.
    - Drag the profit and LOD exclude to tooltip.
    - It looks good but there are some misleading items: 
        >* (1) negative numbers are taken low in size legends, we need big neg numbers in big circle because that is the proportion related with profit. Fix:
        >   * In size, click the field and add the ABS function:
        >       * ABS( SUM([Profit]) / ATTR([LOD EXCLUDE State Profit]))
        >* (2) color do not reflect the negative/positive correct relation: neg prof city / neg prof state = pos, color will be according, but we need in those case be the opossite. Fix
        >   * In color, click the field and add:
        >       * SUM([Profit]) / ATTR([LOD EXCLUDE State Profit]) * SIGN( ATTR([LOD EXCLUDE State Profit]))
        >* (3) if we expand the map to postal code all caluclation are a mess because EXCLUDE only take in considetation city, and no we are in a deeper level. Fix:
        >   * Add post code to the EXCLUDE calculated field:
        >       * { EXCLUDE [City], [Postal Code]: SUM([Profit]) }
    - Adjust size and color transparency (75%)

* To ilustrate: LODs (Fixed) - 1:
    - Duplicate LODs (Include) sheet
    - Create parameter: LOD FIXED city profit:
        - { FIXED [Country], [State], [City] : SUM([Profit]) }
    - Drag the calculated field over color and label to replace. Measure AVG

* To ilustrate: LODs (Fixed) - 2:
    - Duplicate LODs (Exclude) - Part 2:
    - Create parameter: LOD Fixed State Profit:
        - { FIXED [Country], [State] : SUM([Profit]) }
    - In marks card, replace parameter "[_LOD EXCLUDE State Profit]" with "_LOD Fixed State Profit" on colour, size, label, and tooltip.

4. Follow steps in LODs (Fixed) sheet
5. Duplicate map (duplicate longitud in columns, drag + ctrl longitud from column to column again)
6. On the first map, remove fields from colour, size, label, tooltip.
7. Colapse to State.
8. On the second longitud in columns: click right >> dual axis.
9. Hide size card and colors.


> Data source:
>* [Section 6 – The Challenge.pdf](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section6-The-Challenge.pdf)
>* [MegaMerchandise.xlsx](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-MegaMerchandise.xlsx)

> Dashboard: [LODS](https://public.tableau.com/app/profile/jacesca/viz/6_LODsINCLUDEEXCLUDEFIXED/CombinedVisualization?publish=yes)


# 7: Advanced Mapping Techniques
| Area | Concepts |
| ---- | -------- |
| Polygons | Points: X & Y coordinates |
|  | Direction: path |
|  | Unique Identifier: Shape ID |
| Endless possibilities | Any image file as background for map |
| Blending | Validate Blend Relationships to ensure relation is on the correct fields |
| Parameters | Not available for background images |
|  | Solved using calculated fields |
| Drawing tools | [cbistudio](https://cbistudio.interworks.com/) |
|  | Works very well to define points on maps |
|  | Able to use images either |
| Custom shapes | It can be customized adding a folder with the icos in the Local Tableau Repository |
| Joins files to itself | To get combinations of record (join based on <>) |
| Greate Circle Distance | Using the new Distance function |
| Map Services | Built in |
|  | WMS Servers |
|  | [MapBox](mapbox.com) |
|  | [MapTiler](https://cloud.maptiler.com/) |

### 7.1 Working with Polygons
Steps:
1. Loading polygon data.
2. Drag x to columns and y to rows.
3. Drag shape to colour.
4. Try marks from automatic to Polygon.
5. Drag path order to path button in the chart.


### 7.2 Study case: Meeting Rooms
Steps:
1. Load Meeting Rooms name and shapes.
2. Drag x to columns and y to rows.
3. Add room to colour.
4. Add floor to filter.
5. Change chart mark to polygon.
6. Add path field to path button.
7. Go to map menu >> Background images >> [meeting rooms dataset name]:
    - click add images >> Name Ground floor >> look for the ground floor image and select it >> select x for x field and y for y field >> add the dimension of the file (you can view it in the file property, e.g. 2481 X 1754) in right (2481) and top (1754) of x and y fields >> save and close.
8. Load meeting utilization file.
9. Review that the blend relation is made on room.
10. In the marks card change the colour type of the room to detail (click-right on the colour icon and change it).
11. Drag booked utilization over the colour and change the meadure to average.
12. Customize colour (red-blue divergent, reverse, advanced: 0-100)
13. Create parameter "Select Floor" to control the filter and the background image (type: string, list, add values from room file floor field)
14. Hide floor filter card.
15. Edit floor filer in filter card (General tab: use all, condition tab: by formula >> "[Floor] = [Select Floor]")
16. Select Ground in "Select Floor" parameter.
16. In the primary data source, create a calculated field "Floor Image Selection": [Select Floor]
17. Go to map menu >> Background images >> [meeting rooms dataset name]
    - select ground floor name, and click on edit.
    - go to tab options
    - mark lock aspect ratio
    - click add and select "Floor Image Selection"
    - click ok and select "Ground"
    - click ok, apply, ok, ok
    - the image is not showed because the Floor Image Selection is not available in the chart. To fix it, just drag it to the Detail button.
18. Repeat steps 7 and 17 to add the first floor image. Be aware that you have selected first on the Select Floor parameter before start.
19. Both images need to be selected in Go to map menu >> Background images >> [meeting rooms dataset name]
20. In the room utilisation dataset create a parameter "Select visualisation" (type: string, list -> add manually: Actual, Booked). Show the parameter.
21. In the room utilisation dataset create a calculated field "Utilisation" (IIF([Select Visualization] = "Actual", [Actual Utilisation], [Booked Utilisation]))
22. Drag the new calculated field "Utilisation" to the colour and adjust color again as defined in step 12.
23. Hide Axis.
24. Adjust tooltips.




### 7.3 Drawing tool for tableau
Steps:
1. Go to https://georgiamountainfairgrounds.com/pageserver/seating-chart
2. Save the URL of the seeting chart image.
3. Go to https://powertoolsfortableau.com/
4. Select Drawing Tool For Tableau.
5. Load image by url:
    - Click on image (left upper corner).
    - Image Source: URL
    - Copy the saved URL of the seeting chart image.
    - Clic on load from URL.
5. Activate Show coordinates, guideline, show grid and snap to grid.
6. Select Polygon
7. Mark all the polygons in the image.
8. Edit labels

### 7.4 Coffee Proximity
Steps:
1. Load NY Stores xls file.
2. Create the Store Locations sheet
    - Drag together latitude & longitud into the drop field here section of the sheet.
    - Drag store ID to the detail button.
    - Drag MonthlyTurnover to Colour and Size.
    - Change color to green.
    - Change Marks type to shape.
    - Copy the cofee icon to C:\Users\jaces\Documents\My Tableau Repository\Shapes\CoffeCustomIcon
    - Click on shape button.
    - Click reload shapes.
    - Look for the CoffeeCustomIcon and select the cofee icon
    - Calculate distances:
3. Load again NY Stores file and join on it self (StoreId <> StoreId, inner join). Rename it as NY Stores Distances
4. Create the Store Distances
    - We are going to use the [Great-circle distance](https://en.wikipedia.org/wiki/Great-circle_distance). It is the shortest distance between two points on the surface of a sphere, measured along the surface of the sphere.
    - Formula to apply: 
    $${\displaystyle \Delta \sigma =\arccos {\bigl (}\sin \phi _{1}\sin \phi _{2}+\cos \phi _{1}\cos \phi _{2}\cos(\Delta \lambda ){\bigr )}}$$
    - In NY Stores Distances create calculated fields:
        - Distance_OldMethod
            - 3959 * ACOS(
SIN(RADIANS([Latitude])) * SIN(RADIANS([latitude (Sheet11)])) + 
COS(RADIANS([Latitude])) * COS(RADIANS([latitude (Sheet11)])) * 
COS(RADIANS([longitude (Sheet11)]) - RADIANS([Longitude]))
)
        - Distance_NewMethod
            - DISTANCE(
MAKEPOINT([latitude (Sheet11)], [longitude (Sheet11)]),
MAKEPOINT([Latitude], [Longitude]), 
'mi'
)
        - Too Far
            - IIF(MIN([Distance_NewMethod]) > 0.5, 'Yes', 'No')
    - Drag latitude & longitud to the sheet.
    - Drag store id to the detail button.
    - Shange Marks type to shape and select the coffee icon in shape.
    - Adjust size to bigger (a little).
    - Drag toofar into color.
    - Drag DistanceNewMethod to size, and set measure to MIN.
    - Drag StoreName to tooltip.
    ------------------------------------
    - Create a custom map in https://cloud.maptiler.com/ and save it locally.
    - Go to menu Map >> Background Map >> Manage Maps >> Import and select the custom map you created. (Add is for WMS (Web Map Servers))
    --------------------------------------
    - Customize the map layers.


### Data source, dashboard and extra tools
> Data Source:
>* [Polygon Data](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Polygon-Data.xlsx)
>* [Seeting Chart](https://georgiamountainfairgrounds.com/pageserver/seating-chart)
>* [Section 7 – Challenge I](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section7-Challenge-I.pdf)
>   * [Meeting Rooms](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Meeting-Rooms.xlsx)
>   * [Meeting Rooms Utilisation](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Meeting-Rooms-Utilisation.xlsx)
>   * [Office Floor Plan Ground Floor](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Office-Floor-Plan-Ground-Floor.jpg)
>   * [Office Floor Plan 1st Floor](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Office-Floor-Plan-1st-Floor.jpg)
>* [Section 7 – Challenge II](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-Section7-Challenge-II.pdf)
>   * [NY Stores](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-NY-Stores.xlsx)
>   * [Coffee Icon](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P11-coffee.png)

> Additional Tools:
>* [Tools for tableau](https://powertoolsfortableau.com/)
>* [Great-circle distance](https://en.wikipedia.org/wiki/Great-circle_distance)
>* [MapBox](mapbox.com)
>* [MapTiler](https://cloud.maptiler.com/)

> Dashboard: 
>* [Polygons](https://public.tableau.com/app/profile/jacesca/viz/A7_1-Polygons/Polygonsvisualization)
>* [Meeting Rooms](https://public.tableau.com/app/profile/jacesca/viz/A7_2-MeetingRooms/Summary)
>* [Custom Polygons](https://public.tableau.com/app/profile/jacesca/viz/A7_3CustomPolygons/Story1?publish=yes)
>* [Great-circle distance](https://public.tableau.com/app/profile/jacesca/viz/A7_4Great-circledistance/StoreDistances?publish=yes)
