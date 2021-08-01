Our report is trustworthy because:
- We obtain results from the dataset, a random sample, that can generalize to the overall performance of United coached by two coaches, the population.
- We use simulation-based and theory-based inferential methods and tend to make precise estimates and draw solid conclusion by setting a low significance level. 

From the histogram and box-plot above, we can see that ...[TO-DO]. However, due to sampling variation, we are not ready reach a conclusion yet. Therefore, we plan to implement the following statistical methods to address the gap:
- We will use **bootstrap sampling** with reps = 1000 to measure standard error and calculate confidence intervals at a 5% significance level for the estimates under two coaches: mean and standard deviation of goal difference in each replication.
- We will do two **hypothesis tests** at a 5% significance level (denote $\mu_s$ as mean, $\sigma_s$ as standard deviation for Solskjær and $\mu_s$ as mean, $\sigma_s$ as standard deviation for Mourinho): 
    * On mean goal difference:
        * $H_0:\mu_s=\mu_m$​​ 
        * $H_A:\mu_s>\mu_m$​​ 
    * On standard deviation of goal difference:
        * $H_0:\sigma_s=\sigma_m$​​​ 
        * $H_A:\sigma_s<\sigma_m$​​​​ 
- We plan to approximate **confidence intervals based on Central Limit Theorem** for the mean goal difference, given that he sample size is sufficiently large (144 > 30), roughly taken independently and the mean is a sum of random terms. 

We expect to answer the question: whether replacing coach Mourinho with Solskjær significantly improves the United’s performance, based on whether to reject null hypothesis and construction of confidence intervals. These findings provide insights about the performance of each coach and shed light on future decision making, which will benefit the stakeholders of United. This study leads to future questions like: hypothesis testing on the win rate; take in more explanatory variables to measure performance.