# Do changes bring difference: A comparative study of Manchester United’s performance after sacking Jose Mourinho



## Introduction

Jose Mourinho, the controversial “special one” was sacked by Manchester United by December 18, 2018 ([BBC](https://www.bbc.com/sport/football/46603018)). The Portuguese manager joined the England Premier League solikccer club in May 2016, and took the charge for more than 2 years. Jose is broadly recognized as one of the greatest all-time soccer managers ([ESPN, 2013](https://web.archive.org/web/20131023073918/http://espnfc.com/news/story/_/id/1514848/)).



### Purpose
Our goal in this study is to quantitatively evaluate the effectiveness of Manchester United sacking Jose Mourinho. In other word, whether or not such a decision significantly improves the United’ performance in Premier League. The goal difference in each match will be investigated as a simplified process of the ELO system (Hvattum & Arntzen, 2009).



### Dataset
We procecced with the [Premier League results dataset](https://www.football-data.co.uk/englandm.php). After wrangling in the **Preliminary Results** section, our dataset record Manchester United’ goal differences in 76 matches over season 2016/17 and 2017/18 coached by Jose Mourinho in `old_coach`, and 76 matches in season 19/20 and 20/21 coached by Ole Gunnar Solskjær in `new_coach`, who replaced Jose’s position in December, 2018. 

```r
null_distribution <- 
    league_results %>%
    specify(formula = goal_diff ~ coach) %>%
    hypothesize(null = 'independence') %>%
    generate(reps = 1000, type = 'permute') %>%
    calculate(stat = 'diff in means', order = c('new', 'old'))

visualize(null_distribution) + shade_p_value(obs_diff_mean, direction='right')
get_p_value(null_distribution, obs_diff_mean, direction='right')
```



