# R Exploratory Factor Analysis — Morphometric Determinants

An R script for exploratory factor analysis (EFA) of morphometric, bathymetric
and geological factors, using the psych package. The workflow estimates the
correlation structure among the observed variables and extracts a small number
of latent factors that explain their shared variance, comparing several
extraction methods and estimating the number of factors to retain. The data
describe environmental determinants of the Mariana Trench.

## Related publication

This script (exploratory_factor_analysis_psych.R) produced figures in:

Lemenkova, P. Factor Analysis by R Programming to Assess Variability Among
Environmental Determinants of the Mariana Trench. Turkish Journal of Maritime
and Marine Sciences 2018, 4(2), 146-155.

- arXiv:      https://arxiv.org/abs/1812.00989 (physics.geo-ph)
- arXiv DOI:  https://doi.org/10.48550/arXiv.1812.00989
- EarthArXiv: https://eartharxiv.org/es9ka/
- HAL:        https://hal.archives-ouvertes.fr/hal-01948977
- Zenodo:     https://zenodo.org/record/2094101
- SSRN:       https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3296819
- figshare:   https://doi.org/10.6084/m9.figshare.7358207
- Journal:    http://edergi.odu.edu.tr/ojs/index.php/JMMS/article/view/426 (ISSN 2564-7016)

## Script

### exploratory_factor_analysis_psych.R
- Reads the factor table (MorphologyFA.csv) and removes incomplete records
  (na.omit with a per-row missing-value check).
- Builds the pairwise correlation matrix (cor) as input to factor extraction.
- Fits factor models with psych::fa (2 factors, oblique oblimin rotation,
  regression factor scores, communalities from squared multiple correlations)
  under three extraction methods:
  - principal-axis factoring (fm = "pa"),
  - weighted least squares (fm = "wls"),
  - alpha factoring (fm = "alpha").
- Determines the number of factors to retain by Horn's parallel analysis
  (fa.parallel), comparing observed eigenvalues against those from random data.
- Runs item cluster analysis (iclust, the ICLUST algorithm) on the correlation
  matrix.
- Estimates hierarchical and bifactor solutions with omega (McDonald's omega /
  Schmid-Leiman), including a bifactor variant.
- Plots factor loadings and factor diagrams (plot, fa.plot).

## Methods and algorithms

- Exploratory factor analysis with multiple extraction methods (principal axis,
  weighted least squares, alpha factoring).
- Oblique (oblimin) factor rotation and regression factor scores.
- Correlation-matrix estimation and squared-multiple-correlation communalities.
- Factor-retention decision by Horn parallel analysis (eigenvalue comparison
  against random data).
- Item cluster analysis (ICLUST).
- Hierarchical and bifactor modelling via omega (Schmid-Leiman transformation).

## Data

- MorphologyFA.csv: morphometric, bathymetric and geological factors sampled
  along the Mariana Trench (variables in columns, observations in rows).

## Requirements

- R (>= 3.5)
- Packages: psych (main); factoextra, FactoMineR (optional)

Install with:

    install.packages(c("psych", "factoextra", "FactoMineR"))

## Usage

Place MorphologyFA.csv in the working directory and run:

    Rscript exploratory_factor_analysis_psych.R

The script prints factor solutions to the console and draws the loading and
diagram plots to the active graphics device.

## Author and citation

Polina Lemenkova
ORCID: https://orcid.org/0000-0002-5759-1089

If you use this script, please cite:

Lemenkova, P. Factor Analysis by R Programming to Assess Variability Among
Environmental Determinants of the Mariana Trench. Turkish Journal of Maritime
and Marine Sciences 2018, 4(2), 146-155. arXiv:1812.00989.
https://doi.org/10.48550/arXiv.1812.00989

## License

See the LICENSE file in this repository.
