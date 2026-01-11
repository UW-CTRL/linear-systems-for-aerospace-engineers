# Frequency response

So far, we introduced the concept of a *transfer function*, and how with knowledge of an input $U(s)$, we can compute the output $X(s)$. 
Previously, we restricted our discussion to mainly impulse and step inputs. Intuitively, if the system was stable, then the output, given an impulse or step input, would settle to some steady-state value. 
Now, what would happen if the input was *sinusoidal*? Like a vibrational input? If the input is constantly changing in magnitude, then presumably the output would also have changing magnitude. In this chapter, we investigate exactly what that output behavior is given a sinusoidal input with various frequencies.


## Why consider sinusoidal input?
You might be thinking why we are considering sinusoidal inputs? In real-world settings, vibrations are rarely perfectly sinusoidal. They are quite messy and potentially irregular.

Well it turns out that despite a oscillatory signal (like vibrations) not being perfectly sinusoidal, it can be represented as a sum of simpler sine and cosine waves. This is the core principle behind *Fourier analysis*, the study of the way general functions may be represented, or approximated, by sums of trignometric functions of different frequencies.
Related to the Laplace transform, there is also the *Fourier Transform* which takes a signal in the time domain, and transforms it into the frequency domain, a function describing the how much the sine/cosine at a particular frequency contributes to the original function.

Okay, so hopefully now you are convinced that we can represent arbitrary oscillatory functions as a sum of sine and cosine terms. But why should we only consider input that is sinusoidal, rather than the sum of many? Remember that we are concerned with LTI systems. The superposition property means we can simply add up the contributions of each individual sine/cosine component, rather than consider them at the same time.



## System response to a sinusoid

Suppose we have a transfer function $G(s)$. Assume that is is stable, with all poles in the left half plane.
Now consider a sinusoidal input. For mathematical convinience, we consider input $u(t) = e^{i\omega t} = \cos \omega t + i\sin \omega t$. Obviously, it is not physically possible provide a complex input signal. But rather, the *real* part of the output expression will correspond to *real* part of the input ($\cos\omega t$) while the *imaginary* part of the output expression will correspond to the *imaginary* part of the input ($\sin\omega t$). This may be more clear after the following derivation.

If $u(t) = e^{i\omega t}$, then $U(s) = \frac{1}{s - i\omega}$ (this is the frequency shift rule from our laplace table).
Then the output is

$$X(s) = G(s)U(s) = G(s) \frac{1}{s-i\omega}$$


We can expand $G(s)$ and apply partial fraction decomposition to obtain $X(s)$ as a sum:

$$ X(s) = \dfrac{K}{\prod_{k=1}^{n} (s + p_i)} \cdot\dfrac{1}{s - i\omega} = \sum_{k=1}^{n} \dfrac{A_k}{s + p_k} + \dfrac{a}{s - i\omega} $$

where $\{ -p_k \}_{i=1}^{n}$ are the poles of $G(s)$.
Multiplying both sides by $s - i\omega$,

$$ X(s) (s - i \omega) = G(s) = \sum_{k=1}^n \dfrac{A_k}{s + p_k}(s - i\omega) + a $$

We can recover $a$ by setting  $s=i\omega$:

$$G(i\omega) = a$$

Substituting $a$,

$$ X(s) = \sum_{k=1}^{n} \dfrac{A_k}{s + p_k} + \frac{G(i\omega)}{s - i\omega} $$

Taking the inverse Laplace transform gives

$$ x(t) = \sum_{k=1}^{n} A_k e^{-p_k t} + G(i \omega) e^{i \omega t}$$

Let's analyze the steady state response of this system, i.e. as $t \rightarrow \infty$. The first summation term goes away because the system is stable, leaving us with the following where we have rewritten it in polar form.


$$ \lim_{t \rightarrow \infty} x(t) &= G(i\omega)e^{i\omega t}\\
&= | G(i\omega) | e^{i \angle G(i\omega) } e^{i \omega t} \\
&= | G(i\omega) | e^{i \angle G(i\omega) + \omega t}\\
&= | G(i\omega) | \left( \cos{\left(\omega t + \angle G(i\omega)\right)} + i \sin{\left(\omega t  + \angle G(i\omega)\right)} \right)\\
&= M \left( \cos{\left(\omega t + \angle G(i\omega)\right)} + i \sin{\left(\omega t  + \angle G(i\omega)\right)} \right)
$$

Thus we see that the input $u(t)$ is modulated by $G(i \omega)$; its amplitude is magnified by $| G(i \omega) |$ and its phase is shifted by $\angle G(i \omega)$. So the real part of the input $e^{i\omega t}$, $\cos{\left(\omega t\right)}$ leads to the real part of the output of $M \cos{\left(\omega t + \phi\right)}$ and the imaginary part of the input $e^{i\omega t}$, $\sin{\left(\omega t\right)}$ leads to the imaginary part of the output of $M \sin{\left(\omega t + \phi\right)}$

So what is the takeaway here? Given an LTI system $G(s)$, for a sine (or cosine) input, the output is also a sine (or cosine) but the amplitude is scaled by $M=|G(i\omega)|$ and a phase shift by $\phi = \angle G(i\omega)$.
So to describe the output of the LTI given an sinusoidal input with frequency $\omega$, then


Note that $G(i\omega)$ is a complex number; it is just the transfer function where we set $s=i\omega$.



:::{exercise} Example
:class: example

Find the magnitude and phase of $G(s) = \dfrac{1}{s+1}$ where $s = i\omega$.

$$
\left| G(i\omega) \right| = \left| \frac{1}{1 + i\omega} \cdot \frac{1 - i\omega}{1 - i\omega} \right| = \left| \frac{1 - i\omega}{1 + \omega^2} \right| = \frac{\sqrt{1 + \omega^2}}{1 + \omega^2}
$$

$$ \angle G(i \omega) = \angle 1 - \angle(1 + i\omega) = -\tan^{-1}({\omega}) $$
:::


:::{exercise} Example
:class: example

Find the magnitude and phase of $G(s) = \dfrac{10}{s+10}$ where $s = i\omega$.

$$
\left| G(i\omega) \right| = \left| \frac{10}{10 + i\omega} \right| = \frac{10 \sqrt{100 + \omega^2}}{100 + \omega^2}
$$

$$ \angle G(i\omega) = \angle 1 - \angle(10 + i\omega) = -\tan^{-1} \left( \frac{\omega}{10} \right)
$$
:::


:::{exercise} Example
:class: example

Find the magnitude and phase of $G(s) = \frac{1}{(s+1)(s+10)}$ where $s=i\omega$.

$$
\left| G(i\omega) \right| = \left| \frac{1}{(10 + i\omega)(1 + i\omega)} \right| = \frac{1}{\sqrt{100 + \omega^2} \cdot \sqrt{1 + \omega^2}}
$$

$$
\angle G(i\omega) = \angle 1 - (\angle(10 + i\omega) + \angle(1 + i\omega)) = -\tan^{-1}(\omega/10) - \tan^{-1}(\omega)
$$
:::

:::{exercise} Example
:class: example

Find the magnitude and phase of $G(s) = \dfrac{s + 3}{s + 5}$ where $s=i\omega$.

$$
| G(i\omega) | = \dfrac{|3 + i\omega|}{|5 + i\omega|} = \dfrac{\sqrt{9 + \omega^2}}{\sqrt{25 + \omega^2}}
$$

$$
\angle G(i\omega) = \tan^{-1}(\omega/3) - \tan^{-1}{(\omega /5)}
$$
:::

But the magnitude and phase shift of the output signal depends on the input frequency $\omega$. Generally, we are interested in what the output is like for a range of input frequencies, not just one specific freqency.
Different vibrational sources correspond to different frequency ranges, and a system may be subject to *multiple* vibrational inputs, so we definitely want to know how the system behaves across multiple frequency ranges.

In the next section, we cover techniques to *sketch* what the magnitude and phase are across a wide range of frequencies.

## Bode plots