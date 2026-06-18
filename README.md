# Disentangling Offence Composition from Differential Response in Toronto Hate-Crime Arrests
An inferential analysis of whether the lower arrest rate for religious-bias hate crimes in Toronto reflects how police respond, or simply what kinds of crime are being committed.

## Question
Religious-bias hate crimes in Toronto are arrested at roughly half the rate of other hate crimes (~15% vs ~28%). Does this reflect a difference in police response to religious-bias crimes, or is it explained by offence composition, with religious-bias incidents concentrated in the kinds of crime (property mischief) that are hard to clear for anyone?

## Finding
The raw arrest gap is largely explained by offence composition rather than differential police response. In a logistic regression, the raw association between religious bias and lower arrest (odds ratio 0.43, p < 0.001) does not survive controlling for offence type (OR 0.86, 95% CI [0.67–1.12], p = 0.26). The confidence interval crosses 1.0, so any residual association is not statistically detectable. Religious-bias hate crimes concentrate in low-clearing property mischief; once offence type is accounted for, no statistically detectable difference in arrest rate by religious-bias status remains.

The effect is not uniform across offence types, and the variation is itself the more informative result. Within offence categories the gap vanishes for mischief, reverses for violent crime, and persists for threats (a partial exception). Propaganda has too few cases to interpret and is shown with sample sizes for transparency. The pooled estimate averages over strata that disagree, so the single-number summary understates what is actually going on: the disparity is not one phenomenon but several, and offence composition is what makes them sum to a near-null overall.

## Scope and limitations
This analysis describes how police responded to incidents the Toronto Police Hate Crime Unit confirmed and classified as hate crimes. It is not a measure of hate crime incidence, and not a measure of "bias." The data includes only verified hate crimes (unfounded cases and non-criminal hate incidents are excluded), so the classification itself reflects investigative judgment. Arrest is one enforcement action, not a measure of justice. Offence type is one confounder; year, location, and investigative effort are uncontrolled. Several offence categories have small samples. The defensible conclusion is deliberately narrow: the raw arrest gap is attributable to crime composition, not to a statistically detectable difference in arrest response by religious-bias status.

## Data
Toronto Police Service, Hate Crime Open Data: confirmed hate-crime occurrences investigated by the Hate Crime Unit, with occurrence dates from August 2014 to December 2025. Released under the Open Government Licence – Ontario. Analysis covers 2,019 incidents after excluding 22 uncategorizable "Other" offences.

Source: [Toronto Police Service Hate Crime Open Data](https://data.tps.ca/datasets/TorontoPS::hate-crimes-open-data/about) (Open Government Licence – Ontario). The exact snapshot analyzed is included in `data/raw/` for reproducibility.

## Method
Logistic regression used for inference, not prediction: arrest modelled on religious-bias status, with and without controlling for offence type, reading coefficients and confidence intervals rather than predictive accuracy. The 30 raw offence types were grouped into four behavioral categories (mischief, violent, threats, propaganda) by whether the offence tends to have an identifiable suspect, which is the factor driving arrest likelihood. The grouping was assigned from offence labels alone, before modelling. Grouping decisions, including edge cases, are documented in the notebook.

## Licence
Code is released under the MIT License (see `LICENSE`). The underlying data is Toronto Police Service Open Data, used under the Open Government Licence – Ontario; the MIT License applies to this repository's code, not to the data.

## Repository
* `notebooks/hate_crime_arrests.ipynb` — full analysis
* `data/raw/hate_crime_raw.csv` — source data
* `figures/arrest_by_offence.png` — main result figure

## Tools
Python · pandas · statsmodels · matplotlib
