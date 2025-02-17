# Table of Contents
1. [Introduction](#z_intro)
2. [When to use?](#applicability)

# Introduction<a name="z_intro"></a>
- a.k.a. Z-score = $\dfrac{X - \mu}{\sigma}$, $\mu \,,\, \sigma$ are population mean and variance respectively.
    - notice that this Z-score will follow a **standard** normal distribution if the observations($X$) themselves follow a normal distribution
- **for a sample**, Z-score for sample mean = $\dfrac{\bar{X} - \mu}{\sigma/\sqrt{n}}$
    - this is used to determine how far the sample mean is from the population mean.
    - the denominator has $\dfrac{\sigma}{\sqrt{n}}$ instead of $\sigma$ because $Var.(\bar{X}) = \dfrac{\sigma^2}{n}$. [Refer to this proof](../Maths/README.md/#sm)
    - Z-score for sample mean will follow a standard normal distribution even if the observations of the sample are not from a normal distribution.
        - this is because Central Limit Theorem makes it possible for large samples ($n > 30$) to have their sample mean follow a normal distribution, which makes the Z-score for sample mean follow a standard normal distribution. \
    $\bar{X} \sim \mathcal{N}\left(\mu, \dfrac{\sigma^2}{n}\right)$ (Note that for this case, although population mean and variance exist, that don't imply that the population is a normally distributed population)
        - but the observations of the sample (that form the sample mean as well) need to be **i.i.d.**.

# When to use?<a name="applicability"></a>
- infer population properties from a given, considerably large sample
- comparing population means/variances of 2 different samples
