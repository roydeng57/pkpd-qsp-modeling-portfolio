# 01 — House Model: Exploring a Built-in PK/PD System with mrgsolve

First hands-on project in my PK modeling portfolio. Goal: build operational
familiarity with the `mrgsolve` simulation workflow on a model small enough
to fully understand.

## What this project covers

- Loading and inspecting a pre-built `mrgsolve` model (two-compartment PK with
  indirect-response PD)
- Constructing dosing events and running multi-dose simulations
- Visualizing coupled PK/PD output (`GUT`, `CENT`, `CP`, `RESP`)
- Comparing four dose levels (50, 100, 200, 400 mg) to expose the
  PK linearity / PD nonlinearity distinction
- Confirming the distinction quantitatively with a Cmax / Rmin summary table

## Files

| File | Description |
|---|---|
| `house_exploration.Rmd` | The full analysis as an R Markdown document. |
| `house_exploration.html` | Rendered report (open in a browser). |
| `figures/` | Plots saved separately for reference. |

## Key takeaway

Under the `house()` model, plasma exposure scales proportionally with dose
across the entire 50–400 mg range (linear PK), but the PD response saturates
at higher doses due to the IC50-driven inhibition mechanism. The
exposure–response summary table in Section 4.4 of the report quantifies this
gap. This was the first concrete example I encountered of linear PK coexisting
with nonlinear PD, and it motivated the parameter-level exploration that
follows in `02_pk1` and `03_pk2`.

## What this project is not

Not a parameter sensitivity study: I run multiple dose levels but do not
isolate individual PK or PD parameters. That one-parameter-at-a-time
exploration begins in `02_pk1`. The PD side (indirect-response mechanism,
IC50, Imax) is observed here but not dissected; this project is about
getting comfortable with the simulation workflow before going deeper.

## Next in the portfolio

`02_pk1/` strips the model down to a one-compartment oral PK system and
walks through each parameter one at a time: KA, CL, V, dose, and
multi-dose accumulation. That is where the "what does each parameter
actually do to the curve" question gets answered.

## How to reproduce

```r
install.packages(c("mrgsolve", "dplyr", "ggplot2", "rmarkdown"))
rmarkdown::render("house_exploration.Rmd")
```
