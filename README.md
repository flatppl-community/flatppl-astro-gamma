# flatppl-astro-gamma

[Function reference](docs/reference.md) · [Live example](https://live.flatppl.org/#model=https%3A%2F%2Fraw.githubusercontent.com%2Fflatppl-community%2Fflatppl-astro-gamma%2Fmain%2Fexamples%2Fplayground.flatppl&target=Pi_post)

Differential photon spectra and telescope response operators. Library version **0.1**.

For $x=\ln(E/E_0)$, the log-parabola is $\phi(E)=N_0\exp(-\gamma x-\beta x^2)$, with $\phi(E_0)=N_0$.
The response maps $N$ true-energy nodes to $M$ reconstructed bins.

```math
s_j=t\sum_{i=1}^N R_{ji} A_i\phi_i e^{-a\tau_i}q_i,
\qquad R\in\mathbb R_{\ge0}^{M\times N},\quad \sum_j R_{ji}\le1.
```

$t$ is live time, $A$ effective area, $q$ energy quadrature width, and $a\tau$ scaled optical depth.

```flatppl
flatppl_compat = "0.1"
gamma = load_module("flatppl-astro-gamma/main.flatppl")
flux = gamma.logparabola(2.0, 1e-8, 2.2, 0.1, 1.0)
photon_flux = gamma.powerlaw_photon_integral(0.5, 5.0, 1e-8, 2.2, 1.0)
```

The [synthetic ON/OFF example](examples/synthetic-onoff.flatppl) combines this response with an explicit amplitude prior and a joint Poisson count law.
