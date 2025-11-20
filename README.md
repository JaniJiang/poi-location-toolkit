🗺️ POI Location Labeling & Log Analysis Toolkit

A production-ready toolkit for POI (Point of Interest) geographic labeling, whitelist generation, and ASR/NLU log consistency analysis.
This repository provides reliable rule-based utilities used in ASR, POI Search, and address normalization pipelines.

🚀 Features
✔ Rule-based Geographic Entity Recognition

Parse and assign country, province, city, and county

Leverages a hierarchical location dictionary

Includes special-case handling to avoid false matches (e.g., stop matching “xx路”)

✔ Whitelist Dictionary Generation

Automatically extract POI entities from evaluation data

Build a curated whitelist to override rule-based predictions

Ensures stable behavior in production scenarios

✔ City → Location Mapping

Join city names to their corresponding country and province

Enrich data tables (TSV) with missing geographic fields

✔ Log Consistency Checker

Compare NLU slot values between different CUA outputs

Identify mismatches for debugging, evaluation, and regression monitoring

📁 Project Structure
project_root/
│
├── city_join_loc.py
├── gen_white_dict.py
├── label_loc_by_rule.py
├── log_analyse.py
│
├── data/
│   ├── dict/
│   │   └── candidate_loc.jsonl
│   └── cloud_share/
│       └── cua/asr/poi_search/analyse/
│           ├── city_join_loc/
│           ├── label_loc_by_rule/
│           └── log_analyse/
│
├── requirements_asr.txt
├── requirements_qabot.txt
├── requirements_recommend.txt
└── requirements_search.txt

🧩 Usage
1. City Join Location

Enrich a TSV file with country and province fields:

python city_join_loc.py

2. Generate Whitelist Dictionary
python gen_white_dict.py


Output:

white_dict.json

3. Rule-based Location Labeling
python label_loc_by_rule.py


Generates:

country

province

city

county

has_loc

4. Analyze Log Consistency
python log_analyse.py


Prints mismatched shopAddress values between NLU outputs.

📦 Installation

Install dependencies based on your use case (ASR, QA Bot, Search, Recommendation):

pip install -r requirements_asr.txt
pip install -r requirements_qabot.txt
pip install -r requirements_search.txt
pip install -r requirements_recommend.txt

🧠 Technical Highlights

Hierarchical geographic dictionary (country → province → city → county)

Robust rule-based text matching with safe fallbacks

Whitelist-first strategy for precise overrides

Useful for POI search pipeline, ASR correction, and NLU slot verification

Production-tested scripts designed for bulk TSV/JSONL processing

📄 License

MIT License
