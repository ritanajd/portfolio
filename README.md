# portfolio
# Data Analysis Portfolio

Welcome to my data analysis portfolio! This repository showcases a collection of projects I have worked on, demonstrating my skills in data collection, processing, analysis, modeling, and visualization across various domains.

## Projects

Below is a summary of the projects included in this portfolio:



### 1. Big Data: Analyzing Weather Impact on Madrid Traffic Accidents (2022-2024)

**Goal:** To analyze the relationship between weather conditions and traffic accidents in Madrid between 2022 and 2024, aiming to inform urban planning and improve road safety.

**Data Sources:**
*   Traffic accident records (XLSX format, per year) from the Madrid City Open Data Portal.
*   Detailed hourly weather data (CSV format, per month) from Visual Crossing Weather Services.

**Methodology:**
*   **Data Collection:** Acquired data from official sources, handling download limitations for weather data.
*   **Data Preprocessing:** Cleaned and merged weather data (monthly CSVs) and accident data (yearly XLSXs). Handled missing values (e.g., removed 'preciptype', 'severerisk', 'positiva_droga' due to high null percentages). Created aggregated datasets grouped by accident event (`num_expediente`) to analyze accident scale while retaining individual details separately.
*   **Data Analysis:** Performed Exploratory Data Analysis (EDA) using tools like Data Wrangler to understand variable distributions and identify preprocessing needs.
*   **Data Architecture:** Designed a scalable cloud architecture involving DNS, Load Balancer, CDN, Frontend/Backend servers, Database Cache, and Data Warehouse (e.g., Redshift) for processing and serving insights via web/mobile applications.
*   **Data Ingestion & Validation:** Developed pipelines for ingesting, validating, and ensuring the quality of the integrated data.

**Key Insights (from report):** The project aimed to identify patterns in traffic accidents and correlate them with specific weather conditions (temperature, precipitation, wind, visibility, etc.) to provide actionable insights for improving urban safety in Madrid.

**Files:**
*   Report: `BigData_Madrid_Traffic_Accidents/BIG+DATA+FINAL+PROJECT+REPORT.pdf`

---



### 2. Emotion Analysis in Emails Using Graph Convolutional Networks (GCN)

**Goal:** To develop a robust model for classifying emails into six emotional categories (neutral, joy, fear, sadness, surprise, anger) using Graph Convolutional Networks (GCNs), leveraging graph structures to capture complex word relationships often missed by traditional methods.

**Data Source:** A dataset of 634 labeled emails across the six emotion categories, with some class imbalance (neutral being the most common, anger the least).

**Methodology:**
*   **Preprocessing:** Text converted to lowercase, punctuation and stopwords removed, tokenized, and short words filtered.
*   **Graph Construction:** Represented each email as a word co-occurrence graph. Nodes are unique words, and edges connect words appearing within a fixed-size sliding window (size 3), weighted by co-occurrence frequency. Implemented using `networkx`.
*   **Model Architecture:** Employed a GCN model with two graph convolutional layers using the propagation rule `H^(l+1) = σ(D^(-1/2) A D^(-1/2) H^(l) W^(l))`. Node features were initialized with one-hot vectors (or GloVe embeddings in a variant). Global mean pooling was applied, followed by a dense layer and a softmax output layer.
*   **Training & Optimization:** Trained for 100 epochs using an 80-10-10 train/validation/test split. Used cross-entropy loss (weighted to handle class imbalance), Adam optimizer (learning rate 0.001), dropout (0.5), and early stopping.
*   **Evaluation:** Compared GCN performance against baseline models (LSTM, SVM, Random Forest, Naive Bayes). Analyzed confusion matrices (for GAT and GAT+GloVe variants) and attention weights to understand model behavior and errors.

**Key Results:**
*   The GCN model achieved the highest performance with 82% accuracy and 79% F1 score, outperforming baselines.
*   Confusion matrix analysis showed good performance on distinct emotions like anger and joy but revealed confusion between similar emotions (e.g., fear/neutral, neutral/joy).
*   Attention weight analysis indicated the model focuses differently on linguistic patterns for various emotions.
*   Error analysis highlighted challenges like ambiguous emotional content and formal language obscuring emotions.

**Files:**
*   Report: `Emotion_Analysis_GCN/Emotion Analysis in Emails Using Graph Convolutional Networks-3.pdf`

---



### 3. HPC MLOps Pipeline & EV Charging Station Analysis

**Goal:** To develop an AI-driven solution and MLOps pipeline for optimizing the conversion of gas stations into High-Power Charging (HPC) hubs for Electric Vehicles (EVs). The project aims to address the financial risks and lack of data-driven tools for site assessment by integrating diverse datasets, forecasting demand, analyzing competitor synergy, and calculating ROI.

**Components & Methodology:**
*   **AI-Driven Site Assessment (Design AI Report):**
    *   **Problem:** High costs and risks associated with converting gas stations to HPC hubs without data-driven site selection.
    *   **Solution:** Proposed an AI solution using Generative AI, machine learning (Reinforcement Learning - PPO for dynamic pricing, ARIMA for EV adoption forecasting), and geospatial analytics (GeoPandas for competitor analysis).
    *   **Data Sources:** Kaggle EV charging datasets, TomTom Traffic API, OpenChargeMap.
    *   **Key Results:** Demonstrated potential for faster analysis, reduced capital waste, revenue growth through dynamic pricing, and risk mitigation.
*   **MLOps Pipeline Implementation (Integration Scripts & Instructions):**
    *   **Objective:** Create a reproducible pipeline (initially guided by Manus instructions) to automate data ingestion, processing, modeling, and ROI calculation for HPC site evaluation.
    *   **Part 1 (Setup & Data Ingestion):** Sets up the environment, configures Kaggle API, defines HPC cost parameters (YAML), downloads multiple EV charging datasets from Kaggle, and attempts to fetch TomTom O/D data (with fallback).
    *   **Part 2 (Merging, Modeling & ROI):** Merges usage data from different sources, performs simplified usage forecasting (without sklearn initially), calculates ROI for different HPC tiers (350KW, 1000KW) based on cost parameters and forecasts, and includes optional competitor synergy analysis (adjusting forecasts based on nearby competitors).
    *   **Part 3 (Advanced Modeling - Placeholder):** Intended for more advanced modeling like Reinforcement Learning and time-series analysis (details likely in the full project, scripts provided suggest integration steps).
    *   **Data Collector:** Script focused on setting up Kaggle credentials and downloading/synthesizing EV charging data, potentially using TomTom API as well.
*   **Dashboard & Visualization:**
    *   **HPC Dashboard (`HPC Dashboard.py`):** Likely a Python script (potentially using Dash/Plotly or similar) to visualize the results of the analysis, forecasts, and ROI calculations.
    *   **Enhanced Gas Station Map (`Enhanced Gas Station Map.js`, `Green Energy Theme.css`):** Suggests a web-based map visualization, possibly integrated with the dashboard, to display station locations, competitor data, and potentially real-time information. The CSS file provides styling.
    *   **Notebook (`HPC Dashboard MLOPS Instructions.ipynb`):** Jupyter notebook providing instructions or code related to the MLOps pipeline and dashboard setup.

**Technologies:** Python (Pandas, NumPy, Requests, YAML, Kaggle API, potentially GeoPandas, Dash/Plotly), JavaScript, CSS, MLOps principles, Machine Learning (ARIMA, PPO - as per report), Geospatial Analysis.

**Files:**
*   Reports: 
    *   `HPC_MLOps_Pipeline/Reports/Design AI Final Report.pdf`
    *   `HPC_MLOps_Pipeline/Reports/MANUS instructions MLOPS gp.docx`
*   Code:
    *   `HPC_MLOps_Pipeline/Code/Data Collector.py`
    *   `HPC_MLOps_Pipeline/Code/HPC Integration Part 1.py`
    *   `HPC_MLOps_Pipeline/Code/HPC Integration Part 2.py`
    *   `HPC_MLOps_Pipeline/Code/HPC Integration Part 3.py`
    *   `HPC_MLOps_Pipeline/Code/HPC Dashboard.py`
    *   `HPC_MLOps_Pipeline/Code/Enhanced Gas Station Map.js`
    *   `HPC_MLOps_Pipeline/Code/Green Energy Theme.css`
*   Notebooks:
    *   `HPC_MLOps_Pipeline/Notebooks/HPC Dashboard MLOPS Instructions.ipynb`

---



### 4. Recommendation System Project (Beer Recommendations)

**Goal:** To explore and implement different recommendation system techniques, likely focused on recommending beers based on user reviews or item characteristics.

**Components & Methodology:**
This project appears to be divided into three main approaches based on the provided files:

*   **Content-Based Filtering (`Content_Based/`):**
    *   Uses item features to recommend similar items.
    *   The notebook `RCM_CB.ipynb` likely implements a content-based recommendation model.
    *   The data used might be in `dataset_CB.csv`, containing features of the beers or user interactions suitable for this approach.
*   **Singular Value Decomposition (SVD) (`SVD/`):**
    *   A matrix factorization technique often used in collaborative filtering to uncover latent factors.
    *   The notebook `DATA_SVD.ipynb` likely implements SVD on user-item interaction data.
    *   The data `cleaned_beer_reviews (1).csv` seems to be the primary dataset for this, containing user reviews which form the basis for the user-item matrix.
*   **Collaborative Filtering & Cold Start (`Collaborative_Filtering_Cold_Start/`):**
    *   Recommends items based on the preferences of similar users (user-based CF) or similarity between items based on user interactions (item-based CF).
    *   Addresses the "cold start" problem, which occurs when new users or items have insufficient data for recommendations.
    *   The notebook `RMC_CF_coldstart.ipynb` likely implements collaborative filtering algorithms and strategies to handle new users/items.
    *   The notebook `dataset_CF-coldstart.ipynb` might be related to preparing or analyzing the dataset specifically for the cold start scenario.

**Technologies:** Python, Jupyter Notebooks, Pandas, likely libraries like Scikit-learn, Surprise, or other recommendation system frameworks.

**Files:**
*   Content-Based:
    *   `Recommendation_System/Content_Based/RCM_CB.ipynb`
    *   `Recommendation_System/Content_Based/dataset_CB.csv`
*   SVD:
    *   `Recommendation_System/SVD/DATA_SVD.ipynb`
    *   `Recommendation_System/SVD/cleaned_beer_reviews (1).csv`
*   Collaborative Filtering & Cold Start:
    *   `Recommendation_System/Collaborative_Filtering_Cold_Start/RMC_CF_coldstart.ipynb`
    *   `Recommendation_System/Collaborative_Filtering_Cold_Start/dataset_CF-coldstart.ipynb`

---

