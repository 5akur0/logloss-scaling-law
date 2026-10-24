# Excess log-loss scaling of centered normalized networks

A self-contained proof of the fixed-depth excess log-loss (predictive KL) scaling law for
Bayes-optimal learning in deep teacher–student networks.

**Current proof (Chinese, 20 pages, 2026-10-24):** [`scaling-proof-zh.pdf`](scaling-proof-zh.pdf) · [`scaling-proof-zh.tex`](scaling-proof-zh.tex)

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
with the precise regularity conditions stated in the current proof). Unlike the replica-symmetric
treatment of $L\ge2$, no vanishing of the linear Hermite coefficient is required.

The proof assumes neither a replica-symmetric free-entropy formula, nor existence of the
risk limit at fixed $\alpha$, nor local Gaussianity of the posterior.

## Current proof structure

- A coupling-uniform global function comparison and finite-label parameter matching.
- Bounds on the mutual information of the actual training data turn posterior parameter contraction into the qualitative Fisher spectral property needed for the lower bound.
- Conditional I–MMSE and Gaussian integration by parts give the predictive lower bound with its exact factor 1/2.
- Consistent linear Gaussian reference distributions, relative-entropy monotonicity, and a sample-block information identity give the sharp upper bound.
- Rotational symmetry gives moments of individual backpropagated coordinates; Hölder controls gradient differences for both activation branches. A positive perturbation exponent suffices because dimension tends to infinity first. A Hermite calculation then gives the linearization remainder.
- All supporting estimates remain in the standalone document. The scaling theorem and dimension-first limit are unchanged; the redundant radial Hermite-derivative condition has been removed without excluding any previously covered activation.

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

- **2026-10-24 English errata** — Use the defined ridge matrix `R` consistently in Section 7, correct the explanation of the sixth Hermite coefficient, and specialize Appendix A.6 to the Gaussian channel used in this paper. Regenerate the English PDF; the current Chinese edition is unchanged.

- **2026-10-24 eleventh working revision (Chinese)** — Shorten prose by 1,052 Chinese characters (8.3%), removing repeated explanations and replacing indirect wording with explicit statements. All 132 displayed formula blocks, theorem hypotheses and typography are retained; the standalone PDF remains 20 pages.

- **2026-10-24 tenth working revision (Chinese)** — 26 to 20 pages with unchanged typography and theorem. A common coordinate-moment argument replaces Hessian and negative-moment estimates; dimension-first limits allow the weaker positive perturbation exponent. Combine activation projection and repeated-index restoration into one recurrence, use one ordered-tree induction, and organize homogeneous matching as a single-layer estimate followed by depth induction. Merge repeated information estimates while retaining their derivations.

- **2026-10-24 ninth working revision (Chinese)** — 27 to 26 pages: reuse the main OU estimates in their appendix proof, remove repeated matching bounds and definitions, and streamline the Sobolev approximation argument. All hypotheses, error rates and proof steps are retained.

- **2026-10-24 eighth working revision (Chinese)** — Remove three repeated interfaces and four intermediate displays. Give the tensor lemmas distinct reference numbers and identify the relevant item in the local contraction lemma; replace the remaining metaphorical contraction wording.

- **2026-10-24 seventh working revision (Chinese)** — 29 to 27 pages: one conditional-entropy estimate handles both parameter information and auxiliary-observation cost; one relative-entropy identity controls cumulative and incremental information. Share coefficient moment, coordinate and repeated-index estimates across the geometric proofs. Obtain the polynomial correction formula directly by cancelling its deterministic quadratic diagonal. Remove duplicated model definitions and proof summaries; shorten moment and Hessian estimates while retaining all boundary cases.

- **2026-10-24 sixth working revision (Chinese)** — Describe geometric contraction steps using parent indices, remaining factors and stopping positions. Remove metaphorical descriptions while preserving the original hypotheses, displays and labels.

- **2026-10-24 fifth working revision (Chinese)** — Smooth the complete regularized Fisher test field. This removes output smoothing, inverse-matrix differentiation and the comparison with a smoothed Fisher matrix. The lower bound now closes with one fixed regularization parameter, sent to zero after the dimension and sample-ratio limits. Specialize the information identity to the scalar prediction channel.

- **2026-10-24 fourth working revision (Chinese)** — Replace the separate odd and piecewise-linear expansion arguments by one induction on source depth, preserving quadratic diagonal and one-remaining-factor cases. Define projections and slice Gram matrices at first use and replace ambiguous geometric terminology.

- **2026-10-24 third working revision (Chinese)** — 31 to 29 pages: use actual-data mutual information for the spectral argument and remove the auxiliary infinite Gaussian sequence; reuse one Gaussian reference bound for the preliminary information estimate; combine repeated OU and tensor estimates. Rewrite the geometric and activation-expansion proofs with explicit indices and contractions, reducing invented terminology and removing diagnostic counterexamples.

- **2026-10-24 second working revision (Chinese)** — 34 to 31 pages: unify the two predictive lower bounds with a parameter-OU test field; recover row matching and tensor coefficients from one square-difference identity; shorten the actual-activation recursion and remove unused tensor estimates. Bounded normalized odd activations automatically have a nonzero high-order Hermite coefficient, so the redundant radial-derivative condition and long tanh verification are removed.

- **2026-10-24 working revision (Chinese)** — 37 to 34 pages: replace the ridge upper-bound construction by a consistent Gaussian-reference argument; replace activation smoothing by parameter OU smoothing; consolidate residual-tensor contractions and remove redundant terminal sign constraints. The theorem and activation class are unchanged.

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
