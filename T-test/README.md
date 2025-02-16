- for large sample sizes: p-values from t-test indentical to that from z-test.
- for $n_{samples} > 30$ **and not highly skewed data**, t-test can replace z-test.
- <font color="red">what are the 1-sample and 2-sample t-tests?</font>


# Assumptions
- $n_{samples} \le 30$
- **unknown population variance**
- **normally distributed data**
    - a more relaxed version of this requirement: **sample-mean normally distributed** + **sample variance** follows a $\chi^2$-distribution and is **independent of sample mean**
- **presence of outliers violates normality** , hences its advisable to not use T-tests in such scenarios. <font color="red">What??</font>

# T-statistic
- $T = \dfrac{\textrm{sample mean} - \mu_0}{\textrm{sample standard deviation}}$

## T-distribution (Student's T-distribution)
- 