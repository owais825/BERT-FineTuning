# 📰 BERT Fine-Tuning for BBC News Classification

An end-to-end text classification system using **BERT Base Uncased**, fine-tuned on the **BBC News** dataset to classify articles into:

**Business · Entertainment · Politics · Sport · Tech**

---

## 📦 Project Overview

This project implements:

- Data cleaning & preprocessing  
- Tokenization using `bert-base-uncased`  
- Model configuration  
- Training via HuggingFace Trainer  
- Validation & metric reporting  
- Performance analysis & improvements  

---

## 📘 Dataset: BBC News

### **Preprocessing Steps**
- Removed unwanted characters  
- Normalized text  
- Lowercased content  
- Created train/validation/test splits  

### **Label Mapping**

| Label | Category      |
|-------|---------------|
| 0     | Business      |
| 1     | Entertainment |
| 2     | Politics      |
| 3     | Sport         |
| 4     | Tech          |

### **Sample Format**
```json
{
  "text": "news article content...",
  "label": 0
}
```

---

# 🔄 Project Workflow

## **Step 1 — Dataset Loading & Cleaning**
- Load raw BBC text  
- Clean & normalize  
- Generate train/validation splits  

---

## **Step 2 — Tokenization**
Tokenization with BERT Base Uncased:

```python
max_length = 256
padding = "max_length"
truncation = True
```

Generated fields:
- `input_ids`
- `attention_mask`
- `labels`

---

## **Step 3 — Model Initialization**
- Load **bert-base-uncased**  
- Add classification head (5 labels)  
- Dropout settings:

```python
hidden_dropout_prob = 0.1
attention_probs_dropout_prob = 0.1
```

---

# ⚙️ Training Configuration

### **Hyperparameters**

| Hyperparameter        | Value |
|-----------------------|-------|
| Epochs                | 3 |
| Train Batch Size      | 8 |
| Eval Batch Size       | 8 |
| Learning Rate         | 2e-5 |
| Warmup Steps          | 500 |
| Weight Decay          | 0.01 |
| Logging Steps         | 50 |
| Load Best Model       | True |
| LR Scheduler          | Linear warmup → linear decay |

---

# 📊 Training Results

## **Epoch 1**
- Training Loss: **0.5739**  
- Validation Loss: **0.17398**  
- Accuracy: **0.9640**  
- Precision: **0.9656**  
- Recall: **0.9640**  
- F1 Score: **0.9641**

---

## **Epoch 2**
- Training Loss: **0.0744**  
- Validation Loss: **0.10636**  
- Accuracy: **0.9720**  
- Precision: **0.9729**  
- Recall: **0.9720**  
- F1 Score: **0.9721**

---

## **Epoch 3**
- Training Loss: **0.0258**  
- Validation Loss: **0.12087**  
- Accuracy: **0.9720**  
- Precision: **0.9720**  
- Recall: **0.9720**  
- F1 Score: **0.9720**

---

# 🏁 Final Summary

- **Best Epoch:** Epoch 2  
- **Final Accuracy:** **97.2%**  
- **Final F1 Score:** **0.972**  
- Model performance is consistent and strong  

---

# 🔍 Performance Insights

### ✔ Learning Rate Behavior
- LR = 2e-5 produced stable convergence  
- No oscillation or gradient explosion  

### ✔ Training Loss Curve
`0.57 → 0.07 → 0.02`

### ✔ Validation Curve
- Lowest validation loss at **Epoch 2**  
- Slight overfitting at **Epoch 3**

### ✔ Generalization
- High precision and recall  
- Stable across all epochs  

---

# 🚀 Recommendations for Improvement

- Try alternative LRs: **1e-5**, **3e-5**  
- Increase batch size: **16/32**  
- Adjust weight decay: **0.001 → 0.01**  
- Add **early stopping**  
- Try **RoBERTa-base** for potential boost  

---

