<h1 align="center">🫀 Heart Disease Prediction using Machine Learning</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11%2B-blue" alt="Python Version" />
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License" />
  <img src="https://img.shields.io/badge/Status-Completed-success" alt="Project Status" />
  <img src="https://img.shields.io/badge/Built%20with-%E2%9D%A4-red" alt="Love" />
</p>

---

## 📌 Table of Contents
- [Project Overview](#project-overview)
- [Business Problem & Impact](#business-problem--impact)
- [Dataset](#dataset)
- [Methodology & Techniques](#methodology--techniques)
- [Key Findings & Results](#key-findings--results)
- [Important Note on Model Performance & Data Integrity](#important-note-on-model-performance--data-integrity) - [How to Run](#how-to-run)
- [Requirements](#requirements)
- [References](#references)
- [Connect with Me](#connect-with-me)

---

## 💡 Project Overview

This project **develops and evaluates machine learning models to accurately predict the presence of heart disease** in patients based on a comprehensive set of medical attributes. As cardiovascular diseases are a leading cause of mortality globally, early and accurate prediction is crucial for timely intervention and improving patient outcomes.

This work demonstrates an end-to-end data science workflow, including:
* **Data Preprocessing:** Handling outliers and making informed decisions on data integrity.
* **Exploratory Data Analysis (EDA):** Uncovering key relationships within medical data.
* **Model Building:** Implementing and evaluating a range of classification algorithms.
* **Performance Optimization:** Applying hyperparameter tuning to achieve superior predictive accuracy.

## 📈 Business Problem & Impact

Heart disease poses significant challenges to healthcare systems worldwide, responsible for an estimated 17.9 million deaths annually. Traditional risk assessment models often struggle to capture the complex, non-linear interactions among various risk factors.

This project directly addresses this by:
* **Enhancing Early Detection:** Providing a data-driven tool for clinicians to identify at-risk patients more effectively.
* **Improving Patient Outcomes:** Facilitating earlier diagnosis, which can lead to more personalised treatment regimens and potentially decrease the mortality rates.
* **Leveraging AI for Healthcare:** Showcasing the power of machine learning to analyze large medical datasets, identify hidden patterns, and improve prediction accuracy beyond conventional methods.

## 📊 Dataset

* **Source:** A medical dataset containing various patient attributes.
* **Original Size:** 1025 observations, 14 features.
* **Post-Cleaning Size:** 968 observations, 14 features.
* **Target Variable (`Target`):** Binary classification, where `1` indicates the presence of heart disease and `0` indicates its absence.
* **Data Characteristics:** Includes both numerical and categorical features.

**Note on Data Duplicates:**
During the data cleaning process, **723 duplicate records were identified** within the original dataset of 1025 rows. Removing these would have resulted in a significant loss of data(reducing the dataset to 302 unique rows). Given the absence of unique patient identifiers or timestamps to distinguish these as data entry errors or independent repeated observations, the decision was made to **retain these duplicates**. This approach prioritizes maximizing the available data for pattern learning, acknowledging that this may lead to a more optimistic estimation of model performance during internal validation. This was a deliberate trade-off given the dataset's characteristics.

## ⚙️ Methodology & Techniques

The project followed a structured machine learning pipeline:

1.  **Data Cleaning:**
    * Missing values were checked (none found).
    * Identified and analyzed duplicate records.
    * **Outlier removal** was performed on `RestingBloodPressure`, `Cholesterol`, and `OldPeak` to reduce skewness and improve model performance.
    * Columns were renamed for clarity.

2.  **Exploratory Data Analysis (EDA):**
    * **Statistical Summary:** Detailed analysis of age, sex distribution (69.9% male), blood pressure, cholesterol, fasting blood sugar, and maximum heart rate, revealing key insights and distributions.
    * **Visualizations:** Histograms with KDE for numerical features (e.g., Age showing a slight right skew, OldPeak being right-skewed), sex distribution pie charts, and scatter plots (e.g., Age vs. Max Heart Rate showing expected inverse relationship).
    * **Correlation Analysis:** A correlation matrix highlighted moderate positive correlations (`ChestPain`, `MaxHeartRate`, `STSlope`) and moderate negative correlations (`RestingBloodPressure`, `Age`, `Sex`, `Thalium`, `MajorVessels`, `ExcerciseAngina`, `OldPeak`) with the target variable.

3.  **Feature Engineering:**
    * **Label Encoding:** Applied to ordinal categorical features (`ChestPain`, `STSlope`).
    * **One-Hot Encoding:** Applied to nominal categorical features (`RestingECG`, `ExcerciseAngina`, `MajorVessels`, `Thalium`).
    * **Feature Scaling:** `StandardScaler` was used on numerical features (`Age`, `RestingBloodPressure`, `Cholesterol`, `MaxHeartRate`, `OldPeak`) to ensure equal contribution during model training, especially for distance-based algorithms.

4.  **Model Building & Evaluation:**
    * **Train-Test Split:** Data was split 70% for training and 30% for testing.
    * **Algorithms Evaluated:**
        * **Logistic Regression:** Chosen for simplicity and interpretability.
        * **Random Forest:** Ensemble method known for robustness and handling non-linear relationships.
        * **Support Vector Machine (SVM):** Popular for handling high-dimensional, complex data and robustness against overfitting.
        * **Decision Tree:** Simple, widely used for medical datasets, and capable of capturing complex relationships.
        * **Gaussian Naive Bayes:** Simple, fast, and effective with smaller datasets.
    * **Performance Metrics:** Models were rigorously evaluated using Accuracy, Precision, Recall, F1-Score, and ROC AUC.
    * **Hyperparameter Tuning:** `GridSearchCV` was extensively used to optimize Logistic Regression and SVC, significantly improving their performance and mitigating overfitting risks.

## 🚀 Key Findings & Results

All models achieved strong predictive performance (80-96% accuracy), demonstrating the feasibility of ML for heart disease prediction.

| Model | Accuracy | Precision | Recall | F1-Score | ROC AUC |
| :---------------------- | :------- | :-------- | :----- | :------- | :------ |
| **Random Forest** | 96.7% | 95.4% | 97.9% | 96.7% | 0.996 |
| Decision Tree | 93.8% | 93.9% | 93.3% | 93.3% | 0.964 |
| Support Vector Machine | 88.9% | 84.0% | 95.3% | 89.3% | 0.958 |
| Logistic Regression | 83.4% | 79.2% | 89.3% | 83.9% | 0.916 |
| Gaussian Naive Bayes | 81.2% | 78.6% | 83.9% | 81.1% | 0.887 |

**Key Insights:**

* **Random Forest Classifier** emerged as the top-performing model, showcasing exceptional accuracy (96.7%), precision (95.4%), recall (97.9%), and a near-perfect ROC AUC (0.996). Its high recall is particularly critical in medical diagnosis, minimizing false negatives.
* **Hyperparameter Tuning Significance:** Significant performance improvements were observed post-tuning:
    * SVC's F1-score increased from 89% to **96%**, highlighting the impact of optimization.
    * Logistic Regression's F1-score improved from 83% to **88%**.
* **Optimal Hyperparameters Identified:**
    * **Logistic Regression:** `C=0.1`, `max_iter=100`, `penalty='l2'`, `solver='liblinear'`.
    * **SVC:** `C=10`, `degree=4`, `gamma='scale'`, `kernel='poly'`, `probability=True`.
* **Decision Tree Classifier** also performed very strongly (93.8% accuracy), making it a viable second-best option.

These findings underscore the effectiveness of machine learning in cardiovascular disease prediction and provide a robust model for potential future applications.

---

## ⚠️ Important Note on Model Performance & Data Integrity

The exceptionally high performance metrics achieved by the top-performing models (e.g., Random Forest Classifier with 96.7% accuracy and 0.996 ROC AUC, and SVC with 96% F1-score post-tuning) warrant careful interpretation.

As detailed in the "Dataset" section, **723 duplicate records were identified and retained** within the dataset to maximize the available data for pattern learning, given the absence of unique patient identifiers or visit timestamps. While this approach allows the models to train on a larger volume of data, it introduces a **potential risk of data leakage** if these duplicates represent non-independent observations (e.g., identical patient records appearing in both the training and testing sets). This could lead to an **overly optimistic estimation of the model's true generalization performance** on entirely new, truly unseen data.

For a production-level deployment and to ensure the most robust and generalizable results, **future work would critically involve:**
1.  **Obtaining clarified metadata:** To definitively ascertain the nature of these duplicate records (e.g., confirming if they are truly distinct patient profiles or repeat visits).
2.  **Implementing a strict data handling strategy:** Such as removing all exact duplicates or performing a patient-level split (if unique patient IDs were available), *before* the train-test split to prevent data leakage and provide a more conservative, realistic evaluation of model performance on truly unseen data.

Despite this, the project effectively demonstrates a comprehensive machine learning workflow, proficiency in various algorithms, and the impact of feature engineering and hyperparameter tuning on model optimization. The insights gained from the EDA and correlation analysis remain valuable for understanding heart disease risk factors.

---

## 💻 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/heart-disease-prediction.git](https://github.com/your-username/heart-disease-prediction.git)
    cd heart-disease-prediction
    ```
2.  **Set up the Python environment:**
    It is recommended to use a virtual environment.
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: `venv\Scripts\activate`
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (Note: You'll need to create a `requirements.txt` file by running `pip freeze > requirements.txt` in your activated environment once you've installed all libraries from the `Requirements` section.)
4.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook FinalProject.ipynb
    ```
    Follow the instructions within the notebook to execute the code cells sequentially.

## 🛠 Requirements

* Python 3.11+
* **Core Libraries:**
    * `numpy`
    * `pandas`
    * `matplotlib`
    * `seaborn`
    * `scikit-learn`
    * `plotly` (if you implement interactive visualizations later)
    * `warnings` (for managing warnings during execution)

## ✍️ References

* Shah, Devansh, Samir Patel, and Santosh Kumar Bharti. "Heart disease prediction using machine learning techniques." *SN Computer Science* 1.6 (2020): 345.
* Ramalingam, V. V., Ayantan Dandapath, and M. Karthik Raja. "Heart disease prediction using machine learning techniques: a survey." *International Journal of Engineering & Technology* 7.2.8 (2018): 684-687.
* Kaggle: Heart Disease Dataset. [https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset/data](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset/data)

---

## 🤝 Connect with Me

Email: shahbaz.w156@gmail.com
Linkedin: www.linkedin.com/in/shahbaz-sharif

---

<p align="center">
  <b>🚀 Built with passion & machine learning 🚀</b>
</p>
