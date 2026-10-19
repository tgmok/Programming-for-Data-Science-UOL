# Programming for Data Science (ST2195) — University of London

Coursework project completed in **both R and Python**, covering Markov Chain Monte Carlo simulation and a 10-year analysis of US commercial flight data.

📄 **Full report:** [Coursework_Report_Trixie.pdf](Coursework_Report_Trixie.pdf)

| | Python | R |
|---|---|---|
| Part 1 — MCMC | [Python_part_1.ipynb](Python_part_1.ipynb) | [R part 1..Rmd](<R part 1..Rmd>) |
| Part 2 — Flight data | [Python Part 2 (1).ipynb](<Python Part 2 (1).ipynb>) | [R part 2 (1).Rmd](<R part 2 (1).Rmd>) |

---

## Part 1 — MCMC simulation (Metropolis-Hastings)

**Task:** Simulate random samples from the Laplace distribution f(x) = ½·exp(−|x|) using the random walk Metropolis algorithm, then check convergence.

- **(a)** Generated samples (s = 1), plotted a histogram + kernel density estimate against the true PDF, and reported the Monte Carlo mean and standard deviation. The KDE closely matched the true density.
- **(b)** Implemented the **R̂ (R-hat) convergence diagnostic** with 4 chains of 2,000 iterations, and plotted R̂ across a grid of step sizes s ∈ [0.001, 1]. R̂ dropped below the 1.05 threshold as s increased, indicating convergence.

## Part 2 — US flight delays, 1999–2008

**Data:** [2009 ASA Data Expo](https://doi.org/10.7910/DVN/HG7NV7) (Harvard Dataverse): yearly flight records 1999–2008, plus airport, carrier and plane data.

**Data preparation:** Processed one year at a time to stay within memory limits; removed cancelled/diverted flights and duplicates; filled missing values (last observation carried forward); combined all delay columns into a total delay.

### (a) Best times to fly to minimise delays

| Years | Best time | Best day | Best month |
|---|---|---|---|
| 1999–2001 | 04:00–05:59 | Tuesday | Oct / Jan / Nov |
| 2002 | 04:00–05:59 | Saturday | February |
| 2003–2007 | 06:00–07:59 | Saturday | April / September |
| 2008 | 06:00–07:59 | Wednesday | – |

Early mornings had the fewest delays; evenings (18:00–19:59) the most. Summer months peaked.

### (b) Do older planes suffer more delays?

Joined flights with plane manufacture year and plotted average delay vs aircraft age per year. Trend lines showed a slight positive slope, but the effect was weak relative to the overall rise in delays across years, so age alone is not a strong indicator.

### (c) Predicting flight diversions (logistic regression)

Fitted a logistic regression per year using date, scheduled times, airport coordinates, distance and carrier, then visualised how coefficients changed over time and evaluated models with ROC curves.

## Tools

**R:** tidyverse / ggplot2, R Markdown · **Python:** pandas, NumPy, matplotlib, seaborn, scikit-learn, Jupyter

## Skills demonstrated

Statistical simulation · convergence diagnostics · large-dataset wrangling · exploratory data analysis · logistic regression · data visualisation · reproducible analysis in two languages
