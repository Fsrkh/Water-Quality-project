# River water quality across seasons and sections

How do oxygen and nitrate concentrations change from the headwaters to the river mouth? This notebook analyzes 900 samples across five river sections and four seasons, with 45 samples in each section–season combination.

## Findings

- Mean nitrate was 0.871 mg/L higher in spring than in autumn. Averaged equally over all four seasons, mean nitrate increased at every successive section and was 6.116 mg/L higher at the mouth than at the headwaters.
- For oxygen, the 95% confidence interval for the spring-minus-autumn mean difference ranged from −0.010 to 0.314 mg/L. The data are compatible with a small difference in either direction.

## Run the notebook

Open `test.ipynb` in Google Colab, choose **Runtime → Run all**, and upload the original `waterquality.csv` when prompted.

For a local run, place both files in the same directory and run these commands there. Open `test.ipynb` in JupyterLab and run the cells in order.

```bash
python -m pip install jupyterlab numpy pandas matplotlib seaborn statsmodels patsy
python -m jupyterlab
```

## Input data

The CSV uses a semicolon delimiter and a decimal point. Column names and category labels are case-sensitive.

| Column | Expected content |
| --- | --- |
| `ID` | Sample identifier |
| `river_section` | `A1_headwaters`, `A2_upper_course`, `A3_middle_course`, `A4_lower_course`, or `A5_mouth` |
| `saison` | `spring`, `summer`, `autumn`, or `winter` |
| `oxygen_mgL` | Oxygen concentration in mg/L |
| `nitrate_mgL` | Nitrate concentration in mg/L |

## Analysis and outputs

The seasonal comparison gives each river section equal weight. The spatial comparison gives each season equal weight and applies Holm adjustment to the ten pairwise section comparisons for each substance. Both models use HC3 robust standard errors. Confidence intervals assume independent observations. The dataset lacks sampling dates and site identifiers, which limits assessment of correlation from repeated visits.

Running the notebook displays the summary tables and saves two figures in the working directory.

| File | Figure |
| --- | --- |
| `figure_1_water_quality.png` | Oxygen and nitrate distributions by section and season |
| `figure_2_seasonal_differences.png` | Spring-minus-autumn mean differences with 95% confidence intervals |
