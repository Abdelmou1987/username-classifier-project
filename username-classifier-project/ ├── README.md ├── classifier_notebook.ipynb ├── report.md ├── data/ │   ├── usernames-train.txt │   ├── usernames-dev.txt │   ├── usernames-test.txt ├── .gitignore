# Trust & Safety Username Classifier 🛡️

## 📌 Project Summary
This project builds a predictive model that classifies social media usernames as `safe`, `risky`, or `blocked`. Inspired by real-world Trust & Safety use cases in content moderation, this classifier combines machine learning with domain-specific keyword engineering to detect usernames that reference adult content, hate speech, violence, drugs, or political extremism.

Rather than simply optimizing for accuracy, the focus is on **risk-aware flagging**, **explainability**, and **realistic enforcement trade-offs** used in online safety systems.

---

## 🎯 Objectives

- Automate username risk assessment before they go live on a platform
- Combine rule-based keyword labeling with interpretable ML
- Identify obfuscated, slang-based, or disguised risky content
- Prioritize recall on harmful terms to protect platform integrity
- Build a deployable, human-auditable moderation model

---

## 📁 Dataset Description

The dataset consists of three files:
- `usernames-train.txt`
- `usernames-dev.txt`
- `usernames-test.txt`

Each file contains:
- `name` (display name)
- `username` (e.g., `@wetgirls69`, `@maga_patriot88`)
- `label` (`safe`, `risky`, or `blocked` — based on keyword matches)

The data includes real and simulated usernames, some of which are intentionally obfuscated or disguised.

---

## 🧠 Modeling Approach

- Text preprocessing using normalization, character filtering, and obfuscation decoding
- Rule-based labeling using curated Trust & Safety keyword categories
- Character n-gram vectorization (`CountVectorizer` with 3–5 char sequences)
- Model: **Multinomial Naive Bayes**

### Performance Highlights (Balanced Dataset):

| Class      | Precision | Recall | F1 Score |
|------------|-----------|--------|----------|
| Blocked    | 0.62      | 1.00   | 0.77     |
| Risky      | 0.83      | 0.99   | 0.90     |
| Safe       | 1.00      | 0.62   | 0.76     |

- **Overall Accuracy:** 81.7%
- **High recall for risky/blocked classes** ensures low risk exposure
- **Auditable, explainable flag reasons** using keyword category matches

---

## 🔍 Google Colab Notebook

👉 Click here to view and run the notebook: https://colab.research.google.com/drive/1uTK09DFmwwqXlwzN5_lO5bD4fZEak5Ei?usp=sharing

The notebook includes:
- Data loading and cleaning
- Keyword category logic
- Model training and evaluation
- Custom `test_username()` tool for live testing

---

## 🧾 Example Use Cases

```python
test_username("maga_patriot88")     # → RISKY
test_username("fuckjews")           # → BLOCKED (hate)
test_username("cutepuppy123")       # → SAFE
test_username("deepinsidegirl")     # → BLOCKED (adult)
test_username("crypto_bro69")       # → RISKY


