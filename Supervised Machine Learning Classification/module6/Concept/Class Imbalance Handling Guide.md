# Class Imbalance Handling Guide

## 1. Resampling Methods
- **Upsampling**: Increase minority class representation  
- **Downsampling**: Reduce majority class samples  

## 2. Critical Timing
### Correct Workflow:
1. Split raw data → train/test sets
2. Resample **only** training data
3. Keep test set original distribution

### Avoid:
- Resampling before splitting
- Modifying test set data

## 3. Evaluation Priorities
### Core Metrics:
| Metric Type       | Recommended Choices      |
|-------------------|--------------------------|
| Basic Assessment  | Precision, Recall, F1    |
| Imbalanced Data   | AUC-ROC, G-Mean          |
| Visual Analysis   | Confusion Matrix, PR Curve |

### Advanced Techniques:
- Stratified cross-validation
- Learning curve comparison
- Feature distribution monitoring

