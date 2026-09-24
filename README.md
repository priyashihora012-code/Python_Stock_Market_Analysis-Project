<div align="center">

# -- ! Stock Market Analysis (Adani Ports) ! --
### *Historical Stock Data Analysis with Trend & Moving Average Visualization*

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-DataFrames-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge&logo=plotly&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4C72B0?style=for-the-badge&logo=python&logoColor=white)](https://seaborn.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)

<br/>

> *"The market speaks in candles and trends — data analysis helps translate it."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🔄 Project Workflow](#-project-workflow)
- [🧹 Part A — Data Cleaning](#-part-a--data-cleaning)
- [📊 Part B — Price & Trend Analysis](#-part-b--price--trend-analysis)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Stock Market Analysis** project explores the historical stock data of **Adani Ports** using **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**. It covers price trend visualization, trading volume analysis, moving averages, and correlation among key price variables (Open, High, Low, Close, VWAP).

This project is designed to:
- Practice cleaning and preparing time-series financial data
- Visualize closing price and trading volume trends over time
- Compute and interpret a 20-day moving average
- Explore correlations and relationships among price variables

---

## 🎯 Problem Statement

> **Objective:** Analyze the historical stock data of Adani Ports to understand price trends, trading activity, and relationships among price variables.

The dataset (`adaniports.csv`) contains daily trading records including open, high, low, close prices, volume, turnover, and trade counts. The task is to clean the data and use visual analysis to uncover trends, moving averages, and correlations.

| 📂 Column | 📄 Type | 🔍 Description |
|------------|---------|----------------|
| `Date` | Date | Trading date |
| `Open`, `High`, `Low`, `Close` | Numeric | Daily price points |
| `Prev Close`, `Last`, `VWAP` | Numeric | Additional price metrics |
| `Volume`, `Turnover` | Numeric | Trading activity metrics |
| `Trades` | Numeric | Number of trades executed |
| `Deliverable Volume`, `%Deliverble` | Numeric | Delivery-based trading metrics |

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 🧹 **Missing Value Handling** | Fills missing `Trades` values using the median |
| 📅 **Date Parsing** | Converts `Date` column to proper datetime format |
| 📈 **Closing Price Trend** | Line chart of closing price over time |
| 📊 **Trading Volume Trend** | Line chart of daily trading volume |
| 📉 **20-Day Moving Average** | Smooths short-term price fluctuations |
| 📦 **Distribution & Boxplot** | Histogram and boxplot of closing prices |
| 🔥 **Correlation Heatmap** | Relationships among numeric price variables |
| 🔗 **Pair Plot** | Pairwise relationships between Open, High, Low, Close |
| 🏆 **Top 10 Closing Prices** | Bar chart of the highest closing price days |

---

## 🏗️ Project Structure

```
📦 stock_market/
│
├── 📄 stock.ipynb            ← Main Jupyter Notebook (analysis)
│
├── 📄 adaniports.csv          ← Source dataset
│
└── 📄 README.md               ← Project documentation
```

---

## 🔄 Project Workflow

```
Load Dataset (adaniports.csv)
      │
      ▼
┌─────────────────────────────┐
│  Inspect Data (head/tail/    │
│  info/describe/isnull)       │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│  Clean Data                  │  ← Fill missing Trades (median),
│                               │    parse Date column
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│  Trend Analysis              │  ← Closing price & volume trends
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│  Moving Average & Correlation│  ← 20-day MA, heatmap, pair plot
└────────────┬────────────────┘
             │
             ▼
       Draw Conclusions ✅
```

---

## 🧹 Part A — Data Cleaning

### 📝 1. Initial Inspection

The dataset contains **3322 records and 15 columns** of Adani Ports historical stock data. Missing values were found only in the `Trades` column, and zero duplicate records were present.

### 🗑️ 2. Cleaning Steps

**Logic:**
```python
df["Trades"] = df["Trades"].fillna(df["Trades"].median())
df["Date"] = pd.to_datetime(df["Date"], format="%d-%m-%Y")
```

---

## 📊 Part B — Price & Trend Analysis

### 📈 3. Closing Price & Volume Trends

> Line charts track the closing price and trading volume across the full date range, revealing fluctuations in market activity.

```python
plt.plot(df["Date"], df["Close"])
plt.plot(df["Date"], df["Volume"])
```

### 📉 4. 20-Day Moving Average

> A rolling 20-day moving average is calculated on the closing price to smooth short-term noise and highlight the overall trend.

```python
df["MA20"] = df["Close"].rolling(window=20).mean()
```

### 🔥 5. Distribution, Correlation & Pair Plot

> A histogram and boxplot examine the closing price distribution and outliers, a correlation heatmap explores relationships among numeric features, and a pair plot visualizes pairwise relationships between Open, High, Low, and Close prices.

```python
sns.heatmap(df.select_dtypes(include=np.number).corr(), annot=True, cmap="coolwarm")
sns.pairplot(df[["Open","High","Low","Close"]])
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| 🐍 **Python 3.8+** | Core programming language |
| 🐼 **Pandas** | Data cleaning and time-series manipulation |
| 🔢 **NumPy** | Numerical operations |
| 📊 **Matplotlib** | Trend lines and bar charts |
| 🎨 **Seaborn** | Heatmap, pair plot, histogram, boxplot |
| 📓 **Jupyter Notebook** | Interactive analysis environment |

---

## 📈 Results & Insights

- 🧹 Missing values in the `Trades` column were filled using the median; zero duplicate records were found
- 📈 Closing prices fluctuated over time, reflecting changing market trends
- 📊 Trading volume varied significantly across different trading days
- 📉 The 20-day moving average smoothed short-term fluctuations effectively
- 📦 Histogram and box plots highlighted the closing price distribution and outliers
- 🔗 Scatter/pair plots showed a positive relationship between Open and Close prices
- 🔥 The heatmap revealed strong positive correlation among Open, High, Low, Close, and VWAP

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Beginner Friendly** | Introduces time-series financial data analysis |
| 📉 **Real Trading Concepts** | Demonstrates moving averages used in technical analysis |
| 📊 **Multiple Visualization Types** | Line, bar, histogram, boxplot, heatmap, and pair plot |
| 📖 **Readable Code** | Clear, step-by-step notebook cells with markdown observations |
| 🧪 **Extensible** | Can be extended with additional indicators (RSI, MACD, etc.) |

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

---

## 👤 Author

<div align="center">

### Priya Shihora

[![GitHub](https://img.shields.io/badge/GitHub-yourhandle-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/isamaliya16)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/PriyaShihora-686533312/)

**🎓 Role:** Data Analysis Enthusiast | Python Developer \
**📍 Location:** India\
**🛠️ Skills:** Python · Pandas · Matplotlib · Seaborn · EDA

</div>

---

## 🙏 Acknowledgements

- 📚 [Python Official Docs](https://docs.python.org/3/) — Official Python language reference
- 🐼 [Pandas Documentation](https://pandas.pydata.org/docs/) — Data manipulation reference
- 🎨 [Seaborn Documentation](https://seaborn.pydata.org/) — Statistical visualization guide
- 💬 [Stack Overflow Community](https://stackoverflow.com/) — Problem-solving support
- 📖 [Kaggle Learn](https://www.kaggle.com/learn) — Data analysis courses

---

<div align="center">

---

*Made with ❤️ and ☕ — Last updated: 20 July, 2026*

</div>
