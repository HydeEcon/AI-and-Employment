# AI-and-Employment
Talks about AI and how it impacts the job market, and employment in general have been going on for years now, and as AI continues advancing, these discussions will only get larger.  I wanted to add to this discussion be preforming a Diff-In-Diff and a regression to determine whether or not AI actually has an impact on the job market, or if it's all just a bunch a fluff.

First the Diff-In-Diff: Diff-In-Diff is a common tool for causal analysis.  By looking at 2 similar data sets, ideally a data set where the only difference is the implementation of a treatment (a variable we are trying to determine the effects of) and taking the difference between the data sets be and after a treatment has been implemented, we can get a Diff-In-Diff that should tell us the significance of a treatment.

For my two data sets, I looked at the employee count of both Nintendo and Electronic Arts (EA).  These are 2 similar companies, both massive leaders in the video game industry, however one company (EA) has openly supported and implimented AI in their company, where as Nintendo has been a lot more cautious of AI usage.

In order to confirm the similarities between EA and Nintendo, I ran a correlation matrix:

<img width="693" height="591" alt="image" src="https://github.com/user-attachments/assets/7ecbf01f-6e06-4ca5-8e19-63d77020cd91" />

The two employee counts have a ~97% possitive correlation.  With this in mind, let's run the Diff-In-Diff.

To preform the Diff-In-Diff, we are going to look ad the differences in the employement rate before and after AI widespread AI usage:
EA mean Employment rate before AI: 2.76%
Nintendo mean Employment rate before AI: 1.73%

Now lets look at the rate after:
EA mean Employment rate after AI: 6.22%
Nintendo mean Employment rate after AI: 5.53%

Now for the Diff-In-Diff; we are going to examin the difference in EA's mean employment rate minus Nintendo's difference:
EA diff: 3.47%
Nintendo diff: 3.80%
Diff-In-Diff: -0.33%

So what does this mean? It means comparatively, EA had a employment rate was 0.33% lower than Nintendo's after AI usage became widespread.  Overall this number is extremely small (0.0033) and suggests that AI did NOT have a major impact on EA's hiring rate.

Why is this? We have been hearing for a while now that AI is going to take over the workforce, however, as we see, it barely has an impact.  This could be for a few reasons, maybe EA switched their hiring strategy, from video game developers to AI developers. Maybe AI isn't advancced enough to preform the tasks required at EA. There are numerous reasons as to why AI hasn't had an impact, however, it is important to note that this looks at one company in one industry.  As a result, the actual impact of AI could still be affecting jobs, just maybe not at EA or in the Gaming Industry.
