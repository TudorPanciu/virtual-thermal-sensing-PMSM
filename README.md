# Virtual Thermal Sensing for Permanent Magnet Synchronous Motors

Machine learning-based temperature prediction for permanent magnet synchronous motors, investigating various modelling approaches, sparse sampling viability and deployment feasibility for embedded systems.

## Key Results

- Linear regression achieves near-perfect permanent magnet temperature prediction accuracy; neural networks extend capability to comprehensive multi-sensor thermal monitoring.
- Accuracy remains reliable when training models at sparser sampling intervals, revealing slight limitations in well defined edge cases.
- Error analysis and feature ablation studies revealed that prediction accuracy degradation stems from fundamental sampling limitations rather than modelling deficiencies.
- Deployment feasibility analysis proved that our models satisfy the computational requirements of representative automotive and industrial scenarios, acknowledging application-specific limitations.
- Development opportunities for improving model robustness, performance and system level integration are presented among the conclusions.

## Problem Context

Direct permanent magnet temperature measurement on rotating motor components requires slip rings or wireless telemetry—expensive, mechanically complex solutions that introduce failure modes. While ML models achieve >99% accuracy from operational parameters at 2 Hz sampling, embedded motor controllers face computational and power constraints making high-frequency sensing impractical.

**This investigation addresses**: Can sampling frequency be reduced 2-120× while maintaining thermal prediction accuracy? Can virtual sensing extend beyond single-sensor substitution to comprehensive multi-sensor thermal monitoring?

## Approach

**Phase 1: Problem Formulation & Data Understanding**
- PMSM thermal management context and measurement constraints
- Paderborn University dataset analysis (1.3M measurements, 2 Hz sampling)
- Investigation scope: from single-sensor substitution to multi-sensor virtual sensing at sparse sampling intervals

**Phase 2: Methodology**
- Baseline linear regression (0.5s sampling, physics-informed features)
- Sparse sampling characterization (1s-60s intervals)
- XGBoost validation (gradient boosting used for benchmarking)
- Multi-output neural network grid search (architecture + regularization, 75 configurations)
- Feature ablation and error analysis for practical validation
- Deployment feasibility assessment (memory footprint, inference time, safety margins)

**Phase 3: Conclusions**
- Virtual sensing viability confirmation (single and multi-sensor)
- Model behavior validation (error patterns, feature importance)
- Deployment feasibility for automotive/industrial applications
- Limitations and future work (robustness validation, model optimization, system-level integration)

## Repository Structure

```
├── Virtual Thermal Sensing for Permanent Magnet...ipynb    # Complete analysis
├── requirements.txt                                        # Python dependencies
├── models/                                                 # Trained models for deployment feasibility analysis
├── nn_test_results.csv                                     # Test set evaluation data
├── nn_grid_search_results.csv                              # Grid search results
├── computational_cost_analysis.csv                         # Memory footprint and inference time metrics
└── README.md
```

## View the Analysis

**→ [Open the complete notebook on GitHub](https://github.com/TudorPanciu/virtual-thermal-sensing-PMSM/blob/main/virtual-thermal-sensing-PMSM/Virtual%20Thermal%20Sensing%20for%20Permanent%20Magnet%20Synchronous%20Motors.ipynb)**

The notebook contains detailed methodology, results, and discussion. **GitHub's renderer allows viewing without local setup.**

## Dataset

Analysis uses the [Paderborn University PMSM Temperature Dataset](https://www.kaggle.com/datasets/wkirgsn/electric-motor-temperature) (>1.3M measurements at 2 Hz from a German OEM prototype motor across diverse driving cycles).

**To run locally:** Download the 'virtual-thermal-sensing-PMSM' folder from this repository and the dataset CSV file from the link above. Run the notebook with the CSV file inside the folder.

## Technologies

Python 3.11 • scikit-learn • XGBoost • TensorFlow/Keras • pandas • NumPy • matplotlib • seaborn


*November 2025*
