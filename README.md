# 🎓 Student Performance Prediction

## 📝 Description
* This project uses machine learning models to predict students' final grades based on features like study time, parental support, and more. It compares the performance of linear and non-linear models.

## 📁 Project Structure
* student-performance-analysis.Rmd: Full analysis in R Markdown.
* data/student_performance.csv: Cleaned dataset used for modeling.
* info_dataset.pdf: Detailed information about the dataset columns and their descriptions.


## 📂 Dataset Information
* The dataset used in this project contains various features related to student demographics, school performance, and personal characteristics. The primary dataset is sourced from the UCI Machine Learning Repository.
* Additionally, supplementary data is included in the data/ folder, which may contain processed or modified versions of the original data. Please refer to the info_dataset.pdf file for a detailed description of each column and its values.

* 🚀 How to Run
* Open the .Rmd file in RStudio.
* Install the required packages:
* Install.packages libraries <- c("ucimlrepo", "dplyr", "mlbench", "fastDummies", "caret", "corrplot", "ggplot2", "e1071", "quantmod", "kernlab", "rpart", "rpart.plot", "randomForest")
* Knit the R Markdown file to generate the output with code, visualizations, and results.

# ⚙️ Data Preprocessing & Modeling Workflow
## 🔧 Preprocessing Steps
* One-Hot Encoding was applied to categorical variables such as **internet,higher,romantic**, using the fastDummies package. This ensured that the machine learning models could process these non-numeric features appropriately.
* Irrelevant or identifier columns like **famsize,pstatus,schoolsup,famsup,paid,activities and nursery**  were dropped to reduce noise and prevent data leakage.
* Data was split into training and test sets using an 80/20 split for model validation.

## 🔁 Cross-Validation
* To prevent overfitting and ensure robust performance metrics, 10-fold Cross-Validation was used with the caret package. This was applied during model training to evaluate performance across multiple data subsets.
* The training process used consistent preprocessing (e.g., centering, scaling) inside cross-validation pipelines.

## 🤖 Model Training
* Multiple regression models were trained, including:
* Linear Regression
* GLMNet (Lasso and Ridge)
* Support Vector Machine (SVM)
* K-Nearest Neighbors (KNN)
* Decision Tree
* Random Forest
* XGBoost
* Performance was compared using standard metrics: RMSE, R², and MAE on both training and testing datasets.
# 📊 Model Performance

| Model              | Train RMSE | Train R² | Train MAE | Test RMSE | Test R² | Test MAE |
| ------------------ | ---------- | -------- | --------- | --------- | ------- | -------- |
| Linear Regression  | 1.18       | 0.82     | 0.78      | 1.18      | 0.82    | 0.78     |
| GLMNet             | 1.23       | 0.86     | 0.81      | 1.13      | 0.83    | 0.72     |
| SVM                | 1.26       | 0.85     | 0.79      | 1.11      | 0.84    | 0.73     |
| KNN                | 2.29       | 0.59     | 1.61      | 2.02      | 0.49    | 1.47     |
| Decision Tree (DT) | 1.41       | 0.82     | 0.90      | 1.17      | 0.82    | 0.69     |
| Random Tree (RT)   | 1.29       | 0.85     | 0.84      | 1.15      | 0.83    | 0.72     |
| XGBoost            | 1.32       | 0.84     | 0.85      | 1.19      | 0.82    | 0.75     |

## 📌 Key Findings
* G1 and G2 are highly correlated with G3: Students who perform well in earlier exams tend to perform better in the final exam.
* Study time: A positive correlation with G3, indicating that more study time contributes to better final grades.
* Parental occupation: Students with teacher parents tend to score higher.
* Internet access: Students with internet access at home performed better.
* Female students had slightly higher average G3 scores than male students.
* Students aiming for higher education performed better.
* Students with more involved parents did not necessarily perform better, possibly due to over-involvement or low academic interest.
* School: G3 scores varied slightly by school, indicating the school environment might have an impact on student outcomes.

##  Conclusion
* The models analyzed, including linear regression, GLMNet, and SVM, provide valuable insights into the factors affecting student performance. G1 and G2 are the strongest predictors of G3 (final grades), reinforcing the idea that early performance is a good indicator of final success.
* Study time is another critical factor for predicting student success, showing the importance of effective time management and preparation.
* Parental involvement and access to resources like the internet have a noticeable impact, though the exact nature of this relationship varies.
* While certain factors such as study time and parental occupation appear to strongly influence student performance, other variables like failures and school-related factors could offer additional avenues for future exploration.
