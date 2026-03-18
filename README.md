# 🚀 Prompt Engineering + RAG Text Classification

## 📌 Project Overview

This project explores how different prompt engineering strategies and retrieval-augmented generation (RAG) influence the structure and style of generated text. The goal is to classify texts based on prompt type and the use of RAG using NLP and machine learning techniques.

---

## 🎯 Objective

* Detect prompt type from generated text
* Identify whether RAG was used
* Analyze how prompt design affects text patterns

---

## 🧩 Dataset Creation (Core Contribution)

### 📊 Dataset Idea

We created a **custom dataset** by systematically varying:

* Prompt style
* Use of RAG (context vs no context)

### 🏷 Classes (8 total)

```
0 = No-RAG + Direct  
1 = No-RAG + Role-based  
2 = No-RAG + Constrained  
3 = No-RAG + Stepwise  
4 = RAG + Direct  
5 = RAG + Role-based  
6 = RAG + Constrained  
7 = RAG + Stepwise  
```

---

## 🛠️ How the Dataset Was Built

### Step 1: Define Topics

A set of diverse topics was selected:

* Machine Learning
* Climate Change
* Data Privacy
* Cybersecurity
* Neural Networks
  (≈ 20 topics total)

---

### Step 2: Define Prompt Templates

Four prompt engineering strategies were used:

* **Direct** → simple explanation
* **Role-based** → assign expert role
* **Constrained** → enforce structure (e.g., bullet points)
* **Stepwise** → force sequential explanation

Example:

```
Direct: Explain overfitting.
Role-based: You are a professor. Explain overfitting.
Constrained: Explain overfitting in 5 bullet points with an example.
Stepwise: Explain overfitting step by step.
```

---

### Step 3: Add RAG (Context Injection)

For RAG samples, a short factual paragraph was added before the prompt:

```
Context: Overfitting occurs when a model learns training data too closely...

Explain overfitting.
```

👉 This simulates **retrieval-augmented generation (RAG)** without complex pipelines.

---

### Step 4: Automatic Generation (OpenAI API)

A Python script was used to:

* Loop through topics
* Apply all prompt styles
* Generate outputs with and without RAG
* Store results in CSV

Each topic produced:

* 4 (No-RAG) + 4 (RAG) = **8 samples**

---

### Step 5: Dataset Size

* 20 topics × 8 combinations
  → **160 samples**

---

### 📁 Dataset Format

```
text | label | rag | prompt_type | topic
```

Example:

```
"Overfitting occurs when...", 5, 1, role_based, overfitting
```

---

## 🧠 Methodology

### 🔍 NLP Feature Extraction

* Tokenization
* n-grams
* TF-IDF

---

### 📊 Machine Learning Models

* Logistic Regression (baseline)
* SVM / Naive Bayes (comparison)

---

### 🤖 Deep Learning

* DistilBERT / BERT for classification

---

## 📈 Analysis Goals

* Can models detect prompt type from output?
* Can models identify RAG usage?
* Which prompt style creates the most distinct patterns?

---

## 🔥 Key Contribution

This project introduces a **novel dataset** that captures:

* Prompt engineering effects
* RAG influence on generated text

It demonstrates that prompt strategies leave **learnable linguistic patterns** detectable by ML models.

---

## 🚀 How to Run

```bash
pip install pandas scikit-learn transformers openai
python generate_dataset.py
```

Then:

* Open notebook
* Run preprocessing + models

---

## 📌 Future Work

* Add more prompt types (creative, adversarial)
* Use real vector database for RAG
* Compare different LLMs

---

## 🏁 Conclusion

Prompt design and RAG significantly influence text structure. These differences can be captured and classified using NLP and machine learning, offering insights into prompt engineering and AI behavior.

