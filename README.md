# Trust & Safety Username Classifier

## 📌 Project Summary
This project builds a machine learning model to classify social media usernames as `safe`, `risky`, or `blocked` based on a Trust & Safety keyword framework. It mimics real-world use cases for social media moderation and content policy enforcement.

## 🎯 Objectives
- Use predictive modeling to automate username content moderation.
- Identify risky usernames tied to adult content, hate speech, or violence.
- Evaluate the model's performance and interpret the results in an ethical context.

## 📁 Dataset
- **Source:** Curated and generated Twitter-style usernames
- **Files:** `usernames-train.txt`, `usernames-devs.txt`, `usernames-test.txt`
- Each file contains: `name`, `username`, and `label` (ground truth)

## 🧰 Tools and Libraries
- Python, Google Colab
- Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn, Regex
- Gradio (for optional UI)

## 📊 Google Colab Notebook
👉 [Click here to view and run the notebook](YOUR_COLAB_NOTEBOOK_LINK_HERE)

## 📈 Visualizations
All key visualizations are stored in the `/visualizations` folder. Examples include:
- Label distribution
- Word cloud of risky usernames

## 📃 Final Report
See `report.md` or `report.pdf` in this repository for full methodology, modeling, results, and ethical discussion.

## 🚀 How to Run
1. Open the Colab notebook
2. Upload the dataset (`.txt` files)
3. Run all cells to train and evaluate the model
4. Use the `test_username()` function to try custom inputs

## ✅ Project Deliverables
- ✅ Data Cleaning & Preprocessing
- ✅ Exploratory Data Analysis (EDA)
- ✅ Two predictive models (Naive Bayes + Logistic Regression or Random Forest)
- ✅ Model Evaluation (Accuracy, Precision, Recall, F1 Score)
- ✅ Ethical Reflection & Limitations
- ✅ Colab + GitHub integration

---

