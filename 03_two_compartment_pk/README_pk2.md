# PK2: Two-Compartment Oral PK Parameter Sensitivity Exploration

Third project in my PK modeling portfolio. Building on the one-compartment
work in `02_pk1`, this project adds a peripheral compartment connected by
inter-compartmental clearance `Q`, introducing the distribution phase and
the characteristic two-slope semi-log profile that was absent from pk1.

## What this project covers

- Simulating a two-compartment oral PK model (`mrgsolve::modlib("pk2")`)
  with default parameters (CL=1, V2=20, Q=2, V3=10, KA=1)
- Six parameter sensitivity experiments:
  - Double Q: how inter-compartmental clearance reshapes the distribution phase
  - Double V3: a failed prediction corrected by tracing through the ODE system
  - Q→0: verifying degeneration to the one-compartment (pk1) limit
  - Q→∞: rapid-equilibrium limit and the disappearance of biphasic behavior
  - Double dose: confirming linearity carries over from pk1
  - Multiple dosing: pk1 vs pk2 comparison of peak-to-trough fluctuation
- AUC conservation check across parameter perturbations
- Terminal half-life discrepancy noted as an honest observation with hypothesis

## Files

| File | Description |
|---|---|
| `pk2_exploration.Rmd` | The full analysis as an R Markdown document. |
| `pk2_exploration.html` | Rendered report (open in a browser). |

## Key takeaway

The most instructive experiment was doubling V3. I predicted that a larger
peripheral volume would lower the central concentration by pulling more drug
into the periphery, but the simulation showed the opposite at later time
points. Tracing through the ODEs revealed why: a larger V3 lowers the
peripheral concentration gradient, which slows the return flow Q×(C3−CP) and
reduces net transfer out of the central compartment. The prediction failed
because I was reasoning from a static snapshot rather than following the
coupled differential equations forward in time. This is the same lesson that
the volume-of-distribution experiment taught in pk1, scaled up to a system
where two compartments interact through bidirectional flow.

The limiting-case experiments (Q→0 and Q→∞) were also valuable. Watching
the two-compartment model collapse to the one-compartment limit as Q
approaches zero, and seeing the biphasic kink disappear as Q grows large,
made the role of inter-compartmental clearance concrete in a way that reading
about distribution phases had not.

## What this project is not

Not a published-model reproduction, and not a population analysis: there are
no covariates, no inter-individual variability, and no clinical data. The
model uses mrgsolve's built-in default parameters rather than representing a
specific drug. That step comes next in `04_pk3_published_model/`.

## Next in the portfolio

`04_pk3_published_model/` will move from built-in library models to
reproducing a published population PK study with covariate effects and
inter-individual variability. That is the transition from exploring
pre-built systems to working with the kind of models I expect to encounter
in regulatory submissions.

## How to reproduce

```r
install.packages(c("mrgsolve", "dplyr", "ggplot2", "tidyr", "rmarkdown"))
rmarkdown::render("pk2_exploration.Rmd")
```
