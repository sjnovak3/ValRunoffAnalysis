# ValRunoffAnalysis

Live-data runoff analysis using Jupyter.  
Re-run the notebook at any time to pull the latest streamflow and precipitation data from the internet.

## Quick start

```bash
# 1. Clone the repo
git clone https://github.com/sjnovak3/ValRunoffAnalysis.git
cd ValRunoffAnalysis

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Open the notebook
jupyter lab runoff_analysis.ipynb
# or
jupyter notebook runoff_analysis.ipynb
```

Inside the notebook, select **Kernel → Restart & Run All** to fetch fresh data.

## Adding your own data sources

Open `runoff_analysis.ipynb` and edit the **Configuration** cell near the top.
Add entries to `CUSTOM_DATA_SOURCES`:

```python
CUSTOM_DATA_SOURCES = [
    {"label": "My gauge data",  "url": "https://example.com/data.csv",  "format": "csv"},
    {"label": "Basin model out","url": "https://example.com/model.json", "format": "json"},
]
```

## Automated daily refresh

| Method | Command |
|--------|---------|
| nbconvert (cron / Task Scheduler) | `jupyter nbconvert --to notebook --execute runoff_analysis.ipynb` |
| Papermill | `papermill runoff_analysis.ipynb runoff_analysis_output.ipynb` |
| GitHub Actions | Create `.github/workflows/daily_refresh.yml` |

## Data sources

| Source | API | Notes |
|--------|-----|-------|
| USGS NWIS | `https://waterservices.usgs.gov/` | Real-time streamflow — no API key required |
| NOAA NWS | `https://api.weather.gov/` | Recent precipitation observations — no API key required |