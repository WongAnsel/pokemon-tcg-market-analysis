# Pokémon TCG Market Analytics

An end-to-end data pipeline that ingests Pokémon TCG card pricing data, stores and transforms it in a cloud warehouse, and predicts 30-day price movement.

## Tech Stack

| Layer | Tool |
|---|---|
| Ingestion | Python + TCGPlayer API |
| Data Lake | AWS S3 |
| Warehouse | Snowflake |
| Transformation | dbt Core |
| Orchestration | GitHub Actions |
| Modeling | scikit-learn / Prophet |
| Dashboard | Streamlit |

## Pipeline

```
TCGPlayer API → AWS S3 → Snowflake → dbt → scikit-learn → Streamlit
```

## Setup

**Prerequisites:** Python 3.11+, Snowflake free account, AWS free tier, TCGPlayer API key

```bash
git clone https://github.com/YOUR_USERNAME/pokemon-tcg-market-analytics.git
cd pokemon-tcg-market-analytics
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env  # fill in your credentials
```

## Running the Pipeline

```bash
python ingestion/fetch_prices.py        # ingest raw data to S3
python ingestion/load_to_snowflake.py   # load S3 → Snowflake
cd dbt_project && dbt run && dbt test   # run transformations
streamlit run dashboard/app.py          # launch dashboard
```

## Project Structure

```
├── ingestion/        # API fetching and S3/Snowflake loading
├── dbt_project/      # SQL models, tests, and documentation
├── notebooks/        # EDA and analysis
├── models/           # Price prediction model
├── dashboard/        # Streamlit app
└── .github/workflows/          # GitHub Actions pipeline scheduling
```

## Roadmap

- [x] Project setup
- [ ] TCGPlayer API ingestion
- [ ] AWS S3 data lake
- [ ] Snowflake schema design
- [ ] dbt models
- [ ] EDA notebook
- [ ] Price prediction model
- [ ] Streamlit dashboard
- [ ] GitHub Actions scheduled pipeline
