# Dataset Information

## Dataset: `sklearn.datasets.load_digits`

### Description
The Digits dataset is built directly into scikit-learn and requires **no download, no account, and no internet access**.

- **Samples:** 1,797
- **Features:** 64 (8×8 pixel intensity values, range 0–16)
- **Classes:** 10 (handwritten digits 0–9)
- **Feature type:** Non-negative integer pixel intensities

### Why This Dataset Was Chosen
The homogeneous kernel map (Vedaldi & Zisserman, TPAMI 2012) requires histogram-type, non-negative features. Pixel intensity distributions satisfy this requirement — each feature is a count of ink density in one pixel cell, structurally analogous to the HOG and bag-of-visual-words histograms used in the paper's original experiments.

### How to Load
```python
from sklearn.datasets import load_digits
X, y = load_digits(return_X_y=True)
```

No additional steps required.

### Preprocessing Applied
```python
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)
```

MinMaxScaler scales features to [0, 1], preserving non-negativity. This satisfies the domain requirement ℝ₊₀ of the feature map (Section 2, Eq. 1 of the paper).

### Limitations vs. Paper's Dataset
The paper's primary benchmark (Caltech-101) uses 4,200-dimensional multi-scale dense SIFT histograms across 102 object categories. Load_digits uses 64-dimensional raw pixel values across 10 digit classes — a simpler task that will produce higher baseline accuracy but smaller relative improvements from the kernel map.
