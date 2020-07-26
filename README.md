# Kickstarter-Analysis
Trend analysis of Kickstarter data

### Background
A dataset of over 4k elements is analyzed to show trends in Kickstarter campaign performance. Independent variables, launch date and fundraising goal, are observed for their effect on theater fundraising campaign outcome: successful, failed, cancelled. We intend to use this data to increase the liklihood of a successful, theater fundraising campaign.
### Analysis
From the raw dataset, unix timestamps are converted to readable dates, then further reduced to years.
'''
J2 = Unix timestamp
S2 = (((J2/60)/60)/24)+DATE(1970,1,1)
V2 = YEAR(S2)
'''
Using pivottable, a breakdown of outcomes is observed over launch month.
