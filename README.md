# AI-and-Employment
Talks about AI and how it impacts the job market, and employment in general have been going on for years now, and as AI continues advancing, these discussions will only get larger.  I wanted to add to this discussion be preforming a Diff-In-Diff and a regression to determine whether or not AI actually has an impact on the job market, or if it's all just a bunch a fluff.

# Diff-In-Diff Test

First the Diff-In-Diff: Diff-In-Diff is a common tool for causal analysis.  By looking at 2 similar data sets, ideally a data set where the only difference is the implementation of a treatment (a variable we are trying to determine the effects of) and taking the difference between the data sets be and after a treatment has been implemented, we can get a Diff-In-Diff that should tell us the significance of a treatment.

For my two data sets, I looked at the employee count of both Nintendo and Electronic Arts (EA).  These are 2 similar companies, both massive leaders in the video game industry, however one company (EA) has openly supported and implimented AI in their company, where as Nintendo has been a lot more cautious of AI usage.

In order to confirm the similarities between EA and Nintendo, I ran a correlation matrix:

<img width="693" height="591" alt="image" src="https://github.com/user-attachments/assets/7ecbf01f-6e06-4ca5-8e19-63d77020cd91" />

The two employee counts have a ~97% possitive correlation.  With this in mind, let's run the Diff-In-Diff.

To preform the Diff-In-Diff, we are going to look ad the differences in the employement rate before and after AI widespread AI usage:
* EA mean Employment rate before AI: 2.76%
* Nintendo mean Employment rate before AI: 1.73%

Now lets look at the rate after:
* EA mean Employment rate after AI: 6.22%
* Nintendo mean Employment rate after AI: 5.53%

Now for the Diff-In-Diff; we are going to examin the difference in EA's mean employment rate minus Nintendo's difference:
* EA diff: 3.47%
* Nintendo diff: 3.80%
* Diff-In-Diff: -0.33%

So what does this mean? It means comparatively, EA had a employment rate was 0.33% lower than Nintendo's after AI usage became widespread.  Overall this number is extremely small (0.0033) and suggests that AI did NOT have a major impact on EA's hiring rate.

Why is this? We have been hearing for a while now that AI is going to take over the workforce, however, as we see, it barely has an impact.  This could be for a few reasons, maybe EA switched their hiring strategy, from video game developers to AI developers. Maybe AI isn't advancced enough to preform the tasks required at EA. There are numerous reasons as to why AI hasn't had an impact, however, it is important to note that this looks at one company in one industry.  As a result, the actual impact of AI could still be affecting jobs, just maybe not at EA or in the Gaming Industry.

For visual, heres the two companies regression"

<img width="991" height="599" alt="image" src="https://github.com/user-attachments/assets/adaa7402-0e7f-41a4-ae89-5acbc2dae596" />

# Regression

Determining the affect AI has on the economy is slightly harder, as there are no control groups to make a Diff-In-Diff (No Economy similar to the US, that doesn't have AI), so determine it, I created an employment prediction regression, using factors like Employment Cost Index and Job Openings to predict how many people are employed at a given time, we can then plug in AI usage and determine how great of an impact it has on the regression (compared to the other variables). This method isn't perfect however, as it tend to show correlation more so than causation.

To make the Regression, I looked at Employee cost index, average weekly wages, job openings and the unemployment rate, and how they can determine how many people are employed at a given time. These are the results:

<img width="443" height="615" alt="image" src="https://github.com/user-attachments/assets/309fd1d3-9b89-4af1-8a33-e7857f3a99d1" />

What's important here? the R-squared value is significantly high, at 99.5%, meaning these variables can explain 99.5% of the variation in the amount of people employed. The P-Value is also important here, a P-Value for a variable must be less than 0.05, in order for that variable to be considered statistically significant.
* ECI (Empployee Cost Index) P-Value = 0.026, statistically significant
* AWW (Average Weekly Earnings) P-Value = 0.154, statistically insignificant
* JOIT (Job Openings (in Thousands)) = 0.634, statistically insignificant
* U-Rate = 0.0, statistically significant

ECI and U-Rate hold the most statistical significance when determining how many people are employed, at least according to this model.  Now lets run a regression, using the AI variable:

<img width="438" height="649" alt="image" src="https://github.com/user-attachments/assets/ae1dd5e6-1acd-44b7-92d0-9d7a54508540" />

Whats important:
* R-Squared = 1, this is almost too high, possible overfitting of the model
* ECI P-Value = 0.006, significant
* AWW P-Value = 0.008, significant
* JOIT P-Value = 0.055, borderline significant, however technically insignificant
* U-Rate P-Value = 0.039, significant
* AI Usage = 0.146, insignificant

With this in mind, we can determing that the amount of AI being used is not statistically significant when predicting the amount of people employed, i.e. AI is not taking jobs (as of yet), at least when compared to other factors like how much empoying someone costs .
It is very important to keep in mind that these data sets are very small, due to how early AI is in it's development, and while right now we can say that AI doesn't have an impact on jobs, that might change in the future, especially with how fast the development of AI continues.

# Notes

Both regression models have extremely high condition number, which could possible lead to P-Values being innaccurate.  I do not know how to fix this yet, so it is important to keep that in mind. Also, I didn't look at the coefficients of the variables, as I didn't think they were necessary for intrepretation. The Diff-In-Diff for ea doesn't look at exactly when AI was used in EA, as that was hard to figure out, so that is why it looked at AI usage in total.

# Sources

https://www.macrotrends.net/stocks/charts/EA/electronic-arts/number-of-employees for EA employee data
https://www.macrotrends.net/stocks/charts/NTDOY/nintendo/number-of-employees for Nintendo employee data
https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai to determine AI usage
Fred for Persons Employed, ECI, Average Weekly Earnings, Job openings
