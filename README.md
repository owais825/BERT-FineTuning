# BERT Fine-Tuning — BBC News Classification

This project is an end-to-end text classification system built using bert-base-uncased, fine-tuned on the BBC News Classification Dataset.
The model predicts one of five news categories:

Business

Entertainment

Politics

Sport

Tech

📌 Project Pipeline

The system includes:

Dataset cleaning and preprocessing

Tokenization

Model loading and configuration

Training using HuggingFace Trainer

Evaluation with accuracy, precision, recall, F1

Performance analysis and recommendations

📘 Dataset: BBC News

The BBC News dataset contains articles categorized into 5 topics.

✔ Preprocessing Steps

Removal of unwanted characters

Normalization

Lowercasing

Creation of train/validation/test splits

✔ Label Mapping
Label	Category
0	Business
1	Entertainment
2	Politics
3	Sport
4	Tech
✔ Final Dataset Structure

Each sample contains:

{
  "text": "news article content...",
  "label": 0
}

🔄 Complete Project Flow
Step 1 — Dataset Loading & Cleaning

Load raw BBC dataset

Clean text

Generate train/validation splits

Step 2 — Tokenization

Tokenized using bert-base-uncased with:

max_length = 256
padding = "max_length"
truncation = True


Outputs:

input_ids

attention_mask

labels

Step 3 — Model Initialization

Load BERT Base Uncased

Add classification head for 5 labels

Dropout used:

hidden_dropout_prob = 0.1
attention_probs_dropout_prob = 0.1

⚙️ Training (HuggingFace Trainer)
Hyperparameters
Hyperparameter	Value
Epochs	3
Train Batch Size	8
Eval Batch Size	8
Learning Rate	2e-5
Warmup Steps	500
Weight Decay	0.01
Logging Steps	50
Load Best Model	True
LR Scheduler	Linear warmup → linear decay
📊 Evaluation Results
Epoch 1

Training Loss: 0.5739

Validation Loss: 0.17398

Accuracy: 0.9640

Precision: 0.9656

Recall: 0.9640

F1 Score: 0.9641

Epoch 2

Training Loss: 0.0744

Validation Loss: 0.10636

Accuracy: 0.9720

Precision: 0.9729

Recall: 0.9720

F1 Score: 0.9721

Epoch 3

Training Loss: 0.0258

Validation Loss: 0.12087

Accuracy: 0.9720

Precision: 0.9720

Recall: 0.9720

F1 Score: 0.9720

🏁 Summary of Results

Best Epoch: Epoch 2 (lowest validation loss)

Final Accuracy: 97.2%

Final F1 Score: 0.972

Model performance is stable and consistent across epochs

🔍 Performance Insights
✔ Learning Rate Behavior

2e-5 provided smooth convergence

No oscillation or exploding gradients

✔ Training Curve

Training loss decreased steadily:
0.57 → 0.07 → 0.02

✔ Validation Curve

Best validation loss at Epoch 2

Slight overfitting appears at Epoch 3

✔ Generalization

High precision & recall

Strong real-world classification capability

🚀 Recommendations for Improvement

Test alternative learning rates: 1e-5, 3e-5

Increase batch size: 16 or 32 (if GPU allows)

Experiment with weight decay: 0.001 → 0.01

Add early stopping

Try RoBERTa-base, which often outperforms BERT

📦 Technologies Used

HuggingFace Transformers

PyTorch

BBC News Dataset

Scikit-Learn for metrics
