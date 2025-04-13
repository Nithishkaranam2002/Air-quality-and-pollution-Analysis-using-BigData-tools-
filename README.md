# 🌫️ Air Quality and Pollution Analysis using Big Data Tools

This project analyzes air pollution data using Big Data and Machine Learning tools on AWS. The pipeline involves preprocessing large-scale air quality data using Hive on EMR and building a regression model using AWS SageMaker Studio to predict CO levels based on other pollutants and weather data.

## 📌 Project Structure

### 🔹 Phase 1: Data Preprocessing with Hive on AWS
- Dataset: [UCI Air Quality Dataset](https://archive.ics.uci.edu/dataset/360/air+quality)
- Raw data was uploaded to an **Amazon S3** bucket.
- Hive queries were run on **Amazon EMR** to:
  - Handle missing/null values
  - Normalize and clean pollutant readings
  - Generate a labeled dataset for ML
- The cleaned dataset was saved back to S3 for downstream analysis.

### 🔹 Phase 2: Machine Learning and Visualization with SageMaker
- **Amazon SageMaker Studio** was used for end-to-end model development.
- Dataset was loaded from S3 into a Jupyter Notebook in SageMaker.
- A **Linear Regression** model was trained using `scikit-learn` to predict `CO_GT` (Carbon Monoxide) based on selected features:
  - NO2_GT, NOx_GT, C6H6_GT, Temperature, and Relative Humidity.
- Evaluation metrics:
  - **Mean Squared Error**
  - **R² Score**
- Visualizations:
  - Actual vs Predicted CO plot
  - Residual distribution histogram
  - Coefficient bar chart
- All generated plots were stored back in S3 for sharing and documentation.

## 📊 Visualizations

| Chart | Description |
|-------|-------------|
| `actual_vs_predicted_co.png` | Scatter plot showing predicted vs actual CO values |
| `residuals_histogram.png` | Distribution of model errors |
| `coefficients_bar_chart.png` | Feature importance based on regression coefficients |

## 🧠 ML Model Used
- **Linear Regression**
  - Simple yet effective for continuous value prediction
  - Easy to interpret and visualize
  - High R² value indicates good performance on this structured dataset

## 🏗️ Architecture

Air Quality Dataset (UCI) ↓ Amazon S3 (Raw Data) ↓ EMR + Hive (Preprocessing) ↓ Amazon S3 (Processed Data) ↓ SageMaker Studio (JupyterLab) ↓ ML Model Training + Evaluation ↓ Chart Visualizations → Stored in S3

## 🔧 Tools and Technologies
- **Amazon S3** – Scalable data storage
- **Amazon EMR** – Cluster-based data processing
- **Hive** – SQL-like queries for data cleaning
- **Amazon SageMaker Studio** – ML development environment
- **Python + Scikit-learn** – Model training and evaluation
- **Matplotlib** – Visualizations

## 📁 Folder Structure

├── hive-scripts/ │ └── preprocessing_queries.sql ├── notebooks/ │ └── air_quality_model.ipynb ├── charts/ │ ├── actual_vs_predicted_co.png │ ├── residuals_histogram.png │ └── coefficients_bar_chart.png ├── README.md



## 📈 Results Summary
- **MSE**: Low, indicating small prediction errors.
- **R² Score**: > 0.96, demonstrating strong model performance.
- **Insights**:
  - Benzene (C6H6) and temperature had high influence on CO levels.
  - Model predictions closely followed actual values.
![PHOTO-2025-04-12-21-39-53](https://github.com/user-attachments/assets/42764226-16e3-4b4d-839e-05b6ceff2d65)

## 🚀 How to Run
1. Upload dataset to an S3 bucket.
2. Use Hive on EMR to preprocess and clean the data.
3. Save the cleaned data back to S3.
4. Launch SageMaker Studio and open the notebook.
5. Run the ML training and generate visualizations.
6. Save charts to S3 for access and sharing.

## 📬 Contributors
- **Nithish Karanam** – Data processing, model development, visualization

## 📃 License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for more details.
