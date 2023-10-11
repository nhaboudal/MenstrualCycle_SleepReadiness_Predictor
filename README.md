# MenstrualCycle_SleepReadiness_Predictor


This project aims to predict sleep and readiness scores based on menstrual cycle phases and daily temperature. 
The goal is to provide actionable insights for individuals to plan their activities and rest periods more effectively.

## Dataset

The data consists of:
- Menstrual cycle phases (before and after ovulation). [Interpreted from Natrual Cycles ]
- Daily temperature readings.  [Extracted from Natrual Cycles ]
- Daily readiness scores.  [Extracted from Oura Ring ]
- Daily sleep scores. [Extracted from Oura Ring ]

## Jupyter Notebooks and Descriptions

1. **Oura_Extract_Data.ipynb**
   - **Purpose:** Extracts data from the source, preparing it for further analysis.

2. **Oura_Interpolate_Data.ipynb**
   - **Purpose:** Interpolates missing scores and temperatures to ensure continuity in the dataset.

3. **Oura_Visualize_Data.ipynb**
   - **Purpose:** Provides visualizations of scores against menstrual cycle phases and cycles, aiding in preliminary data analysis.

4. **Oura_ttest_Data.ipynb**
   - **Purpose:** Applies t-test and ANOVA to determine if there are significant differences in scores across menstrual cycle phases.

5. **Oura_TrainTest_Model.ipynb**
   - **Purpose:** Trains models to predict sleep and readiness scores and tests their performance.

## Requirements

- Ensure you have Jupyter Notebook or Jupyter Lab installed.
- Required Python libraries: pandas, numpy, matplotlib, seaborn, statsmodels (or any other libraries used in the notebooks).

## Getting Started

1. Clone the repository or download the project files.
2. Navigate to the project directory.
3. Start Jupyter by running `jupyter notebook` or `jupyter lab` in the terminal or command prompt.
4. Open the desired notebook and execute the cells.

