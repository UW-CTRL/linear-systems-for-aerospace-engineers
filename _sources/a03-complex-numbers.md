# Complex Numbers
## Complex number basics
A complex number $ z $ belongs to the set of all complex numbers $ \mathbb{C} $, and is given by:

$$
z = a + ib, \quad a, b \in \mathbb{R}, \quad i = \sqrt{-1} \: \text{where} \:
\operatorname{Re}(z) = a, \quad \operatorname{Im}(z) = b.
$$

The complex number $ z = a + ib $ can be represented as a point in the complex plane. The following diagram illustrates $ z $ in the first quadrant, showing the real and imaginary components, as well as the modulus $ r $ and argument $ \theta $.

![](figs/complex_polar.png)


The complex number can be rewritten in terms of its modulus and argument:

$$
z = a + ib = r\cos\theta + i r\sin\theta = r (\cos\theta + i\sin\theta) = re^{i\theta}, \:\: \text{where} \:\:
r = \sqrt{a^2 + b^2}, \quad \theta = \tan^{-1} \left( \frac{b}{a} \right).
$$
This is the polar form of the complex number.

## Arithmetic of Complex Numbers

Let $z_1 = a_1 + i b_1, \quad z_2 = a_2 + i b_2, \:\: \text{where} \:\:a_1, a_2, b_1, b_2 \in \mathbb{R} $.

### Addition and Subtraction
Complex numbers are added and subtracted by combining their real and imaginary components separately:

$$
z_1 \pm z_2 = (a_1 \pm a_2) + i (b_1 \pm b_2).
$$

### Multiplication
Multiplication of two complex numbers follows the distributive property:

$$
z_1 z_2 = (a_1 + i b_1)(a_2 + i b_2).
$$

Expanding using the distributive property:

$$
z_1 z_2 = a_1 a_2 + i a_1 b_2 + i b_1 a_2 + i^2 b_1 b_2.
$$

Since $ i^2 = -1 $, we simplify:

$$
z_1 z_2 = (a_1 a_2 - b_1 b_2) + i (a_1 b_2 + b_1 a_2).
$$

### Division
To divide two complex numbers, we multiply the numerator and denominator by the conjugate of the denominator:

$$
\frac{z_1}{z_2} = \frac{a_1 + i b_1}{a_2 + i b_2}.
$$

Multiplying by $ \frac{a_2 - i b_2}{a_2 - i b_2} $:

$$
\frac{z_1}{z_2} = \frac{(a_1 + i b_1)(a_2 - i b_2)}{(a_2 + i b_2)(a_2 - i b_2)}.
$$

$$
\frac{z_1}{z_2} = \frac{(a_1 + i b_1)(a_2 - i b_2)}{a_2^2 + b_2^2}.
$$

### Observations
Clearly, other than addition/subtraction, multiplication and division are tedious in cartesian coordinates. Thus it is useful to use the polar form of complex numbers to perform multiplication and division of many complex numbers.

## Arithmetic of Complex numbers in Polar Form

Multiplication

$$ z_1 z_2 = (a_1 + i b_1)(a_2 + i b_2) = r_1 e^{i \theta_1 } r_2 e^{i \theta_2 } = (r_1 r_2)e^{i (\theta_1 + \theta_2)} $$

Division

$$ \frac{z_1}{z_2} = \frac{r_1 e^{i \theta_1}}{r_2 e^{i \theta_2}} = \frac{r_1}{r_2}e^{i (\theta_1 - \theta_2)} $$

Square Root

$$ \sqrt{z} = z^{1/2} = (re^{i \theta})^{1/2} = \sqrt{r} e^{i \theta/2} $$
