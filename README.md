# Stat 451 — Bigfoot Sightings Analysis

**Group 3:** Blake Holman, Eric Lu, Adela Yan, Xabier Bisabarros-Hudoc, Faraz Behlum

---

## Overview

This project analyzes the [BFRO Bigfoot Sightings dataset](https://www.kaggle.com/datasets/thedevastator/unlocking-mysteries-of-bigfoot-through-sightings) to understand what environmental, geographic, and weather-related factors are associated with reported Bigfoot sightings. Our core goal is to classify sightings as **Class A** (direct visual contact) vs **Class B** (circumstantial evidence like sounds or tracks), and to uncover patterns in where and when sightings are most likely to occur.

---

## Research Questions

1. What factors influence whether a sighting is Class A vs Class B?
2. Can we predict the classification of a new sighting using available features?
3. What environmental conditions and locations are most associated with sightings?
4. What does the data say specifically about Bigfoot sightings in Wisconsin?

---

## Dataset

- **Source:** [Kaggle — Unlocking Mysteries of Bigfoot Through Sightings](https://www.kaggle.com/datasets/thedevastator/unlocking-mysteries-of-bigfoot-through-sightings)
- **File used:** `bfro_reports_geocoded.csv`
- **Key features:** classification, state, county, season, latitude/longitude, temperature, humidity, cloud cover, moon phase, wind speed, precipitation, UV index, visibility, and more (28 variables total)

To load the dataset:
```python
import pandas as pd
df = pd.read_csv("bfro_reports_geocoded.csv")
```

---

## Methods

| Task | Method | Why |
|---|---|---|
| Class A vs B classification | Logistic Regression, SVM (RBF kernel) | Logistic gives interpretable coefficients; SVM captures nonlinear boundaries |
| Geographic ruleset | Decision Tree | Human-readable splits; easy to present |
| Feature selection | Lasso Regression | Shrinks irrelevant weather variables to zero; expects sparse signal across 28 features |

**Preprocessing:**
- One-hot encoding for season; target encoding for state (50 categories)
- Mean imputation for ~19% of sightings missing GPS coordinates
- Standardization of all weather variables before SVM fitting

---

## Resources

- [Project Proposal](https://docs.google.com/document/d/1rfGouiVzyGGeA4JohGGnpiWpiX5CIRPr8f9oICG1fMU/edit?usp=sharing)
- [Google Slides Presentation](https://docs.google.com/presentation/d/1KaI4kTSDw4AhNsedKxkDjE-kIUW2YDfbEUA684bk7h4/edit?usp=sharing)

---

## Repository Structure

```
Stat451-Project/
├── README.md
├── data/               # Instructions for downloading dataset from Kaggle
├── notebooks/          # Jupyter notebooks for EDA, modeling, and results
└── results/            # Plots, figures, and output files
```
