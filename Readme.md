# ⚽ EPL Matches Prediction

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange?logo=scikitlearn)
![Status](https://img.shields.io/badge/Project-Completed-success)

A machine learning project that analyzes historical English Premier League (EPL) match data to predict whether the home team will win.

The project explores data preprocessing, exploratory data analysis, feature engineering, classification models, and model evaluation using Python and Scikit-learn.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Dataset](#-dataset)
- [Methodology](#-methodology)
- [Machine Learning Models](#-machine-learning-models)
- [Model Evaluation](#-model-evaluation)
- [Technologies Used](#-technologies-used)
- [Project Structure](#-project-structure)
- [Installation and Usage](#-installation-and-usage)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

## 🎯 Project Overview

Football match outcomes are influenced by several factors, including team performance, recent form, home advantage, and historical match statistics.

This project applies supervised machine learning techniques to historical EPL match data to identify patterns associated with home-team victories.

The problem is formulated as a **binary classification task**:

| Target | Description |
|:---:|---|
| `1` | Home Team Win |
| `0` | Draw or Away Team Win |

The main objective is to investigate how historical team performance and match statistics can be used to predict football match outcomes.

## 🎯 Objectives

- Analyze historical English Premier League match data.
- Perform exploratory data analysis to understand the dataset.
- Engineer features representing recent team performance.
- Train and compare different machine learning classifiers.
- Evaluate models using multiple classification metrics.
- Experiment with predicting outcomes for upcoming fixtures.

## 📊 Dataset

The project uses historical English Premier League match data stored in:

`EPL_Match_Data_2000_2026.csv`

The dataset includes information such as:

- Home and away teams.
- Match dates and results.
- Goals scored and conceded.
- Shots and shots on target.
- Expected goals (xG), where available.
- Corners and other match statistics.
- Historical head-to-head information.

**Data preparation is particularly important:** match statistics from the game being predicted must not be used as pre-match features. Features should be derived exclusively from information available before kickoff.

## ⚙️ Methodology

### 1. Data Preprocessing

- Loaded historical match data using Pandas.
- Inspected and prepared relevant columns.
- Handled missing values.
- Converted match results into a binary classification target.

### 2. Exploratory Data Analysis (EDA)

Explored historical match statistics and investigated patterns associated with home-team victories.

### 3. Feature Engineering

Feature engineering focuses on representing team performance using historical match statistics.

**Rolling Team Statistics**

Calculated rolling averages over each team's previous three matches, including:

- Goals scored and conceded.
- Shots and shots on target.
- Expected goals (xG).
- Corners and other available match statistics.

Team history considers both home and away appearances.

Rolling calculations exclude the current match to prevent using information from the match being predicted.

**Additional Features**

- Team encoding.
- Historical head-to-head information.
- Team performance indicators.

### 4. Model Training

Two machine learning classifiers were implemented and compared:

- Random Forest Classifier.
- HistGradientBoosting Classifier.

Hyperparameter tuning was also explored to investigate model performance.

### 5. Model Evaluation

Models were evaluated using:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Balanced Accuracy.
- Confusion Matrix.

A chronological train/test split was used in the improved evaluation workflow to simulate predicting future matches using historical data.

## 🤖 Machine Learning Models

| Model | Description |
|---|---|
| Random Forest | An ensemble learning algorithm that combines multiple decision trees. |
| HistGradientBoosting | A gradient boosting algorithm that builds decision trees sequentially to improve predictive performance. |

## 📈 Model Evaluation

The following table presents the reported test-set results from the notebook.

| Metric | Random Forest | HistGradientBoosting |
|---|---:|---:|
| Accuracy | 58.98% | 56.95% |
| Balanced Accuracy | 57.15% | 55.63% |
| Precision | 58.54% | 54.00% |
| Recall | 35.56% | 40.00% |
| F1-score | 44.24% | 45.96% |

### Key Observations

- Random Forest achieved higher accuracy and balanced accuracy.
- HistGradientBoosting achieved higher recall and F1-score.
- Both models still have room for improvement, particularly in identifying actual home victories.
- Accuracy alone is not sufficient to determine the best-performing model.

These results represent an experimental evaluation and do not guarantee reliable predictions on future matches.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Scikit-learn | Model training, tuning, and evaluation |
| Jupyter Notebook | Interactive development and experimentation |

## 📁 Project Structure

```text
EPL-Matches-Prediction/
│
├── EPL-Matches-Prediction.ipynb
├── EPL_Match_Data_2000_2026.csv
└── README.md
```

## 🚀 Installation and Usage

### Prerequisites

- Python 3.9 or later.
- Jupyter Notebook or JupyterLab.

### 1. Clone the repository

```bash
git clone https://github.com/abdelwhabkamal/EPL-Matches-Prediction.git

cd EPL-Matches-Prediction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate the environment:

**Windows**

```bash
.venv\Scripts\activate
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### 4. Run the notebook

```bash
jupyter notebook
```

Open `EPL-Matches-Prediction.ipynb` and run the cells.

Make sure the dataset CSV file is available in the project directory.

## ⚠️ Limitations

This project is an educational machine learning experiment rather than a production forecasting system.

Current limitations include:

- The target combines draws and away victories into one class.
- Match outcomes are inherently uncertain.
- Factors such as injuries, suspensions, player availability, and lineups are not fully represented.
- Feature engineering must be carefully validated to prevent future information leakage.
- Model performance may vary across seasons and changes in team strength.

## 🔮 Future Improvements

- Implement three-class classification: Home Win, Draw, and Away Win.
- Introduce time-series cross-validation using `TimeSeriesSplit`.
- Experiment with additional team-form features and historical windows.
- Compare against a `DummyClassifier` baseline.
- Investigate probability calibration and log loss.
- Improve pre-match feature selection.
- Save the trained model for reuse.
- Build a prediction API using FastAPI.
- Develop an interactive interface for upcoming EPL fixtures.

## 👨‍💻 Author

**Abdelwahab Kamal**

Computer Science Graduate | Aspiring AI / Machine Learning Engineer

- GitHub: [@abdelwhabkamal](https://github.com/abdelwhabkamal)
- Repository: [EPL-Matches-Prediction](https://github.com/abdelwhabkamal/EPL-Matches-Prediction)

---

*Developed as a practical machine learning project exploring the application of data analysis and predictive modeling to football analytics.*
