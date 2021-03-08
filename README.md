# Prosper-EDA
Prosper is a peer-to-peer (P2P) lending platform. Investors on the site can invest as little as $25 in personal loans to other people. All personal loans issued on the site are unsecured personal loans with fixed interest rates.  Throughout this project I try to perform Exploratory Data Analysis and visualize the main insights regarding some questions, mainly:  What was the reason behind the company reconstruction in 2009? What affects the borrower’s APR or interest rate?

## Dataset

This data set contains 113,937 loans with 81 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, and many others.


## Summary of Findings

I divided the dataset variables into four main categories: Loan, Borrower, Credit Risk Metrics, and Prosper Customers Historical Data
###  Loan Data
- Loan Amount: Except for peaks at 10k and 15k, loans are log-normally distributed around a mean of $ 5K.
- It looks like Prosper had a rough start during the first 3 years, followed by a shutdown in the first quarter of 2009 then the number of loans started to increase steadily for the next 4 years. Finally the number of loans hit the roof all of a sudden starting from the second quarter of 2013.
- Most of the borrowers prefer the 3-year long term over the others.
- Over half of debts is directed toward paying other debts! About 25% is either not available or not covered by categories offered by Prosper. The remaining 25% is mainly dominated by Home Improvement or Business purposes.
- Borrower Rate: The distribution is mostly normal around 0.18 except for a spike at 0.32.
- 50% of loans are up in the air, and we don't know if they would be completed or defaulted.
Judging by these numbers, current loans have nearly twice the chance to be completed rather than (defaulted, chargedoff, or getting Past Due)

###  Borrower Background
- Top 5 states with the biggest number of customers: California, Texas, New York, Florida, and Illinois
- Obviously, the greatest proportion of borrowers are employed or working full-time jobs, but it's intriguing to find out why retired and not employed are guranteed loan in the first place. These two categories most probably have a very strong credit or some sort of a helthy investment to prove their worth of a loan we need more digging!
- Employment Status Duration: The distribution is heavily right-skewed. Many borrowers tend to apply to and receive a loan at the beginning of their tenure irrespective of their employment status.
- Income Range: Most of the borrowers fall in the middle-income ranges (25k - 75k)
- Monthly Income: The distribution follows a normal distribution on the log scale and the mean value seems to sit around $ 5K
- Occupation: Many borrowers can't identify themselves with an occupation suggested by Prosper or maybe they don't want to reveal that piece of information as indicated by Other. However, Compouter Programmers and Analysts are among the top 10 clients while Students don't borrow that much!
- Unlike home ownership, it's clear that having a verifiable source of income greatly boosts the ability of a person to borrow a loan

###  Credit Risk Metrics
- Credit Grade & Prosper Rating: Before 2009, the distribution was normal with a peak around the C grade, with little variation between different grades in the number of loans in each bucket.
However, after 2009 there not only is there a more noticeable peak around the C grade but also, the variance between categories percentages increased. Especially for HR and AA ratings, where percentages got cut in half!
The new metric for credit rating lowered the percentage of HR loans and AA's as well. It also prohibited giving loans to borrowers with no credit (NC)
- Prosper Score: There are three peaks at Prosper Scores of 4, 6, and 8 and the distribution is fairly normal.
- Before Prosper recounstruction, the company allowed credit scores above 400 with some outliers whose credit score is just positive. And the distribution was normal around a peak of nearly 620 points.
After 2009 and reconstruction, the minimum credit score to secure a loan is about 610 points and the distribution is right skewed. And the mode is around 700 points.
- Credit Inquiries: When I removed outliers from the pre-09 plot (44 records having more than 30 inquiries), the shapes of distribution became nearly identical with the post-09 plot. However, there appears to be a bias toward borrowers with a small number of inquiries (Indicated by the differenc in counts of first five consecutive bins)
It looks like an upper limit was posed on the number of inquiries allowable per credit profile in the company's second iteration (27).
- Delinquencies: Distributions in both cases are nearly identical and are right skewed with mode of 0.
- Public Records: The distribution looks nearly identical except for some outliers in the post-09 data. It's just one person with the exception. Checking his data, he seems bang average; averge Prosper Rating, average Prosper Score. However, he's history with Prosper and always pays on time and a high income range category with large Available Bank Card Credit and Revolving Credit Balance with less than 1 % on Bank Card Utilization. No data about his DebtToIncomeRatio, though. It seems like rules can be broken for some businessmen who showed the ability to pay on time over and over again.
- Revolving Credit: The mean is the same in both cases. However, the post-09 is slightly left skewed, showing bias toward borrowers with high Revoloving Credit Balance.
- Bank Card Utilization: Bank Card Utilization according to the available defenition: the percentage of available revolving credit that it is utilized at the time the credit profile was pulled. This value should be a minimum. And it seems they decided a cut-off value around 1%, above which the listing is subject to other variables deciding whether it would be accepted or not and surely will increase the Borrower Rate. We'll look further into it later.
- Debt-to-income ratio: The distributions look the same, with a peak around 0.25. There seems like a bias toward borrowers with high debt/income ratios where most of the borrowers have a ratio greater than 0.2.

###  Prosper Historical Data
- Principal Outstanding: On a log-scale the Principal Outstanding is slightly left skewed, showing bias toward borrowers with somehow high values, but not so much that it would damage their ability to pay their debts. The peak value is around 3K, but borrower with higher Principal Outstanding values count for a large portion of the distribution.
- ScoreX Change: The distribution is fairly normal, with a peak value around 0.

###  Borrower APR vs Credit Grade
- There is a general trend when Credit Grade increases, the median borrower APR decreases. However if we drew a line connecting Grade means, it will have a very gentle slope.
- Outliers break this general trend.
- For the lowest 3 grades (NC (No Credit), HR, E), the median rate is nearly identical.
- NC grade has broad distributions. HR and E grades have many peaks as well.
- D and C grades have wide variances.
- Difference between B and A grades is where their peaks lie. However, they can be matching for large portions of time.

###  Borrower APR vs Prosper Rating:
- The trend is much cleare now, proving that their new model is more refined.
- The general trend proves what's expected. As Prosper Rating increases, the median Borrower APR decreases. If we drew a slope connecting rating means, we would get a steep slope.
- However, there are outliers that kind of break the general trend.
- Although A ratings are 2nd best, they are more broadly distributed than AA.
- The distribution for HR is most peaked at 0.36 rate.
- E ratings have broad distributions and one of the peaks is equivalent to the mean of HR ratings.
- The variance in middle ratings (B, C, D) is great and shouldn't be underestimated. Outliers in B and C ratings tend to have higher rates.

###  Borrower APR vs Prosper Score and Average Credit Score:
- The negative correlation between Borrower APR and Average Credit Score is more subtle than it's between Borrower APR and Prosper Score

###  Prosper Rating vs Prosper Score and Average Credit Score:
- Connecting ratings' average Prosper Scores result in a strong positive correlation.
- Connecting each rating collective Average Credit Scores result in a moderately strong positive correlation.
- Prosper Ratings are more affected by Prosper Score than by Borrowers' Credit Scores.
- This shows that Prosper weighs in their own data more favorably over external sources.

###  Prosper Score vs (Delinquencies, Inquiries, and Public Records):
- It's clear that in order for the borrower's Prosper Score to increase by 1, the average number of inquiries and trades opened has to decrease except for the transition from a score of 10 to 11.
- Decreasing the number of Delinquencies in borrower's credit record helps especially for Prosper scores above 7. Then each increment in Prosper Score requires a significant decrease in number of Delinquencies.

###  Prosper Score vs (ScoreX Change and Available Bank Credit):
- There is a clear positive linear correlation between Credit Change and Prosper Score.
- On log-scale, it takes a significant change in Bank Credit to increas Prosper Score from 1 to 2. Prosper Scores beyond 2 exhibits a strong linear relationship between Prosper Scale and the log10 of Available Bank Card Credit.

###  Prosper Score vs (Stated Monthly Income and Debt-to-Income ratio):
- As expected, Prosper Score improves with decreasing Debt/Income and increasing Monthly Income to a lesser degree.

###  Borrower APR vs (Loan Amount & Recommendations):
- The general trend for Borrower APR is to decrease with increasing Loan Amount. However, there still exists a great variance in the Borrowe APR for the some Loan Amounts, especially for small Loans (<5k).
- Getting recommendations have no effect on Borrower APR.

###  Borrower APR over the years:
- During year 2008, Borrower APR hit the roof during company's 1st iteration. (Reasonable during the economic crisis)
- Borrower APR started to rise once again on 2nd quarter of 2011 until 4th quarter of 2012. Then eased off until it reached reasonable amount within the normal distribution. Maybe it's related to post-recession period.

###  Borrower APR vs Loan Status:
- Borrowe APR >=0.3 gets completed more often than not, but the possibility of a loan to get (charged-off, defaulted, or past-due) cannot be underestimated
## Key Insights for Presentation

##  Main Insights

###  pre-09 VS post-09
- Company's first iteration showed a moderate weak correlation between Credit Grade and Borrower APR. After applying the new model in the third quarter of 2009, Prosper Rating became a more refined metric for Borrower APR.

###  Borrower APR Controlling Factors
Borrower APR is strongly and negatively correlated with Prosper Rating. Increasing Prosper Rating, guarantees lower Borrower APR.
- The trend is much cleare now, proving that their new model is more refined.
- The general trend proves what's expected. As Prosper Rating increases, the median Borrower APR decreases. If we drew a slope connecting rating means, we would get a steep slope.
- However, there are outliers that kind of break the general trend.
- Although A ratings are 2nd best, they are more broadly distributed than AA.
- The distribution for HR is most peaked at 0.36 rate.
- E ratings have broad distributions and one of the peaks is equivalent to the mean of HR ratings.
- The variance in middle ratings (B, C, D) is great and shouldn't be underestimated. Outliers in B and C ratings tend to have higher rates.
- It's clear that having both low Credit Score and Prosper Score, charges the borrower with the highest rate.
- Having a high Credit Score and Prosper Score, guarantees the borrower the lowest rates.
- High Credit Score combined with low Prosper Score (<5) can still charge the borrower with high rates.
- On the other hand, having high Prosper Score but with low Credit Score, borrower is more likely to be charged with low rates. However, there are still exceptions.
- Most of borrowers with high debt-to-income ratio have below average Prosper Score with varying Credit Scores

###  Prosper Rating Contributing Elements:
- Prosper Rating affected by both Prosper Score and borrower Credit Score. However, it's shown that - Prosper Rating is more sensitive to changes in Prosper Score compared to borrower Credit Score. Proving that Prosper values its own data over external sources.
- Internal data, such as ScorexChangeAtTimeOfListing showed a positive correlation with Prosper Score.
- External data, such as InquiriesLast6Months, DelinquenciesLast6Months, BankcardUtilization showed negative correlaion with Prosper Score.
- Borrower debt-to-income ratio showed a negative correltion with Prosper Score.
- Borrower recommendations don't make any difference when it comes to APR

###  Effects of 2008 Recession on Borrower APR and following Recovery
- After facetting Borrower APR over the years, the 2008 global recession showed its mark. A high rate of 0.32 became more and more dominant through 2008. It too the company nearly 3 years to recover and lower its rates.

###  Borrower APR Variance with Prosper Rating for Each Employement Status Level
- As previously noticed, higher Prosper Ratings guarantee lower rates.
- There is a clear contrast between Employed borrowers and Not-employed ones. Being Employed can set one up for low rates. However, being Not-employed even with high Prosper Rating can't guarantee low rates.
- Working full-time does not differ from working part-time. The distributions look nearly identical.
- Self-employed and Other, have a lot of variance in their borroer rates.
- Retired is a weired one. The distribution looks almost uniform.
