# JeevanJal OS — Maharashtra Drought Dashboard

A drought-monitoring and tanker-dispatch demonstration for Maharashtra. The repository contains two separate interfaces:

- `index.html` is a static browser dashboard. Its village values and dispatch, OTP, and Cedar-policy messages are local demo simulations. It does not send SMS, call AWS Strands/Cedar, or fetch live telemetry.
- `app.py` is a Streamlit dashboard. It requests weather data from Open-Meteo and uses a local Cedar-policy simulation. Strands Agents is optional; the app can run without it.

## Run locally

Use Python 3.10 or later:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

To view the static dashboard, open `index.html` in a browser or serve the project directory:

```powershell
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## GitHub deployment

Pushing to `main` deploys `index.html` to GitHub Pages using the workflow in `.github/workflows/pages.yml`. Enable **Settings → Pages → Build and deployment → GitHub Actions** in the repository if Pages is not enabled automatically.

GitHub Pages serves only the static dashboard; it does not run the Streamlit app. To host `app.py`, use a Python app host such as Streamlit Community Cloud and select this repository with `app.py` as the entry point.

## Railway deployment

Deploy the repository as a Railway service. Railway installs dependencies from `requirements.txt` and uses the root `Procfile` to start Streamlit on the Railway-provided `$PORT`. Do not set the start command to `python app.py`; Streamlit apps must be started with `streamlit run`.

## Dependencies

Install the Python packages listed in `requirements.txt`. No AWS account is required for the local demos.
