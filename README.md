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
It can be checked that the obtained poles on the negative axis and their associated residues agree well with the first ones of $\Gamma(z)$ although their accuracy decreases as one moves further from the interpolation interval. Recall that $\Gamma(z)$ has poles $0,-1,-2,-3,\ldots$ and associated [residues](https://en.wikipedia.org/wiki/Gamma_function#Residues) $Res(\Gamma,-k) = (-1)^k /k!$.
```matlab
[pol(find(real(pol)<eps)) res(find(real(pol)<eps))]
```
```matlab
ans =
   0.0000 + 0.0000i   1.0000 - 0.0000i
  -1.0000 + 0.0000i  -1.0000 + 0.0000i
  -2.0000 + 0.0000i   0.5000 - 0.0000i
  -3.0032 + 0.0000i  -0.1697 + 0.0000i
  -3.7960 + 0.0000i   0.0368 - 0.0000i
```
