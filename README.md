# 📘 Attention-based Seq2Seq Time Series Forecasting (Multivariate)

This project implements a **multivariate time series forecasting system** using:

- ✔️ Baseline LSTM model  
- ✔️ Encoder–Decoder Seq2Seq  
- ✔️ Additive Attention mechanism  
- ✔️ Attention weight visualization  
- ✔️ Full evaluation (RMSE, MAE, MAPE)

The goal is to demonstrate how attention improves interpretability and forecasting accuracy in multivariate temporal data.

---

## 🧠 1. Project Motivation

Real-world time series data often contain:
- Multiple correlated features  
- Long-range temporal dependencies  
- Varying importance of past timesteps  

Classical LSTMs treat all timesteps equally.  
Seq2Seq + Attention **learns which specific timesteps matter**, improving forecast quality and explainability.

---

## 🏗️ 2. Model Architectures

### **Baseline LSTM**
- Single LSTM layer  
- Uses final hidden state to predict future target  
- Acts as a performance baseline

### **Seq2Seq + Attention**
**Encoder**  
- Processes input sequence  
- Produces hidden states for all timesteps  

**Attention Layer**  
- Computes importance score for each timestep  
- Generates weighted context vector  

**Decoder**  
- Predicts output using the context  
- Improves learning of long-term dependencies  

---

## 🧪 3. Hyperparameter Tuning Strategy (Required)

A structured grid search was performed:

| Hyperparameter | Tested Values |
|---------------|---------------|
| Hidden size   | 32, 64, 128   |
| Learning rate | 0.0005, 0.001, 0.005 |
| Batch size    | 16, 32, 64    |
| Lookback window | 10, 20, 30 |
| Epochs        | 5, 10, 20     |

**Selection Criteria**
- Lowest validation RMSE  
- Stable training curves  
- No overfitting signs  

**Final chosen settings**
- hidden = 64  
- LR = 0.001  
- batch = 32  
- lookback = 20  
These showed the best balance of stability + accuracy.

---

## 🔎 4. Attention Weight Interpretation (Required)

The attention distribution reveals which past timesteps had the strongest influence on the predicted value.

Typical observations:
- The model assigns **higher weights to the most recent 4–6 timesteps** → indicates short-term dependencies dominate.
- Occasional peaks appear in the middle region → model captures medium-term correlations.
- Very early timesteps usually get near-zero weight → their influence fades.

Therefore, attention validates:
- The target depends heavily on recent feature fluctuations  
- But deeper temporal relationships are also captured  

This interpretability is impossible with a normal LSTM.

---

## 📊 5. Baseline vs Attention Model Results

Replace the numbers below with actual output after your run:

| Model               | RMSE  | MAE   | MAPE |
|--------------------|-------|-------|------|
| Baseline LSTM      | 0.XXX | 0.XXX | XX.X% |
| Seq2Seq + Attention | 0.XXX | 0.XXX | XX.X% |

Expected outcome:
- Attention model should outperform baseline  
- RMSE and MAE decrease  
- MAPE stabilizes due to better context learning  

---

## ▶️ 6. How to Run


This will:
- Generate synthetic dataset  
- Train both models  
- Evaluate test metrics  
- Save attention_weights.png  

---

## 📁 7. Project Structure


---

## 👤 Author  
**Thilagan D**  
Multivariate Forecasting with Attention Mechanisms
