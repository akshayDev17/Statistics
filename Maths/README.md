# Table of Contents
1. [Central Limit Theorem](#clt)
2. [Slutsky's Theorem](#st)
3. [Gamma Function](#gf)
4. [Fubini's Theorem](#fubini)
5. [Moment Generating Function (MGF)](#mgf)
    1. [Moments](#moments_def)
    2. [Deriving MGF using moments](#mgf_derivation)
6. [Normal distribution](#normal)
    1. [Formula for Probability density function](#normal_pdf)
    2. [Reason for Existence](#reason)
    3. [Area under the curve](#normal_auc)
    4. [MGF for normal distribution](#normal_pdf_mgf)
    5. [Closure under linear combinations](#additive_closure)
    6. [Sample Mean](#sm)
    7. [Sample Variance](#sv)
        1. [Bessel's Correction](#besscorr)


# Central Limit Theorem<a name="clt"></a>
- this also implies that datasets with $n_{samples} > 30$ can freely use Z-test<font color="red">How?</font>

# Slutsky's Theorem<a name="st"></a>
- 

# Gamma Function<a name="gf"></a>
- $\Gamma(z) = \int\limits_{0}^{\infty} t^{(z-1)} e^{-t}dt$
- **Identity**: $\Gamma(z+1) = z.\Gamma(z) \, \forall \, Re.(z) > 0$ (real part of the complex number z)
$$
\Gamma(z+1) = \int\limits_{0}^{\infty} t^{(z)} e^{-t}dt \\
\textrm{using integration by parts:}\\ 
t^{(z)} \int\limits_{0}^{\infty} e^{-t}dt -  \int\limits_{0}^{\infty} \dfrac{\partial t^{(z)}}{\partial t} \left(\int e^{-t}dt\right) dt = -t^{(z)}e^{-t} |_{0}^{\infty} -  \int\limits_{0}^{\infty} z t^{(z-1)}(-e^{-t})dt = \left[\dfrac{t^z}{e^t} \right]_{\infty}^{0} + z\int\limits_{0}^{\infty}  t^{(z-1)}(e^{-t})dt = z.\Gamma(z) + \left[\dfrac{t^z}{e^t} \right]_{\infty}^{0}\\
lt._{t\rightarrow 0} \left(\dfrac{t^z}{e^t}\right) = lt._{t\rightarrow 0} \left(e^{zln(t) - t}\right) = e^{-\infty} (\textrm{ if Re(z) > 0}) = 0 \\
lt._{t\rightarrow \infty} \left(\dfrac{t^z}{e^t}\right) = lt._{t\rightarrow \infty} \left(e^{zln(t) - t}\right) \rightarrow \textrm{ since log function is slower at convergence than linear, the exponent will become negative infinity} \\
\therefore \, , \, lt._{t\rightarrow \infty} \left(\dfrac{t^z}{e^t}\right) = 0 \\
\mathbf{\Gamma(z+1) = z.\Gamma(z)} \textrm{ provided } \mathbf{Re.(z) > 0}
$$

# Fubini's Theorem<a name="fubini"></a>
- 

# Moment Generating Function (MGF)<a name="mgf"></a>
- MGF = $M_X(t)$
- $M_X(t=0) = M_X(0) = 1$

## Moments <a name="moments_def"></a>
- first moment: $E[X]$, second moment: $E[X^2]$, third moment: $E[X^3]$ ....
- first-derivative of MGF at $t = 0 \Rightarrow$ first moment, second-derivative of MGF at $ t= 0 \Rightarrow$ second moment ,third-derivative of MGF at $t = 0 \Rightarrow$ third moment...

## Deriving MGF using moments<a name="mgf_derivation"></a>
- Taylor series: $f(x) = f(a) + \dfrac{f'(a)}{1!}(x-a) + \dfrac{f''(a)}{2!}(x-a)^2  + \dfrac{f''(a)}{3!}(x-a)^3  \cdots$
- using Maclaurin series (Taylor series for x=0, here t=0):
    - $M_X(t) = M_X(0) + \dfrac{M_X'(0)}{1!}t + \dfrac{M_X''(0)}{2!}t^2 + \dfrac{M_X'''(0)}{3!}t^3 \cdots = 1 + \dfrac{E[X]}{1!}t + \dfrac{E[X^2]}{2!}t^2 + \dfrac{E[X^3]}{3!}t^3 \cdots = \sum\limits_{n=1}^{\infty} \left( \dfrac{E[X^n]}{n!}t^n \right)$
    - $E[X^n] = \int\limits_{-\infty}^{\infty}X^n f_X(x) dx \textrm{ where } f_X(x) \textrm{ is the probability density function of random variable X, } \, \therefore \, , \, M_X(t) = \sum\limits_{n=1}^{\infty} \left( \dfrac{t^n}{n!}\int\limits_{-\infty}^{\infty}X^n f_X(x) dx \right)$
    - interchange the summation and integral using [Fubini's Theorem](#fubini)
        - $M_X(t) =  \int\limits_{-\infty}^{\infty}\left(\sum\limits_{n=1}^{\infty} \dfrac{t^n}{n!} X^n f_X(x) \right) dx  = \int\limits_{-\infty}^{\infty}\left(\sum\limits_{n=1}^{\infty} \dfrac{t^n}{n!} X^n\right) f_X(x)  dx = \int\limits_{-\infty}^{\infty}\left(\sum\limits_{n=1}^{\infty} \dfrac{(Xt)^n}{n!} \right) f_X(x)  dx$

    - observe the Maclaurin series for $f(x) = e^x$ : $e^x = 1 + \dfrac{1}{1!}x + \dfrac{1}{2!}x^2 + \dfrac{1}{3!}x^3 + \cdots = \sum\limits_{n=0}^\infty \dfrac{x^n}{n!}$
    - $M_X(t) =\int\limits_{-\infty}^{\infty} e^{tX} f_X(x)  dx = E\left[e^{tX}\right]$
- Therefore, MGF $\mathbf{M_X(t) = E\left[e^{tX}\right]}$

# Normal distribution<a name="normal"></a>

## Formula for Probability density function<a name="normal_pdf"></a>
- PDF(x) = $\dfrac{1}{\sigma\sqrt{2\pi}}e^{-\dfrac{(x-\mu)^2}{2\sigma^2}}$
- x: R.V., $\mu \,,\, \sigma$: mean and standard deviation of this R.V.

## Reason for Existence<a name="reason"></a>

## Area under the curve<a name="normal_auc"></a>
- I = $\int\limits_{-\infty}^{\infty} \dfrac{e^{\frac{-\left(X - \mu\right)^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} dX$
- assume two i.i.d.'s, $I_X = \int\limits_{-\infty}^{\infty} \dfrac{e^{\frac{-\left(X - \mu\right)^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} dX\,,\, I_Y = \int\limits_{-\infty}^{\infty} \dfrac{e^{\frac{-\left(Y - \mu\right)^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} dY$
- $I_XI_Y = \int\limits_{-\infty}^{\infty}\int\limits_{-\infty}^{\infty} \dfrac{e^{\frac{-\left(X - \mu\right)^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} \dfrac{e^{\frac{-\left(Y - \mu\right)^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} dX dY = \int\limits_{-\infty}^{\infty}\int\limits_{-\infty}^{\infty} \dfrac{e^{\frac{-\left(\left(X - \mu\right)^2 + \left(Y - \mu\right)^2\right)}{2\sigma^2}}}{2\pi\sigma^2} dX dY$
- use the transformation $x = rcos\theta  \,,\, y = rsin\theta  \rightarrow dx.dy = rdr d\theta \,,\, \rightarrow r^2 = x^2 + y^2 \,,\, x = X - \mu\,,\,y = Y - \mu$
- $I^2 = \frac{1}{2\pi\sigma^2}\int\limits_{0}^{\infty}\int\limits_{0}^{2\pi} re^{\dfrac{-r^2}{2\sigma^2}} dr d\theta$
    - let $u = r^2 \rightarrow du = 2rdr$
    - $I^2 = \frac{1}{2\pi\sigma^2} \int\limits_{0}^{\infty}\int\limits_{0}^{2\pi} e^{\dfrac{-u}{2\sigma^2}} \frac{1}{2}du d\theta = \frac{1}{4\pi\sigma^2} \int\limits_{0}^{\infty} e^{\dfrac{-u}{2\sigma^2}}.2\pi du = \frac{1}{2\sigma^2}\times (-{2\sigma^2}).\int\limits_{0}^{-\infty} e^B dB = -1 \times \left[e^B\right]_{0}^{-\infty} = -1 (0-1) = 1$
    - $I^2 = 1 \Rightarrow I = 1$
- hence, this is a P.D.F. , i.e. area under the curve is 1.
- notice that if the normalising constant term $\dfrac{1}{\sigma\sqrt{2\pi}}$ is removed, the square of the area under the curve would've been $2\pi\sigma^2$

## MGF<a name="normal_pdf_mgf"></a>
- for $X \sim \mathcal{N}(\mu, \sigma^2) \,,\, M_X(t) = E\left[e^{tX}\right] = \int\limits_{-\infty}^{\infty} e^{tX} \dfrac{1}{\sigma\sqrt{2\pi}}e^{-\dfrac{(X-\mu)^2}{2\sigma^2}} dX$
- lets focus on the exponent first:
    - $tX - \dfrac{(X-\mu)^2}{2\sigma^2}$
    - lets group this using $(X - \mu)$
    - $ = t(X-\mu) - \dfrac{(X-\mu)^2}{2\sigma^2} + t\mu = t\mu + (X-\mu)\left(t - \dfrac{(X-\mu)}{2\sigma^2}\right) = t\mu + \frac{1}{2\sigma^2}\left((2\sigma^2t)(X - \mu) - (X - \mu)^2\right) = t\mu - \frac{1}{2\sigma^2}\left( (X - \mu)^2 - (2)(\sigma^2t)(X - \mu)\right)$
    - assuming $X-\mu = a, \sigma^2t = b$, we have above $a^2 - 2ab$, which can be changed to $(a-b)^2  - b^2$
    - $t\mu - \frac{1}{2\sigma^2}\left( (X - \mu - 2\sigma^2t)^2 - (\sigma^4t^2)\right) = t\mu + \frac{(\sigma.t)^2}{2} - \dfrac{(X - \mu - 2\sigma^2t)^2}{2\sigma^2}$
    - first two terms are independent of $X$, they'll be treated as constants, so lets focus further on the expression containing $X \rightarrow - \dfrac{(X - \mu - 2\sigma^2t)^2}{2\sigma^2}$
    - let $y = X - \mu - 2\sigma^2t \Rightarrow dy = dx$ , the above exponent integral becomes $\int\limits_{-\infty}^{\infty} e^{- \dfrac{(X - \mu - 2\sigma^2t)^2}{2\sigma^2}} dX = \int\limits_{-\infty}^{\infty} e^{- \dfrac{y^2}{2\sigma^2}} dy = \sqrt{2\pi}\sigma$
- hence, $M_X(t) = \dfrac{1}{\sigma\sqrt{2\pi}} . e^{\left(t\mu + \frac{(\sigma.t)^2}{2}\right)}.\sqrt{2\pi}\sigma = e^{\left(t\mu + \frac{(\sigma.t)^2}{2}\right)}$
- Therefore, for a normally distributed random variable X, its moment generating function is $\mathbf{M_X(t) = e^{\left(\large t\mu + \frac{(\sigma.t)^2}{2}\right)}}$

## Closure under linear combinations<a name="additive_closure"></a>
- consider n i.i.d. samples drawn from $\mathcal{N}(\mu, \sigma^2)$: $X_1, X_2, \cdots X_n$
    - MGF $M_{X_i}(t) = E\left[e^{tX_i}\right] = \int\limits_{-\infty}^{\infty} e^{tX_i} \frac{1}{\sigma\sqrt{2\pi}} e^{-\dfrac{(X_i - \mu)^2}{2\sigma^2}} dX_i$
- defining R.V. Y , $Y = \sum\limits_{i=1}^n a_i X_i$ 
- **to prove: Y is also normally distributed** 
    - how to? prove that the MGF of Y is same as that of the MGF of a normally distributed random variable.
- $M_Y(t) = E\left[e^{tY}\right] = E\left[e^{\sum \limits_{i=1}^n a_iX_i t}\right]$ (additive property of expected values of any given random variables, regardless of identical/non-identical distribution, and regardless of dependence)
    - $= E\left[\prod \limits_{i=1}^n e^{a_iX_i t}\right] = \prod \limits_{i=1}^n E\left[e^{a_iX_i t}\right]$ because expectation of product of two *independent R.V.s* is the product of their individual expectations.
    - since each $X_i$ is scaled by $a_i$, its respective distribution now becomes $\sim \mathcal{N}(a_i\mu, a_i^2\sigma^2)$
    - $M_Y(t) = \prod \limits_{i=1}^n e^{\left(\large t\mu + \frac{(\sigma.t)^2}{2}\right)} = e^{\left(\large nt\mu + n.\frac{(\sigma.t)^2}{2}\right)} = e^{\left(\large t.(n\mu) + \frac{(\sqrt{n}\sigma.t)^2}{2}\right)} = \mathcal{N}(n\mu, \sqrt{n}\sigma)$
    - Therefore, $M_Y(t)$ is proved to be the MGF of a normally distributed R.V.


## Sample vs Population<a name="sample_vs_population"></a>
- sample-set: set of numbers drawn using this PDF
- these samples that make up the sample set are said to be **i.i.d**, i.e. independent and identically distributed, as they are independent from each other and drawn from the same distribution.
    - Mathematically: $X_1, X_2, \cdots X_n \sim  \mathcal{N}(\mu, \sigma^2)$
    - why independent? this is by definition.
    - independent sampling strategy typically implies sampling with replacement
    - it also means that sampling a particular value gives no additional information of sampling some other value in the future sampling trials
        - for instance, imaging throwing a dart at a dartboard, given an infinite pool of identically behaving darts.
        - no dart throw will affect how the next dart will land on the board.
        - hence the throws are independent.
        - if instead the dartboard were to change its orientation depending upon what the previous throws were, this would naturally influence the value of the current throw (say whereever the previous throw was, the board now centers around it), hence introducing *dependence* of previous throw on the current throw.
        - if instead the previously thrown darts were to *slightly nudge* the position of the dart to be thrown, this would constitute *dependence* of current throw on previous throws.
        - this time-wise/time-based dependence is usually seen in time-series data.
    - sampling from such a normal distribution corresponds to sampling from an infinite population size with replacement.

### Sample-population identities
- $\mathbf{\sum\limits_{i=1}^n (x_i - \bar{x})^2 = \sum\limits_{i=1}^n (x_i - \mu)^2 - n(\bar{x} - \mu)^2}$ <a name="sp_id_1"></a>
    - $x_i - \bar{x} = x_i - \mu + \mu - \bar{x} = (x_i - \mu) -(\bar{x} - \mu)$
    - $(x_i - \bar{x})^2 = (x_i - \mu)^2 +(\bar{x} - \mu)^2 - 2(x_i - \mu)(\bar{x} - \mu)$
    - taking summation: $\sum\limits_{i=1}^n (x_i - \bar{x})^2 = \sum\limits_{i=1}^n (x_i - \mu)^2 + \sum\limits_{i=1}^n(\bar{x} - \mu)^2 - 2(\bar{x} - \mu)\sum\limits_{i=1}^n(x_i - \mu) = \sum\limits_{i=1}^n (x_i - \mu)^2 + n.(\bar{x} - \mu)^2 - 2(\bar{x} - \mu).n.(\bar{x} - \mu) = \sum\limits_{i=1}^n (x_i - \mu)^2 - n.(\bar{x} - \mu)^2$

## Sample Mean<a name="sm"></a>
- mean of this i.i.d. sample (set) is normally distributed. Steps to prove:
    - express mean as a weighted sum, i.e. linear combination of these i.i.d.
    - linear combination of these i.i.d. is normally distributed due to closure
    - **notice** for sample mean estimation (knowing what the sample mean is), there's no constraints on the relation between the n i.i.d.'s
        - but when a particular sample mean value is chosen to summarize that sample, that fixes one of the n samples.
        - imagine this as having a box of cookies with 3 cookies, and knowing that the total no. of chocolate chips across all cookies in that box is 30
            - average no. of chocolate chips per cookie = 10
            - this leaves us with the possibilities that there can be any no. of chocolate chips on the first and second drawn cookie, but once we know them (i.e. once those cookies are drawn, i.e. taken out of the box), the no. of chocolate chips on the third cookie becomes automatically known, i.e. no freedom of choice/assumption there.
            - these first two draw cookies are the first n-1 R.V.s drawn. once drawn, their values are known, and when the sample mean (average no. of chocolate chips per cookie) is also known, it fixes the third cookie's no. of chocolate chips, i.e. value of $X_n$
        - the sample mean is a **pure arithmetic mean**, hence it will be constraintless, regardless of any other constraints imposed on the sample.
            - for instance, say a condition is known that the product of the no. of cholocolate chips across all cookies is 100
            - this doesn't set any constraints on the sample mean, i.e. average no. of , in terms of how many cookies will decide this value. All 3 cookies will still be free to have whatever values they can, still obeying this product condition
            - but if the sample variance is to be estimated under this new condition + a definite knowledge of sample mean, now 2 degrees of freedom are lost. hence the denominator (Bessel's correction term) will now be $n-2$.
- **Identity** : $\mathbf{E[\bar{X}] = \mu}$
    - $E[\bar{X}] = E\left[\dfrac{\sum\limits_{i=1}^n X_i}{n} \right] = \frac{1}{n} E\left[\sum\limits_{i=1}^n X_i\right] = \frac{1}{n} \sum\limits_{i=1}^n E[X_i] = \frac{1}{n}.n.\mu = \mu $
- **Identity: variance of sample mean in terms of population mean**
    - for any function $g(x)$ , $Var.(g(x)) = E\left[(g(x) - E[g(x)])^2 \right]$
    - hence, for $g(x) = \bar{x}$, $Var.(\bar{x}) = E\left[(\bar{x} - E[\bar{x}])^2 \right] = E\left[(\bar{x} - \mu)^2 \right]$ \
        $Var.(\bar{x}) =  E\left[(\bar{x} - \mu)^2 \right]$
- **Identity**: $\mathbf{Var.(\bar{X}) = \dfrac{\sigma^2}{n}}$
    - also, $Var.(\bar{X}) = Var.\left(\dfrac{\sum\limits_{i=1}^n X_i}{n} \right) = \frac{1}{n^2} Var.\left(\sum\limits_{i=1}^n X_i \right) = \frac{1}{n^2}\left( \left(\sum\limits_{i=1}^n Var.(X_i) \right) + \sum\limits_{i=1}^n\sum\limits_{j=1}^n 2.Cov.(X_i, X_j) \right)$
        - since all $X_i$ are i.i.d., which includes independence, pairwise covariance = 0
        - hence $Var.(\bar{X}) = \frac{1}{n^2}\left( \sum\limits_{i=1}^n Var.(X_i) \right) = \frac{1}{n^2}.n.\sigma^2 = \dfrac{\sigma^2}{n}$ \
        $\therefore \,,\, Var.(\bar{X}) = \dfrac{\sigma^2}{n}$
## Sample Variance<a name="sv"></a>

### Bessel's Correction: Sample Variance expressed in terms of Population variance<a name="besscorr"></a>
- sample variance $S^2$ : $S^2 = \frac{1}{n-1} \sum\limits_{i=1}^n (X_i - \bar{X})^2$
- ideally, the denominator should've been $n$, as variance is defined as the expected squared-deviation from mean.
- the following happens if this naive definition of sample variance is used:
    - $s^2_{naive} = \dfrac{\sum\limits_{i=1}^n (x_i - \bar{x})^2}{n} $
    - using [this sample population identity](#sp_id_1) : $s^2_{naive} = \frac{1}{n}\left(\sum\limits_{i=1}^n (x_i - \mu)^2 - n.(\bar{x} - \mu)^2\right)$
    - $\Rightarrow E\left[s^2_{naive}\right] = E\left[\frac{1}{n}\left(\sum\limits_{i=1}^n (x_i - \mu)^2 - n.(\bar{x} - \mu)^2\right)\right] = \frac{1}{n}\left(E\left[\sum\limits_{i=1}^n (x_i - \mu)^2 \right] - E\left[n.(\bar{x} - \mu)^2\right]\right) =  \frac{1}{n}\left(\sum\limits_{i=1}^n E\left[(x_i - \mu)^2 \right] - n.E\left[(\bar{x} - \mu)^2\right]\right)$
        - $E\left[(x_i - \mu)^2 \right]$ is basically the population variance formula for a given sample $x_i$ , hence will be equal to the population variance value $\sigma^2$. \
        Hence the left term evaluates to $n\sigma^2$ (n-times the same value, population variance, is being summed)
        - we saw that $E\left[(\bar{x} - \mu)^2\right]$ was nothing but the variance of $\bar{X}$ (sample mean) when related with the population mean
            - and when expressed in terms of the population variance, this expression was $\dfrac{\sigma^2}{n}$
            - hence the 2nd term is $\dfrac{\sigma^2}{n}$
    - $E\left[s^2_{naive}\right] = \frac{1}{n}\left(n\sigma^2 - n.\dfrac{\sigma^2}{n} \right)= \frac{1}{n}\left(n\sigma^2 - \sigma^2 \right) = \dfrac{n-1}{n}\sigma^2 \Rightarrow \sigma^2 = \dfrac{n}{n-1} E\left[s^2_{naive}\right] = E\left[\dfrac{n}{n-1}s^2_{naive}\right] = E\left[\dfrac{n}{n-1}\dfrac{\sum\limits_{i=1}^n (x_i - \bar{x})^2}{n}\right] = E\left[\dfrac{\sum\limits_{i=1}^n (x_i - \bar{x})^2}{n-1}\right]$ \
    $\therefore \,,\, \sigma^2 = E\left[\dfrac{\sum\limits_{i=1}^n (x_i - \bar{x})^2}{n-1}\right]$
- hence, to keep the simple relations of **expected value of sample mean = population mean** and **expected value of sample variance is population variance**, the sample variance is defined as:\
$S^2 = \frac{1}{n-1} \sum\limits_{i=1}^n (X_i - \bar{X})^2$

### Intuitive explanation of this correction term
- initially the sample has $n$ DOF (degrees of freedom)
- once a sample mean is chosen, that constraints the last drawn sample, so that these samples drawn have a sample mean equal to the fixed sample mean.
- since the sample variance is a function of both $X_i$'s and $\bar{X}$, and for a fixed sample $\bar{X}$ is also fixed, this only allows the first n-1 drawn samples, i.e. $X_1, X_2, \cdots X_{n-1}$ to be chosen freely
    - hence instead of using $n$ in the denominator, $n-1$ is used.

### Other scenarios w.r.t. DOF
- if say, in addition to $\bar{X}$ we had a condition on the product of observations across this sample
    - $\prod \limits_{i=1}^n X_i = 1000$
    - this **will not affect sample mean computation** in terms of degrees of freedom as it doesn't depend on that. 
    - now that we have this condition and $\bar{X}$, computing variance will now only have $n-2$ degrees of freedom\
    hence, $S^2 = \dfrac{1}{n-2} (X_i - \bar{X})^2$

### Sample Variance of n i.i.d. observations has chi-squared distribution<a name="sv_normal_iid_chisquared"></a>
