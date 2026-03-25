# Compositional Data Analysis (CODA) in Geoscience

## Introduction

Compositional data—where variables represent parts of a whole (e.g., percentages, proportions, chemical concentrations summing to a constant)—violate the assumptions of classical statistics. The closure problem introduces spurious correlations and invalidates standard methods. This project introduces the principles of Compositional Data Analysis (CODA) using two case studies: European food consumption and groundwater chemistry from California’s Central Valley.

## Problem Statement

We need to demonstrate that classical statistical analysis (mean, variance, correlation) can be misleading for compositional data. By applying CODA methods (log‑ratio transformations, variation arrays, biplots, and clustering), we reveal meaningful relationships that are hidden in raw compositions.

## Questions

1. How do classical summary statistics differ from CODA‑based summaries?
2. What does the variation array tell us about important log‑ratios?
3. Can ternary diagrams and biplots effectively show relationships between components?
4. Does clustering on raw data versus CLR‑transformed data produce different results?
5. How do CODA results inform the geochemical understanding of redox processes in groundwater?

## Objectives

- Perform classical EDA on both datasets and note its limitations.
- Apply CODA methods using CoDaPack and Python to extract meaningful log‑ratios.
- Create ternary diagrams and biplots to visualize compositions.
- Compare k‑means clustering results on raw vs. CLR‑transformed data.
- Map the spatial distribution of important log‑ratios in the Central Valley.

## Aim

To equip the geoscientist with the ability to correctly handle compositional data, avoiding false correlations and enabling robust interpretation.

## Data Description

### Nutrition Data
- **File**: `Nutrition_data.csv`
- **Description**: Percentages of various food groups consumed in European countries (1980s). Variables include cereals, fish, meat, vegetables, etc.
- **Source**: Provided in course materials.

### Central Valley Groundwater
- **File**: `DatapointsCentralValleyGroundwater-Jan2019.csv`
- **Description**: Chemical analyses of groundwater samples from the Central Valley, California. Variables include major ions (Ca, Mg, Na, etc.) and trace elements (Cr, U, Fe, Mn, SO₄, etc.).
- **Source**: Public data (California State Water Resources Control Board).

## Methodology

### Part 1: Nutrition Data
1. **Classical EDA** (without CODA)  
   - Compute mean, standard deviation, and correlation matrix.
2. **CODA EDA** (with CoDaPack)  
   - Variation array to identify important log‑ratios.
   - Ternary diagrams for selected subcompositions (e.g., Nuts, White Meat, Fish).
   - Biplot of centered log‑ratio (clr) coordinates.
3. **Clustering**  
   - K‑means clustering on raw data vs. CLR‑transformed data.
   - Compare cluster assignments with geographic groups (Mediterranean, Eastern Europe, North‑Western Europe).

### Part 2: Central Valley Groundwater
1. **Classical vs. CODA summaries**  
   - Variation array to pinpoint key log‑ratios (e.g., Fe/Mn, Cr/U).
2. **Visualization**  
   - Ternary diagrams and biplots for selected elements.
3. **Spatial analysis**  
   - Map important log‑ratios using kriging.
4. **Clustering**  
   - Cluster samples using raw values and CLR‑transformed values, all elements vs. selected elements.

## Mathematical Framework

### The Closure Problem
Compositional data lie in the simplex:
\[
\mathcal{S}^D = \left\{ \mathbf{x} = (x_1,\dots,x_D) \mid x_i > 0, \sum_{i=1}^D x_i = \kappa \right\}
\]
Classical Euclidean geometry is invalid in the simplex.

### Log‑ratio Transformations
- **Additive log‑ratio (alr)**: \( \text{alr}(\mathbf{x}) = \left( \ln\frac{x_1}{x_D}, \dots, \ln\frac{x_{D-1}}{x_D} \right) \)
- **Centered log‑ratio (clr)**: \( \text{clr}(\mathbf{x}) = \left( \ln\frac{x_1}{g(\mathbf{x})}, \dots, \ln\frac{x_D}{g(\mathbf{x})} \right) \), where \( g(\mathbf{x}) \) is the geometric mean.
- **Isometric log‑ratio (ilr)**: Orthonormal coordinates on the simplex.

### Variation Array
A matrix of log‑ratio variances:
\[
v_{ij} = \mathrm{Var}\left( \ln\frac{x_i}{x_j} \right)
\]
High values indicate that the ratio is highly variable and thus potentially informative.

### Compositional Biplot
A biplot of clr‑transformed data approximates the covariance structure of log‑ratios. Vectors represent variables; their angles approximate correlations between log‑ratios.

## Tools

- **CoDaPack** ([http://ima.udg.edu/codapack/](http://ima.udg.edu/codapack/)) – for variation arrays, ternary diagrams, and biplots.
- **Python** (pandas, numpy, matplotlib, scikit‑learn, geopandas) – for complementary analysis, clustering, and mapping.
- **Google Colab** – notebooks provided.

## Repository Structure
