# Excess log-loss scaling of centered normalized networks

A self-contained proof of the fixed-depth excess log-loss (predictive KL) scaling law for
Bayes-optimal learning in deep teacher–student networks.

**PDF:** [`scaling-proof.pdf`](scaling-proof.pdf) · **Source:** [`scaling-proof.tex`](scaling-proof.tex)

## Result

Gaussian regression $y = F_{\theta}(x) + \sqrt{\Delta}\,z$ with a depth-$L$ network
($L \ge 1$ fixed), layer widths $k_\ell/d \to \gamma_\ell \in (0,\infty)$, i.i.d.
standard Gaussian weights and inputs, and $n = \lfloor \alpha d^2 \rfloor$ samples.
Let $\epsilon_{\log}(\alpha)$ be the Bayes excess log-loss (predictive KL) and
$P_{\mathrm{hidden}}=\sum_\ell k_{\ell-1}k_\ell$ the number of hidden weights. Then

$$
\lim_{\alpha\to\infty}\ \limsup_{d\to\infty}\ \Bigl|\alpha\,\epsilon_{\log}(\alpha) - \tfrac12\sum_{\ell=1}^L\gamma_{\ell-1}\gamma_\ell\Bigr| = 0 ,
$$

with the width limit taken first, i.e. $\epsilon_{\log}(\alpha)\simeq P_{\mathrm{hidden}}/(2n)$. The activation class covers centered normalized
`tanh`, the logistic sigmoid and ReLU (an odd smooth branch and a piecewise-linear branch,
each defined by a scalar Hermite condition $\mu_m\neq0$). Unlike the replica-symmetric
treatment of $L\ge2$, no vanishing of the linear Hermite coefficient is required.

The proof assumes neither a replica-symmetric free-entropy formula, nor existence of the
risk limit at fixed $\alpha$, nor local Gaussianity of the posterior.

## Structure

- Lower bound: mixture-path information identity and Gaussian integration by parts with a
  regularized Fisher test field (spectral deficit of the actual tangent).
- Upper bound: noisy Gaussian parameter oracle, ridge tangent predictor, exact block chain
  identity, and an oracle information cost controlled by posterior contraction plus
  global matching of homogeneous comparator networks.
- Appendices: fixed-depth analytic estimates, tangent geometry, raw tree kernels,
  fixed input chaos of actual activations, global matching, and the information inequality.

## Build

Standard LaTeX only (no custom class or template):

```
pdflatex scaling-proof.tex
pdflatex scaling-proof.tex
```

## Changelog

- **v1.1 (2026-10-16)** — notation aligned with the companion paper: $\epsilon_{\log}(\alpha)$, $\epsilon_n$, $I_n$,
  $P_{\mathrm{hidden}}$, Hermite coefficients $\mu_r$, $\mathcal N$; symbols that clash with the paper's
  replica-symmetric quantities ($K_d$, $K$, $q_\ell$, $\lambda$) renamed; "excess log-loss" terminology.

- **v1.0 (2026-10-16)** — first public version (English). Corrections relative to the
  internal draft: the smooth-branch condition is stated as $b_m(1)\neq0$, equivalently
  $\mu_m\neq0$; the piecewise-linear branch requires $\mu_6\neq0$; the linear activation ($b=0$) is explicitly excluded.

## License

[CC BY 4.0](LICENSE).

## Citation

```bibtex
@misc{logloss-scaling-law2026,
  title  = {Excess Log-Loss Scaling of Centered Normalized Networks:
            A Fixed-Depth Theorem in the Dimension-First Limit},
  year   = {2026},
  howpublished = {\url{https://github.com/5akur0/logloss-scaling-law}}
}
```
