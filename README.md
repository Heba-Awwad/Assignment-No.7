SVM model
Load dataset.CSV and detected diagnosis as the target. I label-encoded it (B -> 0, M -> 1).

Selected two features automatically by absolute correlation to the target and plotted the 2D scatter (classes shown separately).

Trained SVM (linear) and Logistic Regression on those two features and reported accuracies.

Shuffled and split the full dataset into the requested sizes (or proportional if dataset smaller): train / val / test = 400 / 100 / 69 (your file has 569 rows — exact requested split was possible).

Standardized numeric features (StandardScaler fit on training set).

Performed feature selection using correlation on the training set and selected top features.

Visualized decision boundaries (2D) for SVM with linear, RBF and polynomial kernels using the top two features.

Compared validation and testing accuracies for the three kernels.

Manually swept C and gamma (the specified ranges) and plotted validation accuracy vs C and vs gamma (RBF).

Measured training & prediction times for four scenarios:

Case 1: 10% train, kernel=linear, C=1

Case 2: 100% train, kernel=linear, C=1

Case 3: 10% train, kernel=rbf, C=1, gamma=0.01

Case 4: 100% train, kernel=rbf, C=1, gamma=0.01
(Bar chart shown.)

Explored SVM weaknesses:

Overlapping classes: I modified 10% of samples from one class to make them closer to the other class and retrained — reported validation accuracy drop.

Noisy data: I added Gaussian noise to 10% of training samples, retrained RBF SVM with the tuned hyperparameters and compared validation/test accuracies.

Files / outputs I produced

Plots: scatter of chosen features, decision boundary plots for each kernel, two grid-search plots (accuracy vs C, accuracy vs gamma), training/prediction time bar chart. (They were displayed in the run output.)

In this summary contains chosen features, 2-feature model accuracies, kernel validation/testing accuracies and grid-sweep data.

Key numbers (from this run)

Dataset shape: (569, 32)

Target column detected: diagnosis (encoded B=0, M=1)

Top features by absolute correlation (training set): concave points_worst, perimeter_worst, concave points_mean, radius_worst, perimeter_mean, ... (full ranking printed in the run)

Chosen two features for the initial 2-feature experiment: concave points_worst, perimeter_worst (automatically chosen by highest abs-correlation)

Two-feature experiment accuracies (held-out test from a small split):

SVM (linear): ~ reported in run (printed)

Logistic Regression: ~ reported in run (printed)

Kernel comparison (validation / testing) — printed in run results (linear / rbf / poly).

Grid sweep bests (simple validation sweep): best C and best gamma printed from the sweep (see run prints).

Overlap experiment: validation acc dropped (example: from 0.8900 to 0.8200 in this run).

Noisy data experiment: small decrease in validation accuracy; test accuracy in this run stayed similar (details printed).
