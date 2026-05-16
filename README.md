# Student Exam Performance Predictor

An end-to-end machine learning web application that predicts a student's Mathematics exam score based on demographic and academic background inputs. Built to understand the full ML lifecycle — from raw data to a served prediction.

---

## What It Does

Takes in student information (gender, ethnicity, parental education level, lunch type, test preparation course, reading score, writing score) and predicts their expected Math score using a trained regression model.

---

## How It Works

The project is structured as a modular ML pipeline:

- **Data Ingestion** — Reads raw CSV data, performs an 80/20 train-test split, and saves artifacts
- **Data Transformation** — Applies median imputation and standard scaling for numerical features; mode imputation, one-hot encoding, and scaling for categorical features
- **Model Training** — Trains and evaluates 7 regression algorithms simultaneously using GridSearchCV for hyperparameter tuning; automatically selects the best-performing model
- **Prediction Pipeline** — Loads serialized model and preprocessor at inference time to serve real-time predictions
- **Web Interface** — A Flask app that takes user input via a form and returns the predicted score

Best model achieved an **R² of ~0.88** on the test set.

---

## Tech Stack

| Layer | Tools |
|---|---|
| ML & Data | Python, Scikit-learn, Pandas, NumPy |
| Web | Flask, Jinja2 |
| Experiment | Jupyter Notebook |
| Deployment Config | AWS Elastic Beanstalk, Azure App Service, GitHub Actions |

---

## Project Structure

```
student-exam-performance-predictor/
├── app.py                  # Flask web application
├── setup.py                # Package setup
├── requirements.txt
├── artifacts/              # Generated model and preprocessor files
├── notebook/               # EDA and model training notebooks
├── src/
│   ├── components/         # Data ingestion, transformation, model training
│   ├── pipeline/           # Inference pipeline
│   ├── logger.py
│   ├── exception.py
│   └── utils.py
└── templates/              # HTML templates
```

---

## Running Locally

```bash
# Clone the repo
git clone https://github.com/arctic-pole/student-exam-performance-predictor.git
cd student-exam-performance-predictor

# Install dependencies
pip install -r requirements.txt

# Train the model (generates artifacts)
python src/components/data_ingestion.py

# Run the Flask app
python app.py
```

Visit `http://localhost:5000` in your browser.

---

## What I Learned

- Structuring a real ML project beyond a notebook — modular components, logging, custom exceptions
- Building and comparing multiple models programmatically with GridSearchCV
- Serving ML predictions through a Flask web interface
- Configuring CI/CD pipelines for cloud deployment (AWS Elastic Beanstalk + Azure App Service)

---

## Dataset

[Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams) — 1,000 student records from Kaggle.
