#  Slooze Wine & Spirits — Inventory Analytics Solution

> **Challenge:** Slooze Data Science Hiring Challenge  
> **Dataset:** [kaggle.com/datasets/sloozecareers/slooze-challenge](https://www.kaggle.com/datasets/sloozecareers/slooze-challenge)

---

##  What's Covered...

| # | Analysis | Techniques Used |
|---|----------|----------------|
| 1 | **EDA & KPI Dashboard** | Aggregations, heatmaps, trend charts |
| 2 | **ABC Analysis** | Pareto / cumulative revenue classification |
| 3 | **EOQ Analysis** | Wilson EOQ formula, cost minimization |
| 4 | **Reorder Point Analysis** | Safety stock (95% SL), lead-time-demand convolution |
| 5 | **Lead Time Analysis** | Vendor benchmarking, distribution analysis |
| 6 | **Demand Forecasting** | Holt-Winters ETS + SARIMA, MAPE/RMSE evaluation |
| 7 | **Margin Analysis** | Gross margin per product |
| 8 | **Slow Movers / Dead Stock** | Velocity segmentation |
| 9 | **Inventory Turnover** | DSI, turnover ratio |
| 10 | **Vendor Concentration** | HHI index, Lorenz curve |
| 11 | **Seasonal Decomposition** | Additive decomposition |

---

##  Quick Start

### 1. Clone / Download
```bash
git clone <your-repo-url>
cd slooze-analytics
```

### 2. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate          # macOS/Linux
# venv\Scripts\activate           # Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Kaggle API
1. Go to [kaggle.com](https://www.kaggle.com) → Account → **Create API Token**
2. Download `kaggle.json`
3. Place it at:
   - macOS/Linux: `~/.kaggle/kaggle.json`
   - Windows: `C:\Users\<username>\.kaggle\kaggle.json`
4. Set permissions (macOS/Linux): `chmod 600 ~/.kaggle/kaggle.json`

### 5. Run the Notebook
```bash
jupyter notebook slooze_analysis.ipynb
```
Then **Run All Cells** (`Kernel → Restart & Run All`)

---

##  Requirements (`requirements.txt`)
```
kagglehub>=0.2.0
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.12.0
plotly>=5.14.0
statsmodels>=0.14.0
scikit-learn>=1.3.0
openpyxl>=3.1.0
scipy>=1.11.0
jupyter>=1.0.0
ipykernel>=6.0.0
```

---

##  Outputs

After running, the following files are generated in the working directory:

| File | Description |
|------|-------------|
| `slooze_analysis_outputs.xlsx` | Key tables: ABC classes, EOQ, ROP, Forecast |
| `01_monthly_sales_trend.png` | Revenue & units over time |
| `02_top_products_revenue.png` | Top 15 products |
| `03_sales_by_location.png` | Sales by store/city |
| `04_sales_heatmap.png` | Day-of-week × month heatmap |
| `05_abc_analysis.png` | Pareto curve + class distribution |
| `06_eoq_analysis.png` | EOQ distribution + cost ranking |
| `07_reorder_points.png` | ROP + safety stock per product |
| `08_lead_time_analysis.png` | Lead time distribution + vendor comparison |
| `09_demand_forecast.png` | 12-week forecast (HW + SARIMA) |
| `10_margin_analysis.png` | Gross margin distribution |
| `11_inventory_turnover.png` | Turnover ratio distribution |
| `12_vendor_concentration.png` | HHI + Lorenz curve |
| `13_seasonal_decomposition.png` | Trend / seasonality / residual |

---

##  Key Analytical Choices

### ABC Classification Thresholds
| Class | Cumulative Revenue | Priority |
|-------|--------------------|----------|
| A | 0–80% | Critical — daily monitoring |
| B | 80–95% | Important — weekly review |
| C | 95–100% | Low — monthly review / consider rationalization |

### EOQ Assumptions
- **Ordering cost:** $50 per order (configurable in cell 4)
- **Holding rate:** 20% of unit cost per year (configurable)

### Reorder Point — Service Level
- **Z = 1.645** → 95% in-stock probability
- Adjust `SERVICE_LEVEL_Z` in cell 5 for different service targets

### Forecast Models
- **Holt-Winters ETS:** Best for data with trend + additive seasonality
- **SARIMA(1,1,1)(1,0,1,52):** Captures autoregressive patterns at 52-week cycle
- Model selection: lower MAPE on 8-week holdout test

---

## Project Structure
```
slooze-analytics/
├── slooze_analysis.ipynb     ← Main notebook (all analysis)
├── requirements.txt
├── README.md
└── outputs/                  ← Generated plots & Excel file
```

---

##  Author
Anjali Yadav | anjalisydv@gmail.com
