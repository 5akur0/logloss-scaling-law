# Excess log-loss scaling of centered normalized networks

A self-contained proof of the fixed-depth excess log-loss (predictive KL) scaling law for
Bayes-optimal learning in deep teacher–student networks.

**Current proof (Chinese, 37 pages, 2026-10-23):** [`scaling-proof-zh.pdf`](scaling-proof-zh.pdf) · [`scaling-proof-zh.tex`](scaling-proof-zh.tex)

**Earlier English edition (v1.1):** [`scaling-proof.pdf`](scaling-proof.pdf) · [`scaling-proof.tex`](scaling-proof.tex)

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
with the precise scalar Hermite and regularity conditions stated in the current proof). Unlike the replica-symmetric
treatment of $L\ge2$, no vanishing of the linear Hermite coefficient is required.

The proof assumes neither a replica-symmetric free-entropy formula, nor existence of the
risk limit at fixed $\alpha$, nor local Gaussianity of the posterior.

## Current proof structure

- A coupling-uniform global function comparison and finite-label parameter matching.
- An auxiliary Gaussian sequence channel turns global matching into the qualitative Fisher spectral property needed for the lower bound.
- Conditional I–MMSE and Gaussian integration by parts give the predictive lower bound with its exact factor 1/2.
- A noisy parameter observation, a ridge predictor, and an exact sample-block information identity give the sharp upper bound.
- All supporting estimates remain in the standalone document. The theorem, activation class and dimension-first limit are unchanged from the preceding Chinese working version.

## Build

Current Chinese edition (Tufte class, Fandol fonts):

```
tectonic scaling-proof-zh.tex
```

Earlier English edition:

```
pdflatex scaling-proof.tex
pdflatex scaling-proof.tex
```

## Changelog

- **2026-10-23 working revision (Chinese)** — 44 to 37 pages: replace the separate tangent-bridge argument with an information-theoretic consequence of global matching, and replace the mixture-channel lower bound with conditional I–MMSE and Gaussian integration by parts. The English edition has not yet been updated to this argument.

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
