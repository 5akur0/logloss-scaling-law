# Predictive KL scaling for centered normalized networks — proof of the fixed-depth counting law

Full proof (44 pages, Chinese) of the following statement.

**Setting.** Matched teacher–student Bayesian network of fixed depth $L\ge1$, Gaussian inputs $x\sim N(0,I_d)$, i.i.d. standard Gaussian hidden weights, fixed all-ones readout, Gaussian output channel $y=F_{\theta}(x)+\sqrt\Delta\,z$ with $\Delta>0$, proportional widths $k_\ell/d\to\gamma_\ell\in(0,\infty)$, and $n=\lfloor\alpha d^2\rfloor$ samples. Let $c=\lim_d P_{\rm hidden}(d)/d^2=\sum_\ell\gamma_{\ell-1}\gamma_\ell$.

**Activations.** The same $\sigma$ in every layer, with $\mathbb E\sigma(G)=0$ and $\mathbb E\sigma(G)^2=1$, and either
1. $\sigma$ bounded, odd and $C^\infty$ with all derivatives bounded, with $\mathbb E[\sigma(G)\mathrm{He}_m(G)]\ne0$ for some odd $m\ge5$ (e.g. normalized $\tanh$ of any slope, centered sigmoid); or
2. $\sigma(z)\propto az+b(|z|-\sqrt{2/\pi})$ with $b\neq0$ (e.g. centered ReLU, leaky ReLU).

**Theorem.**
$$\lim_{\alpha\to\infty}\ \limsup_{d\to\infty}\ \bigl|\alpha\,\epsilon_{\log,d}(\alpha)-c/2\bigr|=0,$$
where $\epsilon_{\log,d}(\alpha)$ is the Bayes-averaged predictive KL at $n=\lfloor\alpha d^2\rfloor$.

The proof does not assume a replica-symmetric formula, the existence of the risk limit at fixed $\alpha$, a branch selection, or differentiated MMSE asymptotics. The dimension limit is taken before the sample-ratio limit.

## Files
- `CENTERED_NORMALIZED_PROOF.pdf` — compiled proof.
- `CENTERED_NORMALIZED_PROOF.tex` — source (tufte-handout, XeLaTeX).

## Build
```sh
xelatex CENTERED_NORMALIZED_PROOF.tex
xelatex CENTERED_NORMALIZED_PROOF.tex
```
Requires `tufte-handout`, `xeCJK`, the Fandol fonts and TeX Gyre Pagella (all in TeX Live).

## Changelog
- **v1.0 (2026-10-16).** Two corrections to the 2026-10-14 version, with no change to any argument:
  1. The activation condition (3) no longer contains the radial condition $\inf_{s\in J}|b_m'(s)|>0$ or the interval $J$. Neither was used in the proof, which needs only $a_m\ne0$ and the parity relations $a_{m\pm1}=0$. Section 2 was reworded to match.
  2. Appendix A.3 previously stated that $b=0$ ($\sigma=\pm z$) belongs to the smooth branch. It does not: the linear activation is unbounded, has $a_m=0$ for all $m\ge2$, and the theorem fails for it.

## License
The text and figures are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); see `LICENSE`.

## Citation
```bibtex
@misc{counting_law_proof_2026,
  title        = {Predictive {KL} Scaling for Centered Normalized Networks: Proof of the Fixed-Depth Counting Law},
  year         = {2026},
  howpublished = {GitHub repository, version v1.0},
  url          = {https://github.com/OWNER/scaling-proof}
}
```
