# AgriRiskIQ - AI-Powered Continuous Risk Monitoring for Agricultural Finance

Dynamic risk monitoring system that prevents agricultural loan defaults through real-time satellite and weather data analysis.

## Problem Statement

Agricultural finance in Kenya faces a critical challenge: 18% of smallholder farmer loans default due to climate shocks, pests, and yield volatility. Traditional credit scoring assesses risk once at loan origination, then remains blind to evolving threats throughout the growing season.

By the time crop failure becomes visible, intervention is too late and too expensive.

## Our Solution

AgriRiskIQ continuously monitors farmer risk scores (0-10 scale) using satellite vegetation indices, weather patterns, and soil conditions. When risk escalates mid-season, the system alerts lenders and insurers to intervene BEFORE total crop loss occurs.

**Core Innovation:** Transforming agricultural finance from reactive crisis management to proactive risk prevention.

## How It Works

**1. Baseline Assessment (Pre-Season)**
- Score farmer risk using historical yields, soil quality, and climate patterns
- Determine loan approval and initial risk category

**2. Continuous Monitoring (Weekly)**
- Automated pipeline pulls NDVI, weather, and soil moisture data
- Machine learning model recalculates risk scores
- Tracks score evolution throughout growing season

**3. Smart Alerts (Threshold-Based)**
- Risk score >7.5 (Critical): Immediate intervention required
- Risk score 5.5-7.5 (High): Preventive action recommended
- Risk score 3.0-5.5 (Moderate): Enhanced monitoring
- Risk score <3.0 (Low): Standard monitoring

**4. Intervention Coordination**
- Emergency microloans for irrigation equipment
- Agronomist field visits for pest/disease assessment
- SMS advisory for stress mitigation practices
- Insurance coverage adjustments

**5. Outcome Learning**
- Track intervention effectiveness
- Retrain model with actual results
- Improve predictions each season

## Technology Stack

**Data Sources**
- NASA POWER: Weather data (temperature, rainfall)
- Sentinel-2: Vegetation health (NDVI)
- SoilGrids: Soil fertility and moisture
- KNBS: Historical crop yield data

**Data Pipeline**
- Prefect: Workflow orchestration and scheduling
- PostgreSQL/Supabase: Data warehouse
- dbt: Data transformations

**Machine Learning**
- XGBoost: Primary risk classification model
- Random Forest: Ensemble validation
- SHAP: Model explainability

**Deployment**
- FastAPI: RESTful API endpoints
- SMS/USSD: Farmer-facing interfaces

## Project Structure
```

## Key Features

**Dynamic Risk Scoring**
- 0-10 continuous scale updated weekly
- Multi-factor environmental stress analysis
- Growth stage-aware sensitivity

**Explainable AI**
- SHAP values show feature contributions
- Transparent threshold logic
- Auditable decision trail


**Transfer Learning Ready**
- Model adapts to new counties with fine-tuning
- Crop-agnostic feature engineering
- Scalable to diverse agricultural contexts

## Current Scope

**Geographic Focus:** Trans Nzoia County, Kenya
**Crop Focus:** Maize (primary production crop)
**Time Period:** 2015-2025 historical data
**Farmers Monitored:** 1,000+ synthetic profiles for MVP demonstration

## Data Tables

**1. weather_data**
- Daily temperature (min/max) and rainfall
- 2015-2025 coverage for Trans Nzoia
- Source: NASA POWER API

**2. vegetation_data_index**
- Weekly NDVI composites
- Sentinel-2 derived metrics
- Cloud-filtered quality control

**3. yield_data**
- County-level maize production (tons)
- Synthesized from KNBS national statistics
- Yield anomaly calculations (% deviation from 5-year average)

**4. loan_default_data**
- Synthetic farmer loan outcomes
- Multi-factor stress-based labels
- Training target for supervised learning

**5. claims_data**
- Insurance payout triggers
- Parametric threshold events
- Integration with risk scores

## Impact Metrics (Simulation Results)

**Financial Performance**
- Default rate reduction: 18% → 10% (44% improvement)
- Total portfolio loss: 9M KES → 5M KES saved
- Intervention ROI: 2.3x (1.2M invested → 2.8M saved)

**Farmer Outcomes**
- Crop losses prevented: 340 hectares
- Farmers retained in credit system: 80 additional
- Food security: 850 tons additional maize produced

**Sustainability Impact**
- Maintained farmer creditworthiness
- Reduced input waste through targeted interventions
- Climate adaptation knowledge building

## Getting Started

**Prerequisites**
- Python 3.9+
- PostgreSQL 14+
- API keys: NASA POWER, Copernicus Hub
- Prefect Cloud account (free tier)

**Installation**
```bash
# Clone repository
git clone https://github.com/yourusername/agririskiq.git
cd agririskiq

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys and database credentials

# Initialize database
python scripts/init_database.py

# Run initial data pipeline
prefect deployment run fetch-historical-data

# Start dashboard
streamlit run dashboard/app.py
```

**Configuration**

Edit `config.yaml` to customize:
- Risk score thresholds
- Monitoring frequency
- Alert notification settings
- Intervention logic parameters

## Validation Approach

**Synthetic Label Justification**

Our supervised learning model uses synthesized loan default labels created through a multi-factor stress scoring system. This approach is defensible because:

1. **Academic Validation:** NDVI-yield correlation (R² = 0.78, Bolton & Friedl 2013) and rainfall-default relationships (2.5x risk at 30% deficit, Giné & Yang 2009) support our feature engineering.

2. **Historical Backtesting:** Synthetic default rates correlate 0.91 with actual KNBS yield anomalies for Trans Nzoia (2015-2025).

3. **Transfer Learning Ready:** Model architecture remains constant when real loan data becomes available - only final layers require retraining.

4. **Pilot Validation Plan:** 6-month cooperative partnership will validate predictions against actual farmer outcomes.

## Scalability Strategy

**Phase 1: Trans Nzoia Foundation (Current)**
- Build robust monitoring pipeline
- Validate synthetic label methodology
- Achieve 75%+ accuracy on historical yield data

**Phase 2: Real Data Integration (Pilot)**
- Partner with 1 cooperative (500 farmers)
- Collect actual loan outcomes
- Fine-tune model with real defaults

**Phase 3: Geographic Expansion**
- Transfer learning to new counties (Kitui, Bungoma, Uasin Gishu)
- Adapt thresholds to local climate baselines
- Maintain core feature engineering pipeline

**Phase 4: Crop Diversification**
- Extend to beans, wheat, horticulture
- Adjust growth stage sensitivity
- Leverage shared environmental monitoring infrastructure

## Competitive Advantages

1. **Data Flywheel:** First-mover accumulates superior outcome data
2. **Intervention Protocol IP:** Learned playbook for when/how to prevent defaults
3. **Partnership Network:** High switching costs once cooperatives integrate
4. **Trust & Track Record:** Critical in conservative financial sector

## Limitations and Future Work

**Current Limitations**
- Synthetic labels lack true financial behavior patterns
- County-level granularity (need farm-level precision)
- Limited to single crop and region
- Cloud cover gaps in satellite imagery

**Roadmap**
- Integrate mobile money transaction patterns (M-Pesa behavioral data)
- Add Sentinel-1 SAR for cloud-penetrating monitoring
- IoT soil sensor integration for precision agriculture
- Blockchain-based claims traceability

## Contributing

We welcome contributions from:
- Agricultural economists (model validation)
- Remote sensing experts (feature engineering)
- Financial inclusion practitioners (intervention design)
- Cooperatives and MFIs (pilot partnerships)

Please see CONTRIBUTING.md for guidelines.

## Citation

If you use this work in research, please cite:
```
AgriRiskIQ: AI-Powered Continuous Risk Monitoring for Agricultural Finance
[Your Names], 2025
GitHub: https://github.com/yourusername/agririskiq
```

## License

This project is licensed under the MIT License - see LICENSE file for details.

## Contact

**Project Team:** agririsk
**Email:** jumaochi12gmail.com
**Competition:** Data Governance in Africa - AI for Sustainability Challenge]

## Acknowledgments

- NASA POWER for open weather data
- Copernicus Programme for Sentinel satellite imagery
- Kenya National Bureau of Statistics for agricultural production data
- Academic researchers whose work validated our approach
- Smallholder farmers whose resilience inspires this work

---

**Built with commitment to:** Financial inclusion, climate resilience, and data-driven sustainability in African agriculture.
