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
   - unseen_data.csv                # Sample 5% of the full cleaned dataset using stratified sampling proportional to the target variable
   - code.ipynb                     # Main notebook for EDA, preprocessing, training, and evaluatioㅜ
   - leaderboard.csv                # Leaderboard results on the test set
   - README.md                      # Project documentation and reproduction guide
   - requirements.txt               # Optional dependency list
   - ag_models/ directory committed google drive file
   - [https://drive.google.com/drive/folders/16qtP90MiKszh4FMkFafQ_N4DPx7I-XlV?usp=drive_link]

4. Running the Training Script
   - load the raw dataset
   - preprocess the data
   - create stratified train/test splits based on readmitted
   - train the AutoGluon model
   - evaluate the model on the hold-out test set
   - save the trained artifacts to ag_models/, save leaderboard results to outputs/leaderboard.csv.
   - If using the notebook instead, open: jupyter notebook notebooks/code.ipynb
and run all cells in order.

5. Running Inferencing
   
   from autogluon.tabular import TabularPredictor
   import pandas as pd

   predictor = TabularPredictor.load("ag_models/")
   unseen_data = pd.read_csv("unseen_data.csv")
   predictions = predictor.predict(unseen_data)

   predictions

6. Model Performance
   The best model: WeightedEnsemble_L3
   score_test : 0.592983
   score_val: 587033
   eval_metric: accuracy

   Test Evaluation:
   accuracy: 0.5929832477861131
   f1 score: 0.3878781217904787
   
7. Dependencies
   - Python version: 3.12
   - Pandas version: 2.3.3
   - Numpy version: 2.1.3
   - Scikit-learn version: 1.7.2
   - Seaborn version: 0.13.2
   - Matplotlib version: 3.10.8
   - AutoGluon version: 1.5.0
