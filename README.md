# Railway Intelligence Dashboard

The **Railway Intelligence Dashboard** is a cloud-hosted web application that analyzes the **North American Rail Network (NARN)** dataset to recommend rail track segments for investment based on usage, ownership, and strategic importance. Designed for data science and GIS enthusiasts, it leverages **CARTO** for spatial data storage and analysis, **FastAPI** for API services, and **Streamlit** for interactive visualizations, all powered by the **GitHub Student Developer Pack**.

## Features
- **Data Ingestion**: Loads NARN GeoJSON into CARTO, cleaning attributes like `PASSNGR`, `STRACNET`, and `MILES`.
- **Spatial Analysis**: Aggregates track mileage by owner (`RROWNER1`), state (`STATEAB`), and strategic status (`STRACNET`) using CARTO SQL queries.
- **Analytics**: Applies K-means clustering and a weighted scoring model (40% `PASSNGR`, 30% `STRACNET`, 20% `MILES`, 10% `TRACKS`) to prioritize investments.
- **Visualization**: Displays interactive maps, tables, and charts via Streamlit, showing top investment recommendations.
- **Deployment**: Hosted on **DigitalOcean** (API) and **Heroku** (dashboard), with a custom domain from **Namecheap** (e.g., `railintel.me`).
- **Security & Monitoring**: Secured with **Astra Security**’s firewall and malware scanner; monitored by **Datadog** and **New Relic**.

## Technologies
- **Backend**: FastAPI, CARTO
- **Frontend**: Streamlit, Plotly, CARTO Maps
- **Infrastructure**: DigitalOcean, Heroku, Namecheap, Termius
- **DevOps**: GitHub Actions, Bump.sh (API documentation), Polypane (responsive testing)
- **Data Processing**: Python (pandas, geopandas, cartoframes)
- **Security**: Astra Security (web application firewall, malware scanner)

## Getting Started
1. Clone the repository: `git clone https://github.com/loki-k4/railway-intelligence-dashboard.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Set up environment variables in `.env` for CARTO credentials (e.g., `CARTO_USERNAME`, `CARTO_API_KEY`).
4. Run the API: `uvicorn api.main:app --reload`
5. Launch the dashboard: `streamlit run dashboard/app.py`

## Dataset
- **Source**: Bureau of Transportation Statistics (NARN GeoJSON, https://doi.org/10.21949/1528950)
- **Attributes**: `OBJECTID`, `RROWNER1`, `PASSNGR`, `STRACNET`, `TRACKS`, `MILES`, `Shape_Length`, `STATEAB`, `STFIPS`, etc.

## License
[MIT License](LICENSE) - Free to use, modify, and distribute.

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for details.
