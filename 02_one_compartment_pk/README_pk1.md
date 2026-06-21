# PK1: One-Compartment Oral PK Parameter Sensitivity Exploration

A from-the-parameters-up exploration of the simplest pharmacologically
meaningful PK structure: one-compartment, first-order oral absorption,
first-order elimination. Built on `mrgsolve`'s built-in `pk1` model.

## What this project covers

1. **Baseline:** single 100 mg dose, 48 h horizon. Sets the reference profile.
2. **Double `KA`:** faster absorption phase, earlier `Tmax`, unchanged terminal slope.
3. **Double `CL`:** steeper terminal slope, shorter half-life, lower AUC.
4. **Double `V`:** opposite shifts in `CENT` vs `CP` (the section worth lingering on).
5. **Double the dose:** dose-proportional scaling under linear PK.
6. **Multiple dosing (Q12h × 5):** accumulation toward steady state.

Each experiment isolates a single change against the same baseline so the
shift is read directly off the overlay plots.

## Files

| File | Description |
|---|---|
| `pk1_exploration.Rmd` | The full analysis as an R Markdown document. |
| `pk1_exploration.html` | Rendered report (open in a browser). |

## Key takeaway

Doubling the volume of distribution `V` moves `Cmax` of the amount in the
central compartment **up**, while moving `Cmax` of plasma concentration
**down**. The mechanism is that `V` acts simultaneously as a denominator in
`k_el = CL/V` (slowing elimination, pushing concentration up) *and* as the
divisor converting amount to concentration (pulling concentration down).
That dual role is the cleanest illustration in this project of why running
a simulation beats reasoning from a single textbook sentence.

See **Section 4.3** of the rendered report for the figure, quantitative
summary, and full mechanism walkthrough.

## What this project is not

Not a reproduction of a published PopPK model, and not a population-level
analysis: there is no inter-individual variability, no covariate effects,
no data fitting. Those come later in the portfolio. This project is purely
a structured walkthrough of "what does each parameter do to the curve,"
which is the foundation everything else builds on.

## Next in the portfolio

`03_pk2_two_compartment/` extends to a peripheral compartment connected
by inter-compartmental clearance `Q`, introducing the distribution phase
and the characteristic two-slope semi-log profile. After that,
`04_pk3_published_model/` will move from built-in models to reproducing a
published PopPK study with covariate effects and inter-individual
variability.

## How to reproduce

```r
# From this folder, in an R session with mrgsolve installed:
rmarkdown::render("pk1_exploration.Rmd")
```

Requirements: `mrgsolve`, `dplyr`, `ggplot2`, `tidyr`. A working C++
compiler is needed for `mrgsolve` to build the model (Rtools on Windows,
Xcode CLT on macOS).
