Deworming Survey RCT
================
Georgianna James
2022-03-02

### Required Packages

``` r
library(survey)
library(tidyverse)
library(stargazer)
library(knitr)
```

# Replicating an RCT

## Treatment Effect Estimation

    ## 
    ## Effects of Deworming Treatment (over 12 months, reported in 2017 USD)
    ## ======================================================================================
    ##                                           Dependent variable:                         
    ##                   --------------------------------------------------------------------
    ##                   Total Individual Earnings Total Consumption Total Household Earnings
    ##                              (1)                   (2)                  (3)           
    ## --------------------------------------------------------------------------------------
    ## Treatment                  63.956                213.839              160.954         
    ##                           (67.550)              (151.675)            (109.598)        
    ##                                                                                       
    ## Control Mean            1,218.199***          2,156.463***          1,296.352***      
    ##                           (54.252)              (98.964)              (82.899)        
    ##                                                                                       
    ## --------------------------------------------------------------------------------------
    ## Observations               13,624                 4,794                4,074          
    ## Log Likelihood          -127,583.200           -45,195.260          -37,753.420       
    ## Akaike Inf. Crit.        255,170.500           90,394.510            75,510.840       
    ## ======================================================================================
    ## Note:                                                      *p<0.1; **p<0.05; ***p<0.01

## Interpretation

The coefficients on the estimates are 213.8 (USD) for total consumption
per capita, 63.96 (USD) for total earnings, and 161.0 (USD) for total
household earnings. This coeficients represent the average treatment
effect. The treatment group consumed 213.8 more USD per capita than the
control; the treatment group earned 63.96 more USD than the control, and
earned 161.0 more USD per household than control.

## T-test

    ## 
    ##  Design-based t-test
    ## 
    ## data:  tot_cnsp_t ~ treatment
    ## t = 1.4098, df = 71, p-value = 0.163
    ## alternative hypothesis: true difference in mean is not equal to 0
    ## 95 percent confidence interval:
    ##  -88.59322 516.27068
    ## sample estimates:
    ## difference in mean 
    ##           213.8387

The 95% confidence interval is -88.59 to 516.27. We cannot say the
treatment effect is signigicantly different than zero at a 95% level of
confidence because the p-value 0.163 is greater than alpha of 0.05.

## Male versus Female

    ## 
    ## Effects of Deworming Treatment on Individual Earnings for Females (over 12 months, reported in 2017 USD)
    ## =============================================
    ##                       Dependent variable:    
    ##                   ---------------------------
    ##                    Total Individual Earnings 
    ## ---------------------------------------------
    ## Treatment                   15.208           
    ##                            (46.906)          
    ##                                              
    ## Control Mean              673.553***         
    ##                            (30.683)          
    ##                                              
    ## ---------------------------------------------
    ## Observations                 6,826           
    ## Log Likelihood            -61,043.290        
    ## Akaike Inf. Crit.         122,090.600        
    ## =============================================
    ## Note:             *p<0.1; **p<0.05; ***p<0.01

    ## 
    ## Effects of Deworming Treatment on Individual Earnings for Males (over 12 months, reported in 2017 USD)
    ## =============================================
    ##                       Dependent variable:    
    ##                   ---------------------------
    ##                    Total Individual Earnings 
    ## ---------------------------------------------
    ## Treatment                   107.888          
    ##                            (119.810)         
    ##                                              
    ## Control Mean             1,727.759***        
    ##                            (103.700)         
    ##                                              
    ## ---------------------------------------------
    ## Observations                 6,798           
    ## Log Likelihood            -64,881.570        
    ## Akaike Inf. Crit.         129,767.100        
    ## =============================================
    ## Note:             *p<0.1; **p<0.05; ***p<0.01

The males in the treatmeant group experienced a 6% increase in
individual earnings, while the females in the treatmeant group
experienced a 2% increase in individual earnings. Furthermore, the males
in the conntrol group had a mean earnings that was nearly triple that of
the females in the control group. Similarly the percent increase for
females is about a third of the males. In summary, the males in this
sample earn nearly triple that of the female earnings, and benefit more
from the treatment, with average increase in income of 6% compared to 2%
for females.

# Attrition Analysis

    ## 
    ## Attrition Results
    ## =============================================
    ##                       Dependent variable:    
    ##                   ---------------------------
    ##                            Treatment         
    ## ---------------------------------------------
    ## Treatment                    0.013           
    ##                             (0.026)          
    ##                                              
    ## Control Mean               0.872***          
    ##                             (0.024)          
    ##                                              
    ## ---------------------------------------------
    ## Observations                 4,821           
    ## Log Likelihood            -2,255.600         
    ## Akaike Inf. Crit.          4,515.201         
    ## =============================================
    ## Note:             *p<0.1; **p<0.05; ***p<0.01

## Discussion

When you run a regression on whether a person was tracked down based on
their treatment status, you are investifating whether or not treatment
status had an effect on whether or not an individual was tracked down.
Within this regression table the control mean refers to the percentage
of those in the control group who were found for the fourth round of
interview, while the treatment coefficient refers to the different
between the percentage of treatment individuals found and control
individuals found. The coefficient here is positive, suggesting that it
might have been a little bit easier to track down those in the treatment
group, however, the SE and p value are so large that there is no
certainity that this difference is statistically significant from zero.

## T-test

    ## 
    ##  Design-based t-test
    ## 
    ## data:  found ~ treatment
    ## t = 0.5076, df = 71, p-value = 0.6133
    ## alternative hypothesis: true difference in mean is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.03870211  0.06513646
    ## sample estimates:
    ## difference in mean 
    ##         0.01321718

When you run a t-test on this design, you find that p value for the
estimate of the treatment effect is 0.6133, which indicates that there
is a 61% possibility that the 0.013 treatment is due to chance, so you
cannot reject the null hypothesis that this estimate is statistically
different than zero (that the results for the treatment are
statistically different than for the contro group), suggesting that
there is no differential attrition. However, failing to reject the null
does not mean you accept it. Therefore, you cannot tell from this sample
whether or not there is differential attrition, although more likely
that not there is no differential attrition.
