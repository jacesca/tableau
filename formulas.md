# Expressions to use in Tableau Formulas

### To extract string in parenthesis from a text:
>REGEXP_EXTRACT([MetricByMachine], '\(([^\[]*)\)')


### To extract string before one specific character in a text:
>TRIM(REGEXP_EXTRACT([MetricByMachine], '([aA-zZ ]+)\('))


### LOD Include
Take sum(profit) in city level, so if in state the measure is avg will be avg(sum)
>{ INCLUDE [City]: SUM([Profit]) }


### LOD Exclude
exclude city of the calculation, so the sum is executed in the next level (state)
> { EXCLUDE City: SUM([Profit]) }


### If-else in one line:
> IIF([Select Visualization] = "Actual", [Actual Utilisation], [Booked Utilisation])


### Great-circle distance
It is the shortest distance between two points on the surface of a sphere, measured along the surface of the sphere

Old method:
> 3959 * ACOS(
SIN(RADIANS([Latitude])) * SIN(RADIANS([latitude (Sheet11)])) + 
COS(RADIANS([Latitude])) * COS(RADIANS([latitude (Sheet11)])) * 
COS(RADIANS([longitude (Sheet11)]) - RADIANS([Longitude]))
)
> <br><br>Note: 3959 is to transform to miles, for kilometers replace it with 3440.

New method:
> DISTANCE(
MAKEPOINT([latitude (Sheet11)], [longitude (Sheet11)]),
MAKEPOINT([Latitude], [Longitude]), 
'mi'
)
><br><br>Note: 'mi' is for miles, 'km' is for kilometers.
