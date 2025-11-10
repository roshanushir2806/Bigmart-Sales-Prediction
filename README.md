# Bigmart-Sales-Prediction
# BigMart Sales Forecasting Pipeline

This project showcases a complete **Data Engineering + Machine Learning pipeline** using BigMart retail sales data.  
It covers everything from **data ingestion** and **database creation** to **model training** and **deployment via Streamlit**.

👉 **Live Demo:** (https://bigmart-sales-prediction-mcbg2wypbpeprxa9cp9jfh.streamlit.app/)
---

##  Project Overview

The **BigMart Sales Forecasting Pipeline** aims to predict the sales of different products across various stores for a large retail chain — **BigMart**.  
This project highlights how raw XML data files can be transformed into a **machine learning-ready dataset**, trained using regression algorithms, and deployed through a **Streamlit web interface** for interactive predictions.

It is designed to reflect a **real-world Data Engineering workflow**:
- Data is collected from multiple sources
- Loaded into a structured **MySQL database**
- Transformed and processed using Python scripts
- Trained using **Scikit-learn** models
- Deployed with **Streamlit** for easy end-user access

---

##  Problem Statement

Retail companies like BigMart deal with thousands of products sold across numerous stores in various cities.  
To optimize operations and forecast inventory, BigMart wants to **predict the sales** of each product based on historical data and product/store features.

This pipeline provides a **reusable, scalable solution** that can:
- Process data automatically from multiple XML inputs  
- Train a regression model to forecast sales  
- Allow users to input product and outlet details to get **real-time predictions**  

---

##  Architecture Overview

```mermaid
flowchart TD
    subgraph Ingestion [📥 Data Ingestion]
        A1[📄 df_item.xml] --> A4[(MySQL: item_info)]
        A2[📄 df_outlet.xml] --> A5[(MySQL: outlet_info)]
        A3[📄 df_sales.xml] --> A6[(MySQL: sales_info)]
    end

    subgraph Processing [⚙️ Data Processing]
        A4 --> B1[🔗 Merge Tables]
        A5 --> B1
        A6 --> B1
        B1 --> B2[🧹 Cleaning & Feature Engineering]
        B2 --> B3[🔀 Train/Test Split]
    end

    subgraph Modeling [🤖 Model Training]
        B3 --> C1[📈 GradientBoostingRegressor]
        C1 --> C2[💾 Save bigmart_best_model.pkl]
    end

    subgraph Deployment [🚀 Streamlit App]
        C2 --> D1[🌐 Streamlit Web Interface]
        D1 --> D2[📊 Predict Sales]
    end
