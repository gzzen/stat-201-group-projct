# Do changes bring difference: A comparative study of Manchester United’s performance after sacking Jose Mourinho

> Todo
>
> - [ ] One more citation from academic paper
> - [ ] Complete the setup for sampling & bootstrapping

## Introduction

### Background

 Jose Mourinho, the controversial “special one” was sacked by Manchester United by December 18, 2018 ([BBC](https://www.bbc.com/sport/football/46603018)). The Portuguese manager joined the England Premier League solikccer club in May 2016, and took the charge for more than 2 years. 

Jose is awarded 4 times of the World’s Best Club Coach since 2003, where he unexpectedly brought FC Porto, the little-known Portuguese club to the position of the European Champoin League winner. In 2010, he coached the underrated Italian club Inter Milan and won two domestic champoinships and the European Champoin League in merely one season. His leadership in Chelsea, another England club carried the entire team to the top of Premier League for 3 times ([Transfermarkt](https://www.transfermarkt.us/jose-mourinho/erfolge/trainer/781)). For all his achievements, Jose Mourinho is broadly recognized as one of the greatest all-time soccer managers ([ESPN, 2013](https://web.archive.org/web/20131023073918/http://espnfc.com/news/story/_/id/1514848/)). 

However, Jose’s prestige uncontrollably fades out when rumours arises about his disputes between players, media or the high-levels in clubs. As the ex-manager of many giant clubs, Jose Mourinho was eventually sacked by Real Madrid ([BBC, 2013](https://www.bbc.com/sport/football/22583729)), Chelsea ([BBC, 2015](https://www.bbc.com/sport/football/34670192)) and Tottenham ([BBC, 2021](https://www.bbc.com/sport/football/56799400)) throughout his coaching path in addition to the United. Nevertheless, the Spurs’ world-class forward Harry Kane expressed his thankfulness to his ex-Boss ([Twitter @HKane](https://twitter.com/HKane/status/1384126605224648716?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1384126605224648716%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fwww.bbc.co.uk%2Fsport%2Ffootball%2F56799400)). 

<img src="intro.assets/Screen Shot 2021-07-30 at 3.30.28 PM.png" alt="Screen Shot 2021-07-30 at 3.30.28 PM" style="zoom:33%;" />

### Question & Methodology

Our propose in this study is to quantitatively evaluate the effectiveness of Manchester United sacking Jose Mourinho. In other word, whether or not such a decision significantly improves the United’ performance in Premier League. 

Our dataset recorded Manchester United’ goal differences in 76 matches over season 2016/17 and 2017/18 coached by Jose Mourinho, and 76 matches in season 19/20 and 20/21 coached by Ole Gunnar Solskjær, who replaced Jose’s position in December, 2018. 

The ELO system is widely adopted in modern soccer analysis, which depends on the goal difference, and add weights on multiple factors such as the current strength of the home team and away team (Hvattum & Arntzen, 2009). Due to limitations of methodologies, we will investigate only the goal difference in the ELO system. Goal difference is a random variable that quantifies the teams’ overall performance in one game, calculated via substracting the scorings by the losing points. 

For the purpose of comparison, we will setup a hypothesis test with significance level $\alpha=0.05$ using the means as the location parameter, and standard deviations as the scale parameter. Since we have no access to the entire population of matches, bootstrap with `rememebr to fill the reps` repititions will be impliemented to estimate to the true population mean and standard deviation of our statistics between two coaches. 

#### Location parameter: means

The location parameter determines the position of the center of the distribution, which evaluates the overall goal difference for each coach. The manager with higher mean must have higher averaged-out difference in goals. However, we still need to examine the significance in hypothesis testing. Assume $\mu_m$​ is the mean of goal difference for Manchester United under Jose Mourinho’s leadership, and $\mu_s$​​​​ represents the mean goal difference as Ole Gunnar Solskjær took his position. We want to study if the successor is doing a better job after Jose is fired, so we have the hypothesis setup as below:

- Null hypothesis $H_0:\mu_s=\mu_m$​​ 
- Alternative hypothesis $H_A:\mu_s>\mu_m$​​ 

#### Scale parameter: standard deviations

The scale parameter decides the spread-out of the distribution. In this study, this parameter evaluates the variation of goal difference. Generally, a manager is more preffered if the team has low standard deviation, which implies higher stability. However, a team that always lose could have low standard deviation as well. Therefore, the conclusion cannot be made directly without the data of mean goal difference. Again we want to compare the standard deviation of goal difference along matches between the original coach $\sigma_m$ and the new coach $\sigma_s$, so we have the setup as below:

- Null hypothesis $H_0:\sigma_s=\sigma_m$​​​ 
- Alternative hypothesis $H_A:\sigma_s<\sigma_m$​​​​ 

## Methods: Plan

Our report is trustworthy for two reasons:
- Although we do not perform a census, the dataset we select serves as a random sample that we take. The result we obtain from this dataset can generalize to the population, which means we can infer and compare the overall performance of the team supervised under these two coaches.
- We plan to use both simulation-based and theory-based inferential methods, explained in details below. In this way, we make this study more objective, comprehensive and reliable. Besides, we tend to make a more precise estimate and draw a more solid conclusion by setting the significance level as 5%. 

From the histogram and box-plot above, We can see that ...[TO-DO]. However, due to sampling variation, we are not ready reach a conclusion yet. Therefore, we plan to implement the following statistical methods to address the gap:

### Bootstrap sampling
We plan to use bootstrap sampling to carry out 1000 resamples (reps = 1000) with replacement from the dataset. We will measure the approximated sampling variation with standard error, and calculate confidence intervals at a 5% significance level to find plausible values for the estimates under two coaches: the mean goal difference ($/mu_s_hat$ for Solskjær, $/mu_m_hat$ for Mourinho) and standard deviation of goal difference ($/sigma_s_hat$ for Solskjær, $/sigma_m_hat$ for Mourinho) in each replication.

### Hypothesis testing
We plan to do hypothesis tests for two parameters under two categories. Denote $\mu_s$ as mean, $\sigma_s$ as standard deviation of goal difference for Solskjær and $\mu_m$ as mean, $\sigma_m$ as standard deviation of goal difference for Mourinho.

Hypothesis test on the mean of goal difference:
- Null hypothesis $H_0:\mu_s=\mu_m$​​ 
- Alternative hypothesis $H_A:\mu_s>\mu_m$​​ 

Hypothesis testing on the standard deviation of goal difference:
- Null hypothesis $H_0:\sigma_s=\sigma_m$​​​ 
- Alternative hypothesis $H_A:\sigma_s<\sigma_m$​​​​ 

Signifiant level for both tests: $\alpha=0.05$

### Confidence interval based on CLT 
To begin with, we want to justify that Central Limit Theorem is applicable for our dataset. First, the sample size we have for each coach 76 is larger than 30, thus sufficiently large to perform CLT. Second, the sample was roughly taken in an independent fashion. Third, the estimator mean of goal difference is a sum of random components, so the sampling distribution of mean converges to the Normal distribution. With this in mind, we are going to approximate confidence intervals for the mean goal difference based on CLT. 

We expect to answer the question we set: whether replacing the coach Jose Mourinho with Ole Gunnar Solskjær significantly improves the Manchester United’s performance, based on whether to reject the null hypothesis and construction of confidence intervals for point estimates of two parameters. These findings provide insights about the performance of each coach, whether sacking Mourinho is a good decision, and shed light on future decision making, which will be beneficial to the stakeholders of United, such as its managers, sponsors and fans. This study could lead to future questions like: whether we can do hypothesis testing on the win, lose, and draw rate; take in more explanatory variables in the ELO system to measure performance.

## References

BBC. (2018). *Jose MOURINHO: Manchester UNITED sack manager*. BBC Sport. https://www.bbc.com/sport/football/46603018. 

*José Mourinho - honours*. Transfermarkt. (n.d.). https://www.transfermarkt.us/jose-mourinho/erfolge/trainer/781. 

*Greatest managers, No. 9: Jose Mourinho*. ESPNFC. (2013). https://web.archive.org/web/20131023073918/http://espnfc.com/news/story/_/id/1514848/. 

BBC. (2013). *Jose MOURINHO: Real Madrid boss to leave next month*. BBC Sport. https://www.bbc.com/sport/football/22583729. 

BBC. (2015). *Jose MOURINHO: Chelsea Sack boss after Premier League slump*. BBC Sport. https://www.bbc.com/sport/football/34670192. 

BBC. (2021). *Jose MOURINHO: Tottenham sack manager after 17 months*. BBC Sport. https://www.bbc.com/sport/football/56799400. 

Hvattum, L. M., & Arntzen, H. (2009, November 19). *Using ELO ratings for match result prediction in association football*. International Journal of Forecasting. https://www.sciencedirect.com/science/article/pii/S0169207009001708. 