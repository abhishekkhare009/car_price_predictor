# Car Price Predictor

This repository contains code for predicting the prices of old cars based on various features such as brand, model, model year, mileage, fuel type, engine, transmission, and accident history. The prediction model is built using a Long Short-Term Memory (LSTM) neural network.

## Project Overview

The goal of this project is to train an LSTM model to predict the price of old cars using historical data. The project involves the following steps:
1. **Data Preprocessing:** Handling missing values, encoding categorical variables, and scaling features.
2. **Model Training:** Building and training an LSTM model to learn patterns from the training data.
3. **Prediction:** Using the trained model to predict car prices on a test dataset.
4. **Output:** Saving the predicted prices along with the corresponding car IDs in a CSV file.

## Data Description

### Input Data
The project uses two CSV files as input:
- `train.csv`: Contains the training data with car features and their corresponding prices.
- `test.csv`: Contains the test data with car features for which prices need to be predicted.

### Columns in Input Data
- `brand`: The brand of the car (e.g., Ford, Toyota).
- `model`: The model of the car.
- `model_year`: The year the car model was manufactured.
- `milage`: The mileage of the car.
- `fuel_type`: The type of fuel used by the car (e.g., Petrol, Diesel).
- `engine`: The engine specification of the car.
- `transmission`: The type of transmission (e.g., Manual, Automatic).
- `accident`: The accident history of the car (e.g., Yes, No).
- `price` (only in `train.csv`): The price of the car.

### Output Data
- `predicted_prices.csv`: Contains the predicted prices for the test dataset. The file includes the following columns:
  - `id`: The unique identifier for each car in the test dataset.
  - `predicted_price`: The predicted price of the car.

## Code Overview

### Data Preprocessing
The data preprocessing steps include:
- Handling missing values using `SimpleImputer`.
- Encoding categorical variables using `LabelEncoder`.
- Scaling numerical features using `StandardScaler`.

### Model Training
The model is built using TensorFlow's Keras API and involves the following steps:
- Creating a sequential LSTM model with a dropout layer for regularization.
- Compiling the model with the Adam optimizer and mean squared error loss function.
- Training the model using an early stopping callback to prevent overfitting.

### Prediction
The test data is reshaped to match the input shape expected by the LSTM model. The model then predicts the prices, and the results are saved in `predicted_prices.csv`.

## Running the Code

1. Ensure you have the required libraries installed:
   ```bash
   pip install pandas numpy scikit-learn tensorflow
   ```

2. Place your `train.csv` and `test.csv` files in the same directory as the code.

3. Run the script:
   ```bash
   python car_price_predictor.py
   ```

4. The predicted prices will be saved in a file named `predicted_prices.csv`.

## Example Usage

### train.csv
| brand  | model  | model_year | milage | fuel_type | engine | transmission | accident | price |
|--------|--------|------------|--------|-----------|--------|--------------|----------|-------|
| Ford   | Fiesta | 2010       | 80000  | Petrol    | 1.6L   | Manual       | No       | 5000  |
| Toyota | Corolla| 2012       | 60000  | Diesel    | 1.8L   | Automatic    | No       | 7000  |

### test.csv
| id | brand  | model  | model_year | milage | fuel_type | engine | transmission | accident |
|----|--------|--------|------------|--------|-----------|--------|--------------|----------|
| 1  | Ford   | Fiesta | 2011       | 75000  | Petrol    | 1.6L   | Manual       | No       |
| 2  | Toyota | Corolla| 2013       | 65000  | Diesel    | 1.8L   | Automatic    | No       |

### predicted_prices.csv
| id | predicted_price |
|----|-----------------|
| 1  | 5200            |
| 2  | 7200            |

## Conclusion

This project provides a comprehensive approach to predicting car prices using an LSTM model. The code handles data preprocessing, model training, and prediction, and outputs the predicted prices in a CSV file.

---

Feel free to adjust the content as per your specific project details and requirements.
