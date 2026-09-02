# Iris Classification

## Overview
This repository contains a simple machine‑learning pipeline for classifying Iris flower species using the classic Iris dataset. The project demonstrates an end‑to‑end workflow from data exploration and model training to model serialization and deployment as a Flask web service.

## Dataset
The dataset is the well‑known **Iris** dataset (150 samples, 4 features: sepal length, sepal width, petal length, petal width) stored in `Iris.csv`. It is used to train a classifier that predicts one of three species: *setosa*, *versicolor*, or *virginica*.

## Model
A scikit‑learn model (e.g., `LogisticRegression` or `RandomForestClassifier`) is trained in the Jupyter notebook `Analysis.ipynb`. After training, the model is serialized with `pickle` and saved as `savedmodel.sav`.

## Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/iris-classification.git
cd iris-classification

# (Optional) Create a virtual environment
python -m venv venv
# On Windows
venv\Scripts\activate
# On Unix/macOS
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

## Running the Flask API
The Flask application is defined in `deploy.py`. It exposes two routes:

- `GET /` – renders a simple HTML page (`templates/index.html`) with a form for inputting flower measurements.
- `POST /predict` – accepts the four feature values, runs the model inference, and returns the predicted species.

Start the server with:
```bash
python deploy.py
```
The API will be available at `http://127.0.0.1:5000/`.

## API Usage Example
```bash
curl -X POST -F "sepal_length=5.1" -F "sepal_width=3.5" \
     -F "petal_length=1.4" -F "petal_width=0.2" \
     http://127.0.0.1:5000/predict
```
The response is rendered in the HTML template, showing the predicted class.

## Project Structure
```
Iris/
├─ Analysis.ipynb          # Data exploration & model training
├─ Iris.csv                # Raw dataset
├─ requirements.txt        # Python dependencies
├─ savedmodel.sav          # Serialized trained model
├─ deploy.py               # Flask web service
└─ templates/
   └─ index.html          # Simple front‑end for predictions
```

## Contributing
Contributions are welcome. Please fork the repository, create a feature branch, and open a pull request. Ensure that new code follows the existing style and that tests (if added) pass.

## License
This project is licensed under the MIT License – see the `LICENSE` file for details.

## Acknowledgments
- The Iris dataset was introduced by Ronald Fisher in 1936.
- Scikit‑learn documentation and examples were instrumental in building the model.
