# Central Limit Theorem
- this also implies that datasets with $n_{samples} > 30$ can freely use Z-test<font color="red">How?</font>

# Slutsky's Theorem
- 

# Gamma Function
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

# Normal distribution

## Formula for Probability density function
- PDF(x) = $\dfrac{1}{\sigma\sqrt{2\pi}}e^{-\dfrac{(x-\mu)^2}{2\sigma^2}}$
- x: R.V., $\mu \,,\, \sigma$: mean and standard deviation of this R.V.

## Reason for Existence

## Sample vs Population
- sample-set: set of numbers drawn using this PDF
- these samples that make up the sample set are said to be **i.i.d**, i.e. independent and identically distributed, as they are independent from each other and drawn from the same distribution.
    - Mathematically: $X_1, X_2, \cdots X_n \sim  \mathcal{N}(\mu, \sigma^2)$