# 📈 Stock Price Prediction using LSTM Networks

A deep learning project that uses **Long Short-Term Memory (LSTM)** networks to forecast **Google (GOOG) stock closing prices** from historical time-series data.

---

## 📊 Dataset Used

**Dataset:** [Google (GOOG) Historical Stock Data](https://finance.yahoo.com/quote/GOOG/history/)  
**Source:** Yahoo Finance  
**Ticker:** `GOOG`  
**Time Range:** Last 20 years from the date of execution  
**Feature Used:** Adjusted Close Price

### Preprocessing

- Missing values handled where necessary
- Data normalized to **[0, 1]** using `MinMaxScaler`
- **100 previous trading days** used to predict the next day's price
- Chronological **70% training / 30% testing** split
- No shuffling to preserve time-series order

---

## 🧠 Model Architecture

The project uses a **Stacked LSTM** architecture:

```text
Input (100 Timesteps, 1 Feature)
            │
       LSTM (128)
            │
       LSTM (64)
            │
        Dense (25)
            │
         Dense (1)
            │
     Predicted Price
```

**Configuration:**

- **Optimizer:** Adam
- **Loss Function:** Mean Squared Error (MSE)
- **Batch Size:** 1
- **Epochs:** 2

---

## 📈 Performance

Since this is a **regression problem**, classification-style accuracy (%) is not appropriate. Model performance is evaluated using **RMSE (Root Mean Squared Error)**.

| Metric | Result |
|---|---:|
| Training Samples | 3,454 |
| Testing Samples | 1,481 |
| Test RMSE | ~2.6 – 3.56 |

> **Note:** The dataset is downloaded fresh from Yahoo Finance on every run, so the exact performance may vary depending on the execution date.

---

## ▶️ How to Run the Notebook

1. Clone this repository.
2. Open `LSTM_project.ipynb` using **Jupyter Notebook** or **JupyterLab**.
3. Install the required dependencies.
4. Run all cells from top to bottom.
5. The trained model will be saved as:

```text
Latest_stock_price_model.keras
```

---

## 🛠️ Tech Stack and Dependencies

| Category | Technologies |
|---|---|
| Language | Python 3 |
| Data Collection | yfinance |
| Data Processing | Pandas, NumPy |
| Deep Learning | Keras / LSTM |
| Evaluation | Scikit-learn |
| Visualization | Matplotlib |
| Environment | Jupyter Notebook |

### Installation

```bash
pip install yfinance pandas numpy matplotlib scikit-learn keras
```
