# Movie Success Prediction Using Machine Learning

This repository contains a comprehensive project that gathers, processes, analyzes, and models movie data in order to predict the success of movies. The project leverages data from multiple sources (including the Flixpatrol API and web scraping of movie budgets) and uses advanced data processing and machine learning techniques to build and optimize predictive models.

## Table of Contents
- Overview
- Data Requirements Documentation
- Data Collection Process
- Data Understanding & Exploratory Analysis
- Data Preparation & Cleaning
- Data Preprocessing & Feature Engineering
- Modeling & Evaluation
- Model Optimization and Deployment
- Additional Scripts
  - Web Scraping Movie Data
  - Data Collection & Processing with Flixpatrol API
- Requirements & Installation
- Usage
- License

## Overview
This project aims to predict the success of movies based on a variety of features including production budget, release date, cast and director metrics, genre information, and other metadata. The workflow involves:

- **Data Documentation:** Outlining data requirements and ethical considerations.
- **Data Collection:** Using both web scraping and the Flixpatrol API to gather movie data.
- **Data Preparation & Cleaning:** Handling missing values and merging multiple datasets.
- **Feature Engineering:** Creating enhanced metrics (e.g., cast/director influence, seasonal genre popularity, and a genre–month interaction score).
- **Modeling:** Testing several models (Logistic Regression, SVM, Random Forest, Gradient Boosting) and optimizing hyperparameters using RandomizedSearchCV.
- **Deployment:** Saving the final model using Pickle for later use in a presentation or production environment.

## Data Requirements Documentation
The project documentation includes a detailed explanation of the data needs, sources, and ethical considerations. The raw data comes from two main sources:

- **Movie Budget & Box Office Data:** Obtained via web scraping from The Numbers and stored in CSV format.
- **Flixpatrol API Data:** Fetched from the Flixpatrol API with your provided API key.

All data processing adheres to data protection and ethical guidelines.

## Data Collection Process
Data collection was performed using multiple methods:

- **API Requests:** Custom Python scripts (using the `requests` library) fetch movie and TV data from the Flixpatrol API.
- **Web Scraping:** The `BeautifulSoup` library is used to extract movie budget and revenue data from websites.
- **CSV Storage:** All data is stored in CSV files (e.g., `boxoffice.csv`, `movies.csv`, `output.csv`, `collected_movie_data.csv`) for further processing.

## Data Understanding & Exploratory Analysis
After collecting the data, the next step was to understand the datasets and perform exploratory analysis. This includes:

- **Merging Datasets:** Combining different CSV files into a master dataset.
- **Visualizing Distributions:** Histograms of box office revenues, production budgets, ratings, etc.
- **Handling Duplicates:** Removing duplicate movie entries.
- **Extracting Date Features:** Converting premiere dates into datetime objects and extracting month and year.

## Data Preparation & Cleaning
The dataset underwent extensive cleaning and preparation:

- **Dropping Duplicates:** Duplicate movies based on film IDs were removed.
- **Handling Missing Values:** Missing data in features like Production Budget, country_id, genre_id, keyword_id, and company_id were addressed using strategies such as:
  - Median imputation for rating columns.
  - Mode imputation for categorical features.
  - Dropping rows with missing values when imputation would introduce bias.
- **Renaming Columns:** Standardizing column names for consistency.
- **KNN Imputation:** Tested for Production Budget but ultimately complete cases were chosen to preserve distribution integrity.

## Data Preprocessing & Feature Engineering
### Feature Engineering Highlights

#### Categorizing Premiere Month:
Premiere months were categorized as:

- **High Revenue:** May, June, November, December
- **Moderate Revenue:** April, July, October
- **Low Revenue:** January, August, September

#### Seasonal Genre Popularity:
The project calculates the historical popularity of genres per season (Winter, Spring, Summer, Fall) and creates new features accordingly.

#### Enhanced Cast and Director Metrics:
These metrics combine frequency and average box office earnings for each cast member and director to quantify their influence on movie success.

#### Genre–Month Score:
A scoring system based on the interaction between movie genres and premiere month categories is implemented to capture seasonality effects.

## Modeling & Evaluation
The modeling phase involved testing several machine learning models including:

- **Logistic Regression**
- **Support Vector Machines (SVM)**
- **Random Forest Classifier**
- **Gradient Boosting Classifier**

## Model Optimization and Deployment
Hyperparameter tuning was performed using `RandomizedSearchCV` to fine-tune the Random Forest parameters. The optimized model was then saved using `pickle` for later use in predictions.

## Additional Scripts
### Web Scraping Movie Data
A Python script is provided to scrape movie data from a website and write it to a CSV file. It uses:

- `requests` for HTTP requests
- `BeautifulSoup` for HTML parsing
- `csv` module for data storage

### Data Collection & Processing with Flixpatrol API
Two scripts are provided:

1. **Fetching Movie Data and Writing to CSV**
2. **Comprehensive Data Collection and Aggregation**

## Requirements & Installation
Make sure you have Python 3.8+ installed. Install the required libraries using pip:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn requests beautifulsoup4 joblib
```

## Usage
### Data Collection:
Run the web scraping scripts or API data collection scripts as needed.

```bash
python your_flixpatrol_data_script.py
python your_web_scraping_script.py
```

### Data Preparation and Modeling:
Execute the main Jupyter Notebook or Python scripts to perform data cleaning, feature engineering, model training, and evaluation.

### Model Deployment:
Load the saved model (`best_random_forest_model.pkl`) in your application to predict movie success based on user-input features.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

This README provides a comprehensive overview of the movie success prediction project. For further details, refer to the individual Python scripts and Jupyter notebooks included in the repository.
