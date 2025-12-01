# Census-Data-Standardization-and-Analysis-Pipeline

This project provides a single-cell executable Colab notebook to process, clean, analyze, and visualize Indian census data (2011) with live dashboards using Streamlit, and storage in MongoDB Atlas and SQLite.

It also handles new state formation (Telangana, Ladakh), missing data imputation, and provides predefined queries for demographic insights.

🚀 Features

Data Ingestion

Reads census data from Excel.

Reads Telangana district list from DOCX.

Handles raw data fetching from URLs.

Data Cleaning & Transformation

Renames columns consistently.

Standardizes state and UT names.

Handles newly formed states (Telangana, Ladakh).

Fills missing values using column sums.

Database Integration

MongoDB Atlas: stores cleaned census records with deterministic _id keys.

SQLite: stores census facts and dimensions (states and districts) with constraints and indices.

Streamlit Dashboard

Interactive queries for district- or state-level demographics.

Select queries from a dropdown menu:

Population, literacy, workers, household fuel, religion, internet access, education, transport/media, house conditions, household size, BPL, and more.

Download query results as CSV.

Colab Cloudflared Tunnel

Exposes Streamlit app via a public URL directly from Colab.

📦 Dependencies
pip install pandas requests python-docx pymongo streamlit openpyxl


Other required tools:

cloudflared (downloaded automatically in Colab)

⚙️ Configuration

Excel URL: Census 2011 data

DOCX URL: Telangana districts

MongoDB URI:

MONGO_URI = "mongodb+srv://bhuvan:12345@cluster0.obh30fm.mongodb.net/censusdb?retryWrites=true&w=majority"


SQLite DB: census.db

Facts Table: census_clean

🛠 Pipeline Steps

Install dependencies and cloudflared.

Fetch raw data from URLs.

Rename columns and standardize states/UTs.

Handle new states formation (Telangana, Ladakh).

Impute missing values using column sums.

Upload data to MongoDB Atlas.

Upload data to SQLite with dimension tables and constraints.

Run Streamlit dashboard for interactive analysis.

Expose Streamlit via Cloudflared tunnel for public access.

📊 Streamlit Dashboard

Access queries such as:

Total population per district

Literate males/females

Workers percentage

LPG/PNG households

Religion composition

Internet access

Education distribution

Transport/media ownership

House conditions

Household size

Owned vs rented households

Latrine types

Water source proximity

Average household income (Power Parity)

Married couples distribution

Households below poverty line

Literacy rate by state

The dashboard allows filtering by State/UT and District, and CSV download of results.

⚡ Run in Colab

Open the notebook in Colab.

Run the single code cell.

Wait for output like:

🌐 Public URL: https://boys-specials-photographer-creature.trycloudflare.com


Open the URL to interact with the dashboard.

🧩 Notes

Missing data warnings are automatically handled and displayed.

MongoDB and SQLite integration ensures easy querying.

Streamlit session_state warnings in Colab are normal and can be ignored.

🛑 Stop Services

To stop Streamlit & Cloudflared in Colab:

streamlit_proc.terminate()
cloudflared_proc.terminate()
