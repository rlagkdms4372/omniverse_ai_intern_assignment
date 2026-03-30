# omniverse_ai_intern_assignment
Omniverse AI Internship Assignment

1. Project Overview
   - This dataset is a real-world clinical dataset comprising diabetic patient hospital encounters recorded between 1999 and 2008. The target variable is readmitted, which indicates whether a patient was readmitted within 30 days, after 30 days, or not readmitted.
   - diabetic_data.csv
     - consis of 101,766 rows × 50 cols
     - Primary dataset containing clinical encounter records for diabetic patients.
   -  The modeling approach is based on AutoGluon TabularPredictor, which automatically trains and ensembles multiple tabular models to optimize predictive performance.

2. Envirionment Setup
   - uv venv --python 3.12
   - source .venv/bin/activate      # Linux / macOS
   - .venv\Scripts\activate        # Windows
   - uv pip install -r requirements.txt

3. Repository Structure
project-root/
│
├── data/
│   ├── diabetic_data.csv              # Main dataset
│   ├── IDS_mapping.csv                # Mapping file for diagnosis/admission/source codes
│   └── unseen_data.csv                # Sample 5% of the full cleaned dataset using stratified sampling proportional to the target variable
│
├── notebooks/
│   └── code.ipynb                     # Main notebook for EDA, preprocessing, training, and evaluatioㅜ
│
├── outputs/
│   └── leaderboard.csv                # Leaderboard results on the test set
│
├── README.md                          # Project documentation and reproduction guide
└── requirements.txt                   # Optional dependency list

4. Running the Training Script
   - load the raw dataset
   - preprocess the data
   - create stratified train/test splits based on readmitted
   - train the AutoGluon model
   - evaluate the model on the hold-out test set
   - save the trained artifacts to ag_models/, save leaderboard results to outputs/leaderboard.csv.

If using the notebook instead, open: jupyter notebook notebooks/code.ipynb
and run all cells in order.

5. Running Inferencing
   
import pandas as pd
unseed_data = pd.read_csv("unseed_data.csv")

leaderboard = predictor.leaderboard(unseed_data, silent=False)
leaderboard.to_csv('leaderboard_unseen.csv', index=False)

6. Model Performance

7. Dependencies
   - Python version: 3.12
   - Pandas version: 2.3.3
   - Numpy version: 2.1.3
   - Scikit-learn version: 1.7.2
   - Seaborn version: 0.13.2
   - Matplotlib version: 3.10.8
   - AutoGluon version: 1.5.0
