# PK Modeling Portfolio

A learning portfolio documenting my transition from computational biomechanics
to pharmacometrics, built around `mrgsolve` in R.

---

## About this repository

I hold a Ph.D. in Mechanical Engineering (University of Calgary, 2024), where
my doctoral work focused on PDE-based mechanistic modeling of knee joint
poromechanics, statistical shape modeling across 1,370 clinical imaging
datasets, and model credibility workflows (global sensitivity analysis,
Monte Carlo uncertainty propagation, V&V).

I am now redirecting this quantitative toolkit toward clinical pharmacology
and pharmacometrics. This repository is the public record of that transition:
a place where I work through PK/PD models from the ground up, document what I
learn, and make my reasoning visible. It is updated continuously and is meant
to be read as a learning journal, not a finished product.

---

## Projects

| Project | Focus | Status |
|---|---|---|
| [`01_house_model/`](01_house_model/) | First hands-on exploration of `mrgsolve` using the built-in `house()` PK/PD model. Multi-dose simulation, dose-response, and quantitative confirmation of linear PK vs. nonlinear PD. | Complete |
| [`02_pk1_oral_one_compartment/`](02_pk1_oral_one_compartment/) | Building a one-compartment oral PK model from scratch using `$PARAM` / `$CMT` / `$ODE`. Parameter sensitivity experiments (KA, CL, V, dose, multiple dosing) and reproduction of textbook results. | In progress |
| `03_pk2_two_compartment/` | Planned next: two-compartment PK model with distribution phase. | Planned |

---

## Tools and references

- **Software**: R 4.x, `mrgsolve`, `dplyr`, `ggplot2`
- **Textbooks**: Rowland & Tozer, *Clinical Pharmacokinetics and Pharmacodynamics* (Ch. 1–8)
- **Documentation**: <https://mrgsolve.org>

---

## Contact

Ruoqi Deng, Ph.D.
[ruoqi.deng@ucalgary.ca](mailto:roydeng57@gmail.com) · Atlanta, GA
[LinkedIn](https://www.linkedin.com/in/ruoqi-deng-492654a5/)
