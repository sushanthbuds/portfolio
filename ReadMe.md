# Statistics Final Project — Group 7

**Obesity levels: analysis of lifestyle and demographic factors**

Quarto-based course website and reproducible analysis for **George Mason University**, MS in Data Analytics. The project explores an obesity-related dataset (OpenML), with data cleaning, statistical tests, and machine learning in R.

---

## What’s in the project

| Item | Description |
|------|-------------|
| `_quarto.yml` | Quarto website config (navbar, Minty theme, `styles.css`) |
| `index.qmd` | **Code** page — full R workflow: cleaning, EDA, plots, chi-square, SVM, logistic regression, decision tree |
| `Introduction.qmd` | Narrative: dataset, NOIR table, cleaning, research questions, methodology, conclusions |
| `about.qmd` | Project / team contact (Quarto “trestles” template) |
| `us.qmd` | Short bios: Sushanth Buddhala, Sumanth Veluvolu, Vivek Atchutanna |
| `team.qmd` | Default Quarto “Running Code” placeholder |
| `References.qmd` | OpenML dataset link and other citations |
| `Cleaned_Dataset_rename.csv` | Cleaned dataset (exported from the analysis pipeline) |
| `Group_7.Rproj` | RStudio project file |
| `docs/` | Pre-rendered static site (HTML + `site_libs`) |

**Note:** `Introduction.qmd` references image files (e.g. `Obesity.jpg`, PNG figures). Those images are **not** in the zip; add them next to the `.qmd` files or update paths if figures are missing when you render.

---

## Research questions

1. How does a **family history of overweight** relate to **obesity level** (with BMI and gender)?
2. Are there **significant differences in obesity levels between males and females**?
3. How do **physical activity** and **vegetable consumption** relate to **obesity level**?

---

## Methods (as implemented in `index.qmd`)

- **Data cleaning:** `dplyr` / `tidyverse` — BMI from height/weight, renames, dedupe, rounding, level collapsing, `write.csv` to `Cleaned_Dataset_rename.csv`
- **Visualization:** `ggplot2`, **Plotly** (interactive bar/stacked/contour plots)
- **Tests:** Chi-square tables for gender × obesity, family-history subsets, activity categories
- **Models:** **SVM** (`e1071`), **logistic regression** (binary obesity), **decision tree** (`rpart` / `rpart.plot`)
- **Other libraries used:** `caret`, `randomForest`, `xgboost`, `nnet`, `psych`, `plyr`

---

## Prerequisites

- [R](https://www.r-project.org/) (recent version)
- [RStudio](https://posit.co/download/rstudio-desktop/) (optional; open `Group_7.Rproj`)
- [Quarto](https://quarto.org/docs/get-started/)

Install R packages used in `index.qmd` (example):

```r
install.packages(c(
  "dplyr", "tidyverse", "ggplot2", "plyr", "randomForest", "caret",
  "plotly", "nnet", "psych", "rpart", "rpart.plot", "xgboost", "e1071"
))
```

---

## Build the website

From the project root (`stat-final-project-main` folder that contains `_quarto.yml`):

```bash
quarto render
```

Output goes to `docs/` (per typical Quarto website layout in this repo). To preview locally:

```bash
quarto preview
```

---

## Data paths (important for reproducibility)

`index.qmd` currently reads the **raw** CSV from a machine-specific path:

- `C:/Users/buddh/Downloads/Obesity Dataset.csv` (with `skip=46`)

and at one point reads the cleaned file from:

- `C:/Users/buddh/OneDrive/Desktop/Cleaned_Dataset_rename.csv`

For sharing or running on another computer, point these to:

- The **OpenML export** you use as raw input, or  
- The bundled **`Cleaned_Dataset_rename.csv`** in the project folder (e.g. `read_csv("Cleaned_Dataset_rename.csv")`) after you align the cleaning steps with that file.

---

## Dataset source

- **OpenML** obesity / factors dataset (see `References.qmd` for the project’s cited URL and id).

---

## Team

Graduate students, MS Data Analytics, George Mason University:

- **Sushanth Buddhala** — sbuddhal@gmu.edu · [GitHub](https://github.com/sushanthbuds)  
- **Sumanth Veluvolu** — sveluvo@gmu.edu  
- **Vivek Atchutanna** — vatchuta@gmu.edu  

---

## Project location

The Quarto project was extracted from **`stat-final-project-main.zip`** to:

`Desktop\stat-final-project-main\stat-final-project-main\`

This `ReadMe.md` lives in your **Portfolio** repo folder so you can open it from Cursor without Desktop path issues.
