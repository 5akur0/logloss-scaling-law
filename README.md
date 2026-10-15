# Predictive KL scaling of centered normalized networks

A self-contained proof of the fixed-depth predictive KL scaling law for
Bayes-optimal learning in deep teacher–student networks.

**PDF:** [`scaling-proof.pdf`](scaling-proof.pdf) · **Source:** [`scaling-proof.tex`](scaling-proof.tex)

## Result

Gaussian regression $y = F_{\theta}(x) + \sqrt{\Delta}\,z$ with a depth-$L$ network
($L \ge 1$ fixed), layer widths $k_\ell/d \to \gamma_\ell \in (0,\infty)$, i.i.d.
standard Gaussian weights and inputs, and $n = \lfloor \alpha d^2 \rfloor$ samples.
Let $\varepsilon_{\log,d}(\alpha)$ be the average Bayes predictive KL and
$c = \lim_d P_{\mathrm{hidden}}(d)/d^2 = \sum_{\ell} \gamma_{\ell-1}\gamma_\ell$. Then

$$
\lim_{\alpha\to\infty}\ \limsup_{d\to\infty}\ \Bigl|\alpha\,\varepsilon_{\log,d}(\alpha) - \tfrac{c}{2}\Bigr| = 0 ,
$$

with the width limit taken first. The activation class covers centered normalized
`tanh`, the logistic sigmoid and ReLU (an odd smooth branch and a piecewise-linear branch,
each defined by a scalar Hermite condition).

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

- **v1.0 (2026-10-16)** — first public version (English). Corrections relative to the
  internal draft: the smooth-branch condition is stated as $b_m(1)\neq0$, equivalently
  $a_m=\mathbb E[\sigma(G)\mathrm{He}_m(G)]/\sqrt{m!}\neq0$; the piecewise-linear branch
  requires $a_6\neq0$; the linear activation ($b=0$) is explicitly excluded.

## License

[CC BY 4.0](LICENSE).

## Citation

```bibtex
@misc{scalingproof2026,
  title  = {Predictive {KL} Scaling of Centered Normalized Networks:
            A Fixed-Depth Theorem in the Dimension-First Limit},
  year   = {2026},
  howpublished = {\url{https://github.com/5akur0/scaling-proof}}
}
```
