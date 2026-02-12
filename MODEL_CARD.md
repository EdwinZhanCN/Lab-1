## Kickstarter Projects Prediction

### Objective

This model is aimed to predict whether a kickstarter project will be successfully reached its founding goal: "successful" or "failed" based only on information available at the time of launch.

For use in automated edge tools that prioritize resources usage, where the cost of a "False Positive" (backing a failure) is significantly higher than a "False Negative".

### Metrics

The model was evaluated using a Time-based Split (training on older data, testing on the most recent 20% of projects) to prevent temporal leakage.

- **F1-Score** was chosen to balance precision and recall
  - **Baseline (GaussianNB)**: Achieved an F1-Score of approximately 0.60.
  - **SGD SVM**: Achieved a peak F1-Score of 0.5932 when utilizing `class_weight='balanced'`.
Figures:
Best SGD SVM Model:
<img width="396" height="130" alt="Screenshot 2026-02-12 at 11 40 37 AM" src="https://github.com/user-attachments/assets/2b1edb2e-2271-4858-ad04-52abb15c340d" />
Confusion Matrix (adopted a 10:1 cost ratio penalizing False Positives for the Best Model):
<img width="546" height="393" alt="Screenshot 2026-02-12 at 11 41 05 AM" src="https://github.com/user-attachments/assets/b86941d5-6fb0-4ebe-ba89-7366039a5b88" />

More experiment data see (https://github.com/EdwinZhanCN/Lab-1/blob/main/lab02_SGD_experiment.csv)

### Limitations
- The model is trained on a dataset ending in 2018, it may not account for modern shifts in trends
- The model cannot learn the quality of project videos, descriptions, or other important data that are significant drivers of real-world success due to limitation in data size.
