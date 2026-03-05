# Course 4 Project: Fashion Forward Forecasting

Build a predictive model using customer reviews. The model analyzes review text, customer's age, product category, and other metadata to predict whether a customer will recommend a product.

## Project Overview

This project develops a machine learning model that predicts customer recommendations based on product review data. By using natural language processing (NLP) tools, we aim to understand what drives customer recommendations for a product and predict customer behavior based on product attributes and customer review comments.

## Structure

├── data/

│   └── review.csv              # Raw dataset containing customer reviews and metadata

├── dsnd_pipeline_project.ipynb # Main Jupyter notebook containing:

│   ├── Data Exploration
│   ├── Building Pipeline
│   ├── Training Pipeline
│   └── Fine-Tuning Pipeline

├── requirements.txt            # Python dependencies required for the project

└── README.md                   # Project documentation

## Data Exploration

Several visualizations were developed to understand the data.
- **Customer Age**: The cusomters who left the comments are between age 20 to 80. Most cusomters are between 30 to 50. The customer's age is an important feature to be considered.
- **Recommendataion**: The positive recommendations are much more than negative recommendations. This trend suggests that customers with positive experience tend to leave a comment for the product.
- **Product Class**: Dresses, Knits, and Blouses are top 3 products receiving reviews.
- **Title**: Title usually indicate the core information for the comments. The top 5 titles are related to 'love' and 'beautiful', suggesting positive feedbacks.

## Feature Pipelines

- **Numerical feature pipeline**: The missing value is filled with mean value. All numbers are calibrated to same scale using min-max-scaler.

- **Categorical feature pipeline**: All categorical values are converted to integer labels. The missing value is filled with most frequent value. One hot encoder converted each category to binary values.

- **Text feature pipeline**: Create a pipeline to count the number of space, '!', and '?' characters in the text. The space count indicate the length of the comments. The '!' and '?' usually represent strong feelings or questions from customers.

- **Customer feature**: Natural language processing of customer reviews and feature extraction using spaCy (preprocessing and linquistic feature) and TF-IDF (convert to numerical vector).

## Model Training

- Random Forest Classifier with default hyperparameter setting was used to train the model.
- Model accuracy is 0.845 as validated using testing dataset.

## Model Fine-Tuning

- Random Forest Classifier hyperparameters were randomly combined.
- Instead of cross-validation, I set up 8/2 split of training/test dataset and run each combination once. This is because it took too long to run multiple times.
- The best combination of hyperparameters were selected - n_estimators (decision tree) = 100, max_features = 200. 
- The accuracy is improved slightly to 0.850.
