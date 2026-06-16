# N-subjettiness, intuitively

An interactive web app that builds intuition for jet $N$-subjettiness:

$$\tau_N = \frac{1}{d_0} \sum_k p_{T,k}\,\min\!\big(\Delta R_{1,k},\,\Delta R_{2,k},\,\dots,\,\Delta R_{N,k}\big)$$

Drag the subjet axes around a randomly generated jet, switch between 1-/2-/3-prong jet topologies (QCD, W/Z, top), and watch $\tau_N$ and the tagging ratios $\tau_2/\tau_1$, $\tau_3/\tau_2$ react in real time.

**Live demo:** https://nollde.github.io/substructure/

## What it shows

- Particles plotted on the $(\eta, \phi)$ plane, sized by $p_T$ and colored by their nearest subjet axis.
- Yellow ✕ markers for the $N$ subjet axes — drag them anywhere; $\tau_N$ updates continuously.
- Axes initialize at the locally optimal positions (pT-weighted Lloyd's algorithm with farthest-point seeding) so dragging always moves *away* from the optimum.
- Live values: $\tau_1$, $\tau_2$, $\tau_3$ at their optima, plus $\tau_N$ for the current draggable configuration.

## Why $\tau_N$ makes sense

$\tau_N$ measures how badly a jet resists being squeezed into $N$ prongs. If the jet really has $N$ hard cores, you can place $N$ axes so every hard particle sits right on one — the sum collapses, $\tau_N \to 0$. Force the same jet into $N{-}1$ axes and the leftover prong has nowhere to go — its hard particles contribute large $p_T \cdot \Delta R$ terms. That's why **ratios** like $\tau_2/\tau_1$ (W/Z tagging) and $\tau_3/\tau_2$ (top tagging) discriminate prong counts.

## Running locally

It's a single static HTML file with no build step:

```bash
open index.html
```

…or serve it:

```bash
python3 -m http.server 8000
```

## Stack

- Vanilla JS, single file — no framework, no bundler.
- MathJax (CDN) for inline LaTeX rendering.
- pT-weighted Lloyd's algorithm with multi-restart for finding optimal axes.

## Credits

Concept & Direction: **Dennis Noll**
Coding: **Claude Code**
