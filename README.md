# Do 'feminised' government workplaces pay less?

(TL;DR: No.)

I've examined this question several times but it keeps popping up. So I'm publishing this analysis — and the relevant data — here for when it's next asked.

The Australian Public Service (APS) decentralised pay bargaining in the 1990s. In the years since, unions and some politicians said agencies with a higher proportion of female staff pay less than others. The Community and Public Sector Union repeated this argument in the lead-up to this year's APS enterprise agreement (EA) negotiations.

The Albanese government [says it is trying to reduce pay gaps between APS agencies](https://www.abc.net.au/news/2023-06-02/which-public-servants-will-receive-a-pay-boost/102420798). To aid this, the Australian Public Service Commission (APSC) collated and shared the salary ranges of 103 APS agencies. I've combined these data [with other APSC employment data](https://www.apsc.gov.au/employment-data/aps-employment-data-31-december-2022) to understand the associations between a workforce's gender split and the salaries they receive. The two datasets — salaries and staff headcounts — were correct as of December 31, 2022.

(You can access the [Python script I used for this analysis here](./data/analyse_data.ipynb).)

## Examining the data

This analysis omits six agencies, because the APSC excludes them from its staff headcounts (and I was too lazy to fetch their data). That leaves 97 agencies — close to a census of APS staff. The excluded agencies are:

* Australian Office of Financial Management
* Commonwealth Grants Commission
* Domestic, Family & Sexual Violence Commission
* IP Australia
* Royal Australian Mint

The analysis also excludes senior executive service (SES) officers, most of whom are employed on individual contracts. Also, graduate staff are categorised as APS3 officers — the level at which almost all of them are employed.

The plot below shows that almost half (44.6%) of all non-SES staff are employed as APS6s or EL1s.

![A bar chart showing APS staff numbers by job level.](./data/staff_levels.png)

The APS is a largely feminised workforce, both overall and at each job level. 60.7% of the staff included in this analysis are women. Some agencies are extremely feminine at some levels; others are extremely masculine. But in general, the "femininity" of the 97 workplaces are normally distributed. (Each circle in the plot below represents one agency's employee cohort at that level.)

![A strip plot showing, for each job level, the proportion of agencies' staff who are women.](./data/female_staff.png)

The combined salary and staffing data allow us to examine any correlations — and to understand whether feminised workplaces pay less.

I use APS agencies' minimum salaries in this analysis, as I believe they more closely reflect the salaries of most staff. Minimum salaries are also more likely to represent alternative salaries for staff seeking to leave a low-paying workplace.

The plots below show no clear association between the proportions of agencies' staff who are female (x-axis) and the agencies' salaries (y-axis). (The circle sizes reflect the number of staff in that agency at that level.)

![A series of eight scatterplots showing a lack of correlation between female staff and salaries.](./data/salary_levels.png)

## Calculating correlation

A visual inspection of the plots above is enough to answer the original question: no, feminised workplaces are not paid less.

However, we can measure the correlation (the **R squared** value) precisely.

These are the results of linear regressions at each job level, using the percentage of staff who are women to predict an agency's salary. I tested both the minimum and maximum salaries:

### **Regression results**

| job level | min. salary | max. salary |
| --- | --- | --- |
| APS1 | 0.8% | 0.1% |
| APS2 | 1.0% | 1.8% |
| APS3 | 1.2% | 0.0% |
| APS4 | 0.8% | 0.0% |
| APS5 | 0.5% | 0.1% |
| APS6 | 0.0% | 1.5% |
| EL1 | 0.1% | 0.0% |
| EL2 | 1.2% | 0.4% |