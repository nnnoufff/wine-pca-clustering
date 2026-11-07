# Clustering Before and After PCA

**Mini Project, Group 6**

Compare K-Means clustering on the original data (13 features) with K-Means on the data reduced by PCA to 2 components, and measure what PCA changes.

## Dataset

[Wine dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html) (from `sklearn`): 178 wines, 13 chemical features, from 3 grape types.

The grape type is never used for clustering. It is used only to check the results (ARI).

## What We Did

1. **Preprocessing:** checked for missing values (none) and standardized the features.
2. **K-Means before PCA:** K = 3 on all 13 features.
3. **PCA:** reduced to 2 components, which keep 55.4% of the information.
4. **K-Means after PCA:** K = 3 on the 2 components.
5. **Visualization:** before and after PCA plots on PC1 and PC2.
6. **Comparison and analysis:** Silhouette score and Adjusted Rand Index (ARI).
7. **Bonus:** different numbers of PCA components, and DBSCAN before and after PCA.

## Results

| | Silhouette | ARI (vs grape type) |
|---|---|---|
| K-Means before PCA (13 features) | 0.285 | 0.897 |
| K-Means after PCA (2 components) | 0.561 | 0.895 |

### Bonus: number of PCA components (K-Means)

| Components | 1 | 2 | 3 | 5 | 13 |
|---|---|---|---|---|---|
| ARI | 0.505 | 0.895 | 0.880 | 0.897 | 0.897 |

### Bonus: DBSCAN

| | ARI |
|---|---|
| DBSCAN before PCA (`eps=2.4`, `min_samples=5`) | 0.421 |
| DBSCAN after PCA (`eps=0.65`, `min_samples=8`) | 0.559 |

## Key Insights

- **PCA barely changed the clustering.** ARI is 0.897 before and 0.895 after, so K-Means found essentially the same groups.
- **Visualization is clearer.** The 13 features cannot be plotted, but the 3 groups are easy to see in 2 components.
- **Information was lost (about 44.6%), but it did not hurt the clustering.** The Silhouette went up (0.285 to 0.561) partly because it is measured in 2D only, so it is not a fair like-for-like gain.
- **2 components are enough.** One component loses too much (ARI 0.505). From 2 components on, the result is almost the same.
- **DBSCAN improved after PCA** (0.421 to 0.559), but K-Means is still better on this data.
- **Better approach:** K-Means after PCA gives the same quality with 2 features instead of 13, and is easy to visualize.

## How to Run

```bash
pip install pandas matplotlib scikit-learn jupyter
jupyter notebook wine_pca_clustering.ipynb
```

## Files

- `wine_pca_clustering.ipynb`: code, visualizations, explanations and final summary

## Team

Group 6
