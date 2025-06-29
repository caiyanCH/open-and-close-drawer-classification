# Open and Close Drawer Classification

This repository contains code and data for classifying robot manipulation actions (open vs. close drawer) based on the PhysicalAI Robotics Manipulation in the Kitchen dataset. We trained and evaluated classical machine learning models using episode-level statistical features derived from robot hand trajectories and object state data.

## Project Structure
├── data/ # Sample processed CSVs (open/close drawer)
├── notebooks/ # Jupyter notebooks for analysis and visualization
├── src/ # Python scripts for feature extraction and model training
├── requirements.txt # Python dependencies
└── README.md # Project description


## Task Description

The classification task distinguishes between **open drawer** and **close drawer** actions using robot demonstration data. Models were trained using episodes from the drawer task and tested on both seen (drawer) and unseen tasks (e.g., fridge, cabinet).

## Features

We computed statistical features at the episode level:
- **Action variables**: mean, std, range, slope, etc. (e.g., `action_21` to `action_33`)
- **Object state**: drawer position (`obs_state_12`), including start/end values, slope, etc.
- **Episode metadata**: total frames, task label

## Models

We evaluated five classical models:
- Logistic Regression
- Lasso Regression
- Support Vector Machine (SVM)
- Random Forest
- Gradient Boosting

## Results

- **Drawer task**: All models achieved perfect scores (100% Accuracy / Precision / Recall / F1 / AUC).
- **Unseen tasks**: High generalization with 96–100% performance across metrics.

## Generalization Insights

Features like `obs_state_12_start_value` and `action_30_range` captured shared motion patterns and object states across tasks, enabling robust cross-task performance.

## Limitations

- No temporal modeling (static episode-level features)
- Handcrafted feature design
- Experiments conducted in controlled environments

## Future Work

- Introduce temporal models (e.g., RNNs, Transformers)
- Learn representations directly from raw signals (e.g., via autoencoders)
- Evaluate in noisy or real-world robot settings

## Dataset Links

- [Original Dataset (PhysicalAI)](https://huggingface.co/datasets/nvidia/PhysicalAI-Robotics-Manipulation-Kitchen)
- [Open/Close Drawer Processed CSV](https://huggingface.co/datasets/caiyan123/open-close-drawer-csv)
- [Merged Other Tasks CSV](https://huggingface.co/datasets/caiyan123/merged_other_task)

## License

For academic use only. Please cite the dataset and code source where appropriate.
