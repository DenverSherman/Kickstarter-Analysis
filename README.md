# Kickstarter-Analysis
Trend analysis of Kickstarter data

### Background
A dataset of over 4k elements is analyzed to show trends in Kickstarter campaign performance. Independent variables, launch date and fundraising goal, are observed for their effect on theater fundraising campaign outcome: successful, failed, cancelled. We intend to use this data to increase the liklihood of a successful, theater fundraising campaign. A breakdown of analysis is outlined by tab below, followed by a results section.
### Analysis - Launch Date
From the raw dataset, unix timestamps are converted to readable dates, then further reduced to years.
```
J2 = Unix timestamp
S2 = (((J2/60)/60)/24)+DATE(1970,1,1)
V2 = YEAR(S2)
```
Using a pivotchart, a breakdown of outcomes is observed over launch months. This chart and accompanying table are available in the **'Outcomes Based on Launch Date'** tab. The settings of the pivotTable are adjusted to show empty cells as 0, correcting the discontinuity for the October canceled line.

![Launch Date Trend](https://github.com/DenverSherman/Kickstarter-Analysis/blob/master/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis - Goal
Next, we create a new tab, **'Outcome Based on Goal'**. Goal groups are outlined as less than 1000, between 1000 and 4999 (then add 5000 to both boundaries until 49999) and Greater than 50000. Each upper and lower group boundary is placed in a hidden column. To count occurences of each outcome by goal, we use countifs as follows:
```
'Parent Data'!F:F = Outcome = {"Successful", "Failed", "Canceled"}
'Parent Data'!D:D = Goal = Amount requested
'Parent Data'!R:R = Subcategory
A:A = Lower Bound
B:B = Upper Bound
=COUNTIFS('Parent Data'!F:F,"Successful",'Parent Data'!D:D,">="&B3,'Parent Data'!D:D,"<="&C3,'Parent Data'!R:R,"plays")
```
Formula quoted above is for the highlighted cell. For group 'Greater Than 50000', the upper bound criteria is removed.

![Outcomes Based on Goal Table](https://github.com/DenverSherman/Kickstarter-Analysis/blob/master/Resources/CountIfs_Analysis.png)

![Outcomes Based on Goal](https://github.com/DenverSherman/Kickstarter-Analysis/blob/master/Resources/Outcomes_vs_Goals.png)

### Results
From the observational data given, we can draw conclusions on how to increase the liklihood of thater fundraising campaign success. First, **Campaigns launched in Late Spring and Summer tend to be more successful**. We observed 65% percent campaign success from May to July contrasting a 58% success rate December to February. In total, about 61% of theater campaigns are successful. **May seems to be the ideal launch date for our campaign**, with an observed 66% success rate. For our fundraising goal of $12,000, previous campaigns for plays show about **54% success rate within our goal range**. An increase in the goal would expect a decrease in the success rate as $15000 to $19999 slides to 50%.
