# Statistical Distributions

Below are some commonly used statistical distributions, along with their key properties and use cases.

---

## 1. **Uniform Distribution**
   - **Notation**: \( X \sim U(a, b) \)
   - **Parameters**:
     - Lower bound (\( a \)).
     - Upper bound (\( b \)).
   - **Probability Density Function (PDF)**:
     \[
     f(x) = \frac{1}{b-a} \quad \text{for } a \leq x \leq b
     \]
   - **Use Cases**:
     - Modeling events with equal probability over an interval.
     - Random number generation.

---

## 2. **Normal Distribution (Gaussian Distribution)**
   - **Notation**: \( X \sim N(\mu, \sigma^2) \)
   - **Parameters**:
     - Mean (\( \mu \)): Center of the distribution.
     - Variance (\( \sigma^2 \)): Spread of the distribution.
   - **Probability Density Function (PDF)**:
     \[
     f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
     \]
   - **Use Cases**:
     - Modeling natural phenomena (e.g., heights, weights).
     - Central Limit Theorem applications.

---

## 3. **Log-Normal Distribution**
   - **Notation**: \( X \sim LogNormal(\mu, \sigma^2) \)
   - **Parameters**:
     - Mean (\( \mu \)) of the logarithm of the variable.
     - Variance (\( \sigma^2 \)) of the logarithm of the variable.
   - **Probability Density Function (PDF)**:
     \[
     f(x) = \frac{1}{x\sigma\sqrt{2\pi}} e^{-\frac{(\ln x - \mu)^2}{2\sigma^2}} \quad \text{for } x > 0
     \]
   - **Use Cases**:
     - Modeling variables that are multiplicative products of many independent factors (e.g., stock prices).
     - Positive-skewed data.

---

## 4. **Exponential Distribution**
   - **Notation**: \( X \sim Exp(\lambda) \)
   - **Parameters**:
     - Rate (\( \lambda \)): Inverse of the mean.
   - **Probability Density Function (PDF)**:
     \[
     f(x) = \lambda e^{-\lambda x} \quad \text{for } x \geq 0
     \]
   - **Use Cases**:
     - Modeling time between events in a Poisson process.
     - Reliability analysis (e.g., failure times).

---

## 5. **Poisson Distribution**
   - **Notation**: \( X \sim Poisson(\lambda) \)
   - **Parameters**:
     - Rate (\( \lambda \)): Average number of events in an interval.
   - **Probability Mass Function (PMF)**:
     \[
     P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}
     \]
   - **Use Cases**:
     - Modeling the number of events in a fixed interval (e.g., arrivals, calls).
     - Rare event modeling.

---