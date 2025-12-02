# PersonalLearn - Team 14

**Hi!ckathon 2025 - Hi! PARIS Hackathon**  
*Strengthening Academic Engagement through AI-Driven Personalization*

## Achievements
- **Rank:** Winner of the Capgemini Best Scientific Approach Award 🏆
- **Score:** $R^2$ score of **0.79** on the hackathon's test run (2nd best score ex-aequo).
- **Model Performance:** Achieved ~$0.85$ $R^2$ on internal validation splits.

## Live Demo
**Try the PersonalLearn prototype here:** 👉 [**PersonalLearn MVP**](https://personal-lean-demo1.vercel.app/)  
*(Note: Use the demo or simply upload your own courses to see the adaptive content engine in action.)*

## Overview
**Problem Statement:** Improving student’s concentration and motivation has become a critical challenge in modern education. Digital distractions, reduced attention spans, stress, personal difficulties, and lack of confidence increasingly prevent students from staying engaged during learning activities. These issues directly affect academic performance, long-term retention, and students’ ability to organize and maintain effective study habits. In a context where teaching methods are evolving but attention span is decreasing, it is essential to develop tools that adapt to learners' cognitive capacities, personalize their study experience, and support them in staying focused and motivated.

**PersonalLearn** is an intelligent learning application designed to address this crisis. By leveraging PISA dataset metrics, we created a "Cognitive Engine" that profiles students' mental endurance and adapts educational content accordingly.

Unlike traditional "one-size-fits-all" methods, PersonalLearn:
- **Profiles** cognitive limits using PISA-derived metrics.
- **Segments** dense course materials into micro-units tailored to the user's profile.
- **Monitors** engagement to suggest timely breaks and prevent burnout.

## Team Members
- **Bogdan Gorelov**
- **Franck Ulrich Kenfack Noumedem**
- **Ivann Harold Kamdem Pouokam**
- **Ireni Tonin**
- **Nassim Arifette**
- **Noha Khairallah**

## Repository Structure

| File | Description |
|------|-------------|
| `group_14_notebook.ipynb` | **Main Codebase.** Contains data preprocessing, feature engineering, XGBoost model training, and prediction generation. |
| `scientific_approach_team14.pdf` | Detailed report on the data science methodology, feature engineering, and model architecture. |
| `business_approach_team14.pdf` | Overview of the product vision, value proposition, business model, and market strategy. |


## Scientific Approach
Our solution is built on a robust **XGBoost Regressor** model trained on over 1,7 million samples from PISA datasets (2015, 2018, 2022).

### Key Methodologies:
1.  **Rigorous Preprocessing:**
    - Removed 45+ identifier/administrative columns to prevent overfitting and bias.
    - Handled missing data by removing columns with 100% nulls in the test set.
    - Prevented data leakage by excluding item-level math scores while retaining *timing* data.
2.  **Advanced Feature Engineering (65+ New Features):**
    - **Efficiency Ratios:** `Score / (Timing + 1)` to distinguish lucky guesses from deliberate solving.
    - **Cross-Subject Interactions:** Capturing correlations between Science/Reading performance and Math ability.
    - **Behavioral Consistency:** Using standard deviation of timing to detect erratic focus vs. steady concentration.
3.  **Model Tuning:**
    - **Algorithm:** XGBoost Regressor (Histogram-based with `tree_method="hist"` for efficiency and `enable_categorical=True` for robust categorical feature handling).
    - **Sample Weighting:** Applied a weight of 0.75 to 2022 data to account for post-pandemic distribution shifts.
    - **Explainability:** SHAP analysis confirmed that "how" a student answers (timing) is a top predictor of performance.

## Business Value
PersonalLearn bridges the gap between raw content and cognitive capability.
- **For Students:** Increases retention by breaking "walls of text" into manageable micro-units.
- **For Teachers:** Provides a dashboard to view learning patterns and identify struggling students early.
- **For Institutions:** A scalable, automated tutoring support system to reduce dropout rates.

## Usage

The core logic, data preprocessing, model training, and predictions are encapsulated in the Jupyter Notebook `group_14_notebook.ipynb`.

### Dataset
The PISA dataset used in this project is available on Kaggle: [PISA MathScore Prediction Dataset](https://www.kaggle.com/datasets/kepard/pisamathscore/)

### Running the Code
1.  **Local Environment:**
    *   Ensure you have Python installed.
    *   Clone this repository.
    *   Open `group_14_notebook.ipynb` in a Jupyter-compatible environment (e.g., Jupyter Lab, VS Code with Python extension).
    *   Place the `X_train.csv`, `y_train.csv`, and `X_test.csv` files (from the Kaggle dataset) in the correct relative paths as expected by the notebook, or update the file paths within the notebook.
    *   Run all cells to execute the pipeline.

2.  **Google Colab (Recommended for ease of use):**
    *   Open `group_14_notebook.ipynb` directly in Google Colab.
    *   **Mount Google Drive:** The notebook expects the data files to be in `/content/drive/MyDrive/HiParis/`. You will need to mount your Google Drive (`from google.colab import drive; drive.mount('/content/drive')`) and place the `X_train.csv`, `y_train.csv`, and `X_test.csv` files (from the Kaggle dataset) into a folder named `HiParis` within your Google Drive's root.
    *   Run all cells. Colab will handle the environment setup and library installations.

## Context
Developed for **Hi!ckathon 2025** organized by Hi! PARIS Center (HEC Paris & IP Paris).
For more details on the challenge, visit the [Hi!ckathon website](https://www.hi-paris.fr/hickathon/).

---
*Developed with ♥️ by Team 14 for Hi!ckathon.*
