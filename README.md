# STOAM-VLSTM: Versatile Long Short-Term Memory for Time-Series Prediction

## Overview

**VLSTM** (Versatile Long Short-Term Memory) is an enhanced LSTM architecture tailored for time-series prediction tasks. It builds on the traditional LSTM model by adding advanced features such as automated data preprocessing, early stopping, model checkpointing, dynamic hardware optimization for faster training, and robust evaluation metrics. This versatile model is highly customizable and designed to efficiently handle multi-feature time-series data, making it suitable for a wide range of real-world applications.

**Key Features:**
- **Customizable LSTM architecture**: Choose the number of layers, units, and other hyperparameters.
- **Data preprocessing**: Automatic scaling of features using MinMaxScaler to improve model performance.
- **Training optimization**: Includes ModelCheckpoint and EarlyStopping to prevent overfitting and save time.
- **Dynamic GPU/CPU selection**: Automatically adjusts training resources for faster execution.
- **Prediction-ready**: Seamlessly make predictions on new data.
- **Comprehensive evaluation**: Use multiple metrics like MAE, RMSE, MAPE, and MAD for performance assessment.
- **Interactive visualizations**: Plot training loss and predictions using Plotly for better insight into model performance.

---

## Use Cases

**VLSTM** is perfect for time-series regression tasks. Some common use cases include:

- **Stock Price Prediction**: Predicting future stock prices based on historical market data.
- **Sales Forecasting**: Predicting future sales or demand for products in various industries.
- **Weather Forecasting**: Predicting weather conditions based on past data.
- **Energy Consumption Forecasting**: Estimating future energy usage based on historical consumption patterns.
- **Anomaly Detection**: Identifying unusual patterns in time-series data.

---

![VLSTM](https://github.com/user-attachments/assets/6ec10339-cb97-4ca8-b6de-a13215e1fa4d)

## How to Use VLSTM

### 1. **Installation**
To install the required dependencies, run the following command:

```bash
pip install -r requirements.txt
```

### 2. **Preparing Data**
Your dataset should be in a Pandas DataFrame (df) format with:

* Features: Columns containing historical data (e.g., 'Open', 'High', 'Low', 'Close' for stock prices).
* Target: A column with the values you want to predict (e.g., 'Close' for stock price prediction).
Use the prepare_data() method to preprocess your data:

```bash
vlstm = VLSTM(target='Close')
X, y = vlstm.prepare_data(df, features=['Open', 'High', 'Low', 'Close'])
```

### 3. **Training the Model**
Once the data is ready, train the model using the train() method:

```bash
history, y_test, y_pred, train_score, test_score = vlstm.train(df, features=['Open', 'High', 'Low', 'Close'])
```

### 4. **Evaluating the Model**
After training, evaluate the model's performance using various metrics such as MAE, RMSE, MAPE, and MAD:

```bash
vlstm.evaluate(y_test, y_pred)
```

### 5. **Making Predictions**
To make predictions on new data:

```bash
predictions = vlstm.predict(new_df, features=['Open', 'High', 'Low', 'Close'])
```

### 6. **Visualizing Results**
You can visualize training loss and the actual vs predicted values:

```bash
vlstm.plot_loss(history)
vlstm.prediction_plot(y_test, y_pred)
```

## Model Architecture

The VLSTM architecture consists of two LSTM layers followed by a Dense layer and Dropout for regularization. The network is highly customizable to meet the needs of different datasets and tasks. Here's a breakdown of the model layers:

1. LSTM Layer 1: This is a customizable layer with a user-defined number of units.
2. LSTM Layer 2: Another LSTM layer that can capture more complex time-series dependencies.
3. Dense Layer: A fully connected layer with a customizable number of units.
4. Dropout: Regularization layer to prevent overfitting by randomly dropping units during training.
5. Output Layer: The final Dense layer with a customizable activation function (linear for regression tasks).

## Comparison to Traditional LSTM

| **Feature**                         | **VLSTM Architecture**                                                                 | **Traditional LSTM**                                                                     |
|-------------------------------------|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| **Model Customization**             | Highly customizable: sequence length, number of layers, units, dropout, etc.           | Limited customization, usually one or two LSTM layers with default configurations.      |
| **Data Preprocessing**             | Automatic MinMax scaling of features and dynamic handling of the target feature.        | Requires manual data preprocessing and scaling of features.                             |
| **Training Optimization**          | Includes `ModelCheckpoint` and `EarlyStopping` to improve training efficiency and prevent overfitting. | Usually lacks these optimizations, leading to potential overfitting or inefficient training. |
| **GPU/CPU Optimization**           | Dynamic selection of GPU or CPU for training, improving resource utilization.           | Often defaults to CPU with limited GPU support.                                         |
| **Evaluation Metrics**             | Provides detailed metrics: MAE, RMSE, MAPE, MAD for robust model evaluation.           | Often limited to basic metrics like MSE or accuracy.                                    |
| **Prediction Readiness**           | Seamless transition for making predictions on new data with fitted scalers.            | Manual scaling required for prediction, making it less convenient.                       |
| **Model Saving and Deployment**    | Saves the best model automatically for deployment and inference.                       | Requires manual saving/loading of the model, less convenient for deployment.            |


## Why VLSTM is Better than Traditional LSTM:
* Advanced Features: VLSTM automates many processes (e.g., data scaling, model saving/loading, and training optimizations), reducing the manual effort required to build and deploy models.
* Optimized for Real-World Use: With GPU/CPU optimization, callbacks, and a focus on saving the best model, VLSTM is designed for more complex, scalable, and efficient workflows.
* Better Evaluation and Visualization: VLSTM provides comprehensive evaluation metrics and powerful visualizations to track model performance, making it easier to interpret results.

## Conclusion
VLSTM (Versatile Long Short-Term Memory) is a more flexible, efficient, and scalable approach to time-series forecasting compared to traditional LSTM models. It is ideal for use in real-world applications where ease of deployment, training optimization, and model interpretability are important. By offering robust features like automatic data preprocessing, early stopping, model checkpointing, and dynamic GPU utilization, VLSTM provides significant advantages over basic LSTM architectures, especially in production environments.
