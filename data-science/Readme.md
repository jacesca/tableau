# Data Science: Hands-On Exercises
Developed exercises are visible at [Tableau Jacesca's Profile](https://public.tableau.com/app/profile/jacesca/).<br>
Material can be found [here](https://www.superdatascience.com/pages/training).


# Data Science - Visualization
* Fields in Tableau are broken up into dimensions (blue) and measures (green).
* Calculated fields are custom variables created from fields provided in data.

> Data Source: [Office Supplies](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P12-OfficeSupplies.csv)

> Dashboard: [DS1 - BarPlot](https://public.tableau.com/app/profile/jacesca/viz/DS1-Barplot/Summary)


# Data Science - Ad-Hoc A-B Test
Using Ad-Hoc A-B tests to find anomalies.

**Challenge**: Prepare an A/B Test, with the premise "If we hold everything else equal and we take a make customer and a female customer which one of them is more likely to exit".

Steps:
* In gender sheet, follow:
    1. Click on cnt(churn modeling) in label
    2. Select Add Table Calculation
    3. Calculation Type: Percent of Total & Compute using Table Down
    4. Close
    5. Now we copy this field from label to rows, replacing the previous. (Hold +Ctrl and Drag to rows).
    6. Set alias for Exited (Click-right on Exited >> alias)
    7. Change order, moving Exited above cnt field.
    8. Add a reference line (label None)with the global Exited, you can take this value by removing temportally the gender from columns.

* Repeat the steps to create sheets for country, has a credit card, is active and number of products, duplicating the sheet and just replacing the column.

* Validation sheet
    1. **Find a variable that you are sure does not affect the result in the choice of customers to stay or exit**
        > (e.g. phone-number, id, etc.)<br>
        > Letters are tricky because they are generally less uniformly distributed as numbers.

    2. Create a calculated field on that variable found (In the example we use Customer ID) to extract the last digit and use it to demostrate that probability is not affected by this variable (replicate the last sheet and use this variable to test if the global average of exited 20% remains)

> Data Source: [Churn Modelling](https://sds-platform-private.s3-us-east-2.amazonaws.com/uploads/P12-Churn-Modelling.xlsx)

> Dashboard: [DS5 - Ad Hoc A-B Test](https://public.tableau.com/app/profile/jacesca/viz/DS5-AdHocA-BTest/Story1?publish=yes)
