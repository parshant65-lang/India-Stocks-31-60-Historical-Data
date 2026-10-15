# India Public Equities (Constituents 31 to 60) - 1-Minute Historical Kline Archive

An institutional-grade, open-source archive of cleaned, standardized, and validated **1-minute intraday historical candlestick data** for **India's Top Liquid Companies (Batch 31 to 60)** with daily automated cloud ingestion.

---

## 🏛️ Directory Architecture & Strict Date-Wise Hierarchy

Every stock is strictly organized into daily CSVs partitioned by Year/Month/Date:

```text
India-Stocks-31-60-Historical-Data/
├── ABB/
│   └── 1m/
│       ├── README.md
│       └── 2026/
│           └── 10/
│               ├── ABB_1m_2026-10-01.csv
│               ├── ABB_1m_2026-10-05.csv
│               └── ABB_1m_2026-10-09.csv
├── DMART/
│   └── 1m/...
└── ... [All 30 Companies]
```

---

## 📊 Dataset Overview
- **Constituents:** 30 Benchmark Companies (Rank 31 to 60)
- **Timeframe:** 1 Minute (`1m`)
- **Total Archived Daily Files:** `330` sessions
- **Total 1-Minute Candles:** `118,446` candles
- **Last Ingested:** `2026-10-15 15:35:39 UTC`
- **Trading Sessions:** Monday – Friday, 09:15 to 15:30 IST (03:45 to 10:00 UTC)

---

## 📑 Data Schema (Uniform Across All Files)

| Column Name | Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `timestamp` | `int64` | Candle open time in Unix milliseconds (UTC) | `1791517500000` |
| `datetime_utc` | `string` | Standard ISO human-readable UTC timestamp | `2026-10-09 03:45:00` |
| `open` | `float64` | Opening price in INR | `7845.00` |
| `high` | `float64` | Highest price reached during the 1-minute window | `7860.00` |
| `low` | `float64` | Lowest price reached during the 1-minute window | `7830.00` |
| `close` | `float64` | Closing price of the 1-minute candle | `7852.50` |
| `volume` | `float64` | Cumulative volume traded in the 1-minute candle | `1420` |

---

## ⚡ 1-Line Pandas Stream Loader (No Clone Required)

Stream any stock's 1-minute data directly from GitHub's raw CDN into Pandas in 1 second:

```python
import pandas as pd

# Load ABB 1-minute data for October 09, 2026
url = "https://raw.githubusercontent.com/parshant65-lang/India-Stocks-31-60-Historical-Data/main/ABB/1m/2026/10/ABB_1m_2026-10-09.csv"
df = pd.read_csv(url)
print(df.head())
```

---

## 🔄 Daily Automated Cloud Ingestion
A GitHub Actions workflow runs every weekday post-market (**Monday to Friday at 15:30 IST / 10:00 UTC**) to query Yahoo Finance, slice newly closed 1-minute sessions into daily CSVs, de-duplicate timestamps, and commit updates automatically.
