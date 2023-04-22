# Tableau tips

**In dashboards**
* To handle the width of containers, everything need to be in a container first. (click right on container)

**In Sheets**
* Click & hold on a column field, and when it is over the colors press ctrl and when the plus sign is visible let it go, then move the color category below the marks.
* To organize fields in the left panel area, click right on white space (better at the bottom) and then group by folder (default: group by DataSourceTable).
* Dimensions in blue, measures in green. If a dimension is showing in green, drag it to meausere space and then returning to the dimension space to allow Tableau recognize it correctly (Issue in Tableau environment).
* Hack: To set the format property on a field so each time you use it, you do not need to go to format: right click on field >> Default properties >> Number format.
* To adjust the graph into the sheet: select fit height on the bar menu dropdown fit.
* To avoid trend lines being calculated each time points are selected: right-click on trendline >> edit >> unmark show recalulated line for highlighted or selected data points.
* To see data related to a point in the chart, select one or more points and click on the view data icon of the showed tooltip.


**Table calculations**
* Table calculation are conducted after aggregation has been performed. Eg. Quick label calculations (e.g. Running total, difference) and relative to (Previous, Next, First, Last), powerful tool in the possible calculation can be configured on a field in a chart.
* To get the calculations of sheet: click right on the sheet tab name >> duplicate as crosstab


**Charts**
* On scatter plots to disagregate: go to menu >> analysis >> uncheck aggregate measures.
* To show a bar chart of cases by age:
    * Add age field to columns.
    * Change it to dimension.
    * Add cases to rows.
    * Change thw quick table calculations (right click on the cases field) to percent of total.
* Highlighters can be added from the fields (in details). Click right >> show highlighter.
* Clusters used for segmentation (Left panel >> Analytics tab >> Double click on Cluster)
* To add trends (line tendency): Left panel >> Analytics tab >> Trend line (Model). 
* To avoid trends is recalculated twice: Right click on any trend lines >> Edit All trend lines >> Unmark show recalculated line for highlighted or selected data points.
* To select just the top 5: move the field to filter >> Select Top tab >> Select By field >> set top and number >> select field and measure >> click ok button.
* Hack: To reverse/flip a chart: right click on the axis to reverse >> edit axis >> mark reversed (scale) >> click ok.
* To add multiples criteria to colour in a chart, select all the fields you want to be part of the criteria and move them together to colour.
* To add a reference line: right-click on the axis >> add reference line >> set the value to the correct parameter >> set label to value >> click ok.
* Drop lines (on scatter chart right click on empty space and select drop lines) shows you the reference to the selected point.
* To create BoxPlots: 
    * Click on Analytics on the left panel >> drag the box-plot over the bar-circle chart and let it go.
* In trend lines, if you want to hide one in a multiple line chart, just click right on the space of the specific one space of the multiline chart >> trend lines >> unmark show trend lines.
* In a buble chart, you can customize order of the categories defined in color button following: localizing the proper field >> click right >> default properties >> sort >> sort by manual >> setting the orderd >> close.

**Parameters**
* Parameters easy to create from the parameter left-bottom side area (right click - create parameter).
* Parameters can be formatted also to express currency ($), thounsands (K), millions (M), etc.

**Groups and sets**
* To create groups: click-right on the field (left side panel) >> Create >> Group >> select what to group >> click Group >> Set a name for the group >> Unmark Include Others >> Apply >> Ok. Now you can use this new field in other charts as Bar or Pie.
    * A second method is to select the labels in a bar chart to group categories.
    * Notice that groups retaque all individual values to get the required measure e.g. avg. (not making avg of avg but avg of all the items included in the group).
* To create set: select the labels in the chart and click on the set icon and select create Set. 
    A second method is click right on the field >> Create >> Set 
* To create dynamic sets: Go to the field (please select unique keys) in the left panel >> right click >> create >> set >> on general tab: put a name, select use all >> set a condition or define the top criteria (choose the proper tab) >> click ok.
* Combined sets are only possible if each of them is based on the same dimension.
* To create combined sets: right click on one of the sets >> create combined set >> put a name >> set the 2 sets >> select combination type >> click ok.
* To add parameters to sets with defined condition, a formula with the condition referring the parameter need to be added, for that "by formula" option need to be selected in the condition tab of the set.

**Histograms**
* To create bins: right click on the field >> Create >> Bins >> Set a name and size.
* To create a parameter to adjust the bins in our histogram:
    * Click right on the white space in left panel.
    * Select Create parameter.
    * Set the name, data type, select kist in allowable values, set minimum, maximum, and step size.
    * Click right on the created parameter and select show parameter.
    * Click right on the field bins we need to link and select edit.
    * Click on the size of bins and select the created parameter.

**Maps**
* To set geographic roles: Right click the appropriate field and select the appropriate geographic role.
* To split, select column -> Click right -> split and set configuration (e.g. ' ' as separator and only last)
* For unknown values: Edit locations, filter exclude, or default value/position.
* For maps, it is important to align the location when we only have the city names (map >> edit locations).
* For regions not recognized a map: we can select the field >> click right >> Geographic role >> Create from >> select the associated field.
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

**Data source tab**
* To make unions, hold on the second table and move it over the fist one until UNION shadow appears.
* To read pdf, the "Cleaned with Data Interpreter" option will be help full (Mark it!).
* When reading pdf some field may be splitted to merge them: select the column fields >> click right >> select merge...
* Sometime when reading a table in pdf file, the total row is also included, to remove it: on the data source tab select filter add from the right up corner >> click the add button >> select the field to set the condition >> click ok button >> set the value (e.g. select from list, none, look for the total, mark it) >> mark exclude >> click ok button >> click ok button again.
* On data source tab, we can change the type of a field by right click on the type in the header of the field and selecting the new type associated (including geographic role).
* When there is missing data points in drawing the map, validate location (Edit location) to match the country with what geographic points are referring.
* Some times it is necessary to make a blend join with a table based on the Quarter/Year, you can customize it in menu data >> blend relation >> modify it to add year and quarter from the date. If you need to have this blend relation in your dashboard, you need to drag the date, as many times as you define in the blend relationship, to detail button.
* To add forecast, just go to Analytics in left panel and drag the forecast model to the chart.