# TCF

This repository contains MATLAB codes for performing TCF rational approximation

## Approximating the Gamma function.
We approximate the Gamma function $\Gamma(z)$ on the real line using 100 linearly spaced points between $-1.5$ and $1.5$
```matlab
Z = linspace(-1.5,1.5);
f = @(z) gamma(z);
[r,pol,res] = tcf(f,Z);
```
One can plot the approximation on a wider domain such as ($-3.5, 4.5)$
```matlab
zz = linspace(-3.5,4.5,1000).';
figure()
plot(zz,r(zz))
xlim([-3.5 4.5])
ylim([-8 8])
grid on
xlabel('x')
ylabel('r(x)')
title('Rational approximation of the Gamma function')
```
