#  Dog Breed Trait Analysis

**Author:** Michelle Fitos  
**Date:** May 18, 2025

This project explores how behavioral traits — specifically **intelligence** and **suspicion** — relate to **dog breed popularity**. Using breed-level trait scores and popularity rankings, the analysis combines **exploratory data visualization**, **linear regression**, and **decision tree modeling** to evaluate which characteristics predict breed preference.

🔗 **[View Final HTML Report](https://Fitosm.github.io/elte-ppk-r-course-Spring-2025/dogbreed.html)**  
---

##  Project Summary

-  **Data Source:** Tidy Tuesday dataset of dog breeds
-  **EDA:** Visualizations exploring how suspicion and intelligence relate to breed rank
-  **Models Used:**
  - Linear regression (with interaction term)
  - Decision tree (rpart)
-  **Evaluation:** Residual diagnostics, QQ plots, and RMSE comparison
-  **Findings:**
  - Suspicion negatively predicts popularity
  - Intelligence improves popularity **only when suspicion is high**
  - Tree model reveals intuitive behavioral thresholds

---

## Codebook

| Variable Name         | Type       | Description |
|----------------------|------------|-------------|
| `breed`              | Character  | Name of the dog breed from the original dataset |
| `breed_clean`        | Character  | Breed name cleaned with `clean_string()` (lowercase, no accents or punctuation) for joining and matching |
| `mean_rank`          | Numeric    | Mean popularity rank across all available years in the AKC rankings |
| `intelligence_proxy` | Numeric    | Row mean of `trainability_level`, `adaptability_level`, and `mental_stimulation_needs` from the trait dataset |
| `suspicion_proxy`    | Numeric    | Row mean of `barking_level`, `watchdog_protective_nature`, and reversed `openness_to_strangers` (i.e., `6 - openness_to_strangers`) |
| `fitos_family_dog`   | Logical    | TRUE if the cleaned breed name appears in `c("frenchbulldogs", "greatdanes", "americanstaffordshireterriers")` |
| `hungarian_breed`    | Logical    | TRUE if `breed_clean` matches any of the cleaned Hungarian keywords: `vizsla`, `puli`, `pumi`, `komondor`, or plural variants |
| `group`              | Factor     | Label assigned as: `"Fitos Family"` if `fitos_family_dog = TRUE`, `"Hungarian Breeds"` if `hungarian_breed = TRUE`, else `"All Other Breeds"` |
| `fitted`             | Numeric    | Predicted `mean_rank` from the linear regression model |
| `residuals`          | Numeric    | Difference between actual and predicted `mean_rank` values from the linear model |


---

##  Fitos Family Dog

As part of the analysis, certain breeds were grouped under `fitos_family_dog` based on the author's lived experience. Here's a proud representative of that group:

![Fitos Family Dog](half%20baked%20razzle.jpg)

---

##  Files in This Repo

- `dogbreed.rmd`: Full analysis with code and explanations  
- `dogbreed.html`: Final knitted HTML report  
- `README.md`: Project summary (this file)  
- `half baked razzle.jpg`: Image of the current Fitos family dog