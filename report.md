# ISOM 835 Term Project Report

**Title:** Trust & Safety Username Classifier Using Predictive Modeling
**Student:** Mutaz Abdel Dayem
**Course:** ISOM 835 – Predictive Analytics and Machine Learning
**Professor:** Hasan Arslan
**Date:** May 2025

---

## Introduction & Dataset Description

In the digital age, content moderation has become one of the most critical challenges faced by social media platforms. This project presents a machine learning-based classifier designed to identify potentially harmful usernames using a Trust & Safety (T\&S) keyword framework. The aim is to simulate a real-world solution to automatically flag usernames containing adult content, hate speech, violent terms, or high-risk language before user profiles go live.

The dataset was constructed using three text files: `usernames-train.txt`, `usernames-dev.txt`, and `usernames-test.txt`. Combined, these files include over 200,000 entries with manually or rule-based labels: `safe`, `risky`, and `blocked`. Each row contains a user's display name, their username (e.g., @wetgirls69), and a classification label.

The dataset represents both real-world and synthetically generated usernames. Obfuscations such as character substitutions (e.g., "f\*\*k", "pr0n") were deliberately included to mimic the tactics often used by users to bypass moderation systems.

---

## Exploratory Data Analysis (EDA)

Due to the short and textual nature of usernames, traditional EDA techniques such as scatterplots or correlation matrices offered limited value. Instead, exploration was carried out through:

* **Label distribution analysis**: The data was heavily skewed toward the `safe` category, with significantly fewer examples of `risky` or `blocked` usernames.
* **Sample inspection**: Random samples from each category were manually reviewed to validate the rule-based labels and explore false positives/negatives.
* **False-positive review**: Words like "lover", "69", and political terms like "freedom" often caused safe usernames to be flagged incorrectly, motivating a deeper review of keyword combinations.

---

## Preprocessing

A robust preprocessing pipeline was essential due to the diversity and unpredictability of user-generated content. The following steps were applied:

### 1. **Normalization**

* Converted all usernames to lowercase
* Removed special characters and normalized common obfuscations (e.g., "f\*ck" to "fuck")

### 2. **Keyword Dictionary Construction**

* Defined categories with extensive keyword lists:

  * `profanity`: curse words, slurs
  * `adult`: pornographic or sexual content
  * `hate`: antisemitic, racist, anti-LGBT terms
  * `violence`: murder, terror, suicide terms
  * `child_abuse`: loli, cp, grooming keywords
  * `drugs`: weed, crack, meth, kush, xanax
  * `risky`: conspiracy, MAGA, cashapp, crypto
  * `obfuscated`: encoded/altered hate speech

### 3. **Label Assignment**

* Used a rule-based system to assign initial labels (`ts_label`) based on keyword presence
* Combined `blocked_keywords` and `risky_keywords` logic into an automated pre-labeling function

### 4. **Vectorization**

* Applied `CountVectorizer` with character n-grams (3 to 5) to create features from short usernames

### 5. **Balancing**

* The dataset was imbalanced; the `safe` class dominated. To mitigate this, a balanced dataset was created with equal counts of `safe`, `risky`, and `blocked` entries for model training.

---

## Business Questions

1. **Can usernames be automatically classified for moderation before going live?**
   Yes. Using a lightweight, keyword-driven predictive model, usernames can be reliably flagged before publication.

2. **What categories of unsafe usernames are most common?**
   `Adult content` and `hate speech` dominate the `blocked` category. Risky usernames often include political or financial references like "maga", "crypto", or "freedom".

3. **Can explainability be built into such models to support human moderators?**
   Yes. This model uses keyword categories to identify why a name was flagged, offering interpretable reasoning for each classification.

---

## Predictive Modeling

### Model Used:

* **Multinomial Naive Bayes (MNB)**

MNB was chosen due to its:

* Efficiency with large-scale text data
* Compatibility with character-level vectorization
* High interpretability and reproducibility

## 🤖 Predictive Modeling

### Model Used:
- **Multinomial Naive Bayes**

This model was selected due to its strong performance in text classification tasks, especially when working with short-form strings like usernames. Combined with a carefully engineered set of character n-gram features and rule-based preprocessing, it provided a highly scalable and interpretable solution.

The focus of this project was not solely on traditional machine learning metrics, but on *Trust & Safety relevance* — ensuring the system captures and flags risky and blocked usernames reliably.

### Performance (Balanced Dataset):

| Class      | Precision | Recall | F1 Score |
|------------|-----------|--------|----------|
| Blocked    | 0.62      | 1.00   | 0.77     |
| Risky      | 0.83      | 0.99   | 0.90     |
| Safe       | 1.00      | 0.62   | 0.76     |

- **Overall Accuracy:** 81.7%

This model favors **recall** for blocked and risky content — a safer design for moderation workflows. While some safe usernames are over-flagged, the classifier provides **high coverage and auditability**, which is critical in high-risk moderation environments.


Most classification errors occurred when safe usernames contained suggestive patterns (e.g., "booklover69").

---


## 📊 Insights & Recommendations

- The model effectively detects obfuscated keywords and harmful language using character-based features.
- It prioritizes **risk coverage over perfect precision** — a strategic tradeoff in content safety enforcement.
- Keyword engineering, not just machine learning, played a crucial role in identifying subtle risks in usernames.
- False positives (e.g., “booklover69”) are manageable and expected in high-sensitivity use cases. They can be further reduced with whitelisting, user reports, or human-in-the-loop review.
- This approach is already deployable — a lightweight model with understandable rules and high flagging accuracy for risk content.


---

## Ethics & Interpretability

### Risks:

* **False positives**: Risk of misclassifying legitimate usernames as `blocked` can affect user trust
* **Bias**: Improper keyword lists can reflect or amplify bias (e.g., LGBTQ or religious terms)
* **Censorship concerns**: Terms like "trump", "maga", or "freedom" may be politically sensitive

### Mitigations:

* All flagged usernames are assigned a **reason category** (e.g., "adult", "hate", "drugs")
* Human moderators can override model predictions based on context
* Transparent documentation of keyword sources and regular review of rules is essential

---

## Appendix

**Colab Notebook** :https://colab.research.google.com/drive/1uTK09DFmwwqXlwzN5_lO5bD4fZEak5Ei?usp=sharing

GitHub Repository: https://github.com/Abdelmou1987/username-classifier-project

Files Included:

T&S_Project.ipynb

usernames-train.txt, usernames-dev.txt, usernames-test.txt

report.md, README.md, .gitignore

---

**Note**: Due to the nature of usernames, visualizations such as bar plots or heatmaps were omitted. Instead, qualitative review and manual testing formed the core of the exploratory and evaluation phases.
