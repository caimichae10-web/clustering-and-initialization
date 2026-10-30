# Clustering and Initialization: K-means vs K-means++

Statistical Methods for Machine Learning — University of Milan  
Assignment 5: Clustering and Initialization

## Overview

This project empirically compares **uniform random initialization** and **K-means++ (D² seeding)** for Lloyd's K-means clustering. Both initialization methods and the Lloyd update procedure are implemented **from scratch using NumPy**; scikit-learn is used only to generate the synthetic dataset.

## Datasets

- **Synthetic:** 600 two-dimensional samples generated with `make_blobs`, four well-separated centers, `cluster_std=1.3`, `random_state=123`; `k=4`.
- **MNIST:** a fixed random subset of 5,000 images sampled without replacement from the 60,000-image training partition (`seed=42`). Images are flattened to 784 features and normalized to `[0,1]`; `k=10`. Labels are used for illustration only, not for clustering.

MNIST is downloaded automatically into the local `data/` directory when the notebook is run. The dataset itself is **not** included in this repository.

## Experimental design

Each initialization strategy is tested with 30 different seeds (`0` through `29`) on each dataset. The notebook reports the mean, population standard deviation, median, minimum and maximum of final inertia, and plots inertia distributions. A synthetic-dataset diagnostic counts runs within 5% of the lowest observed inertia.

| Dataset | Mean inertia reduction with K-means++ | Standard-deviation reduction |
|---|---:|---:|
| Synthetic | 75.75% | 68.49% |
| MNIST | 0.10% | 35.31% |

These are descriptive results from the specified 30-run experiments. The observed best inertia is not guaranteed to be the global optimum.

## Files

- `kmeans_assignment.ipynb` — complete implementation and experimental analysis
- `Clustering_and_Initialization.pdf` — report (**download and add the latest PDF from Overleaf**)
- `figures/` — figures from the report
- `requirements.txt` — Python dependencies
- `.gitignore` — excludes datasets, virtual environments and generated temporary files

## How to reproduce

1. Install Python and create a virtual environment (recommended).
2. Install dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. Start Jupyter or open `kmeans_assignment.ipynb` in VS Code using the virtual environment's Python kernel.
4. Execute all cells **from the repository's root directory**. The MNIST cell requires an Internet connection on first execution. Figures are written to the local `results/` directory.

The notebook intentionally contains no precomputed outputs; running it reproduces the results. Small numerical differences may arise across environments.

## References

- Arthur, D., & Vassilvitskii, S. (2007). *k-means++: The Advantages of Careful Seeding.*
- LeCun, Y., Bottou, L., Bengio, Y., & Haffner, P. (1998). *Gradient-Based Learning Applied to Document Recognition.*
- Pedregosa, F., et al. (2011). *Scikit-learn: Machine Learning in Python.*
