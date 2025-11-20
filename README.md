# 🗺️ POI Location Labeling & Log Analysis Toolkit

A production-ready toolkit for **POI (Point of Interest) geographic labeling**, **whitelist generation**, and **ASR/NLU log consistency analysis**.  
This repository provides reliable rule-based utilities used in ASR pipelines, POI Search systems, and address normalization workflows.

## 🚀 Features

### ✔ Rule-based Geographic Entity Recognition
- Parse geographic components: **country**, **province**, **city**, **county**
- Uses a hierarchical location dictionary for robust matching
- Includes safeguards to avoid false positives (e.g., ignore “xx路” street suffixes)

### ✔ Whitelist Dictionary Generation
- Automatically extract POI entity names from evaluation datasets
- Build a consistent whitelist for overriding ambiguous rule matches
- Ensures stable behavior in production environments

### ✔ City → Location Mapping
- Enrich input TSV data with missing geographic fields
- Map city names to their corresponding country/province from dictionaries

### ✔ Log Consistency Checker
- Compare NLU slot extraction results across different system outputs
- Identify mismatches for debugging, regression testing, and quality control

## 📁 Project Structure

```
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
```

## 🧩 Usage

### 1. City Join Location
```bash
python city_join_loc.py
```

### 2. Generate Whitelist Dictionary
```bash
python gen_white_dict.py
```

### 3. Rule-based Location Labeling
```bash
python label_loc_by_rule.py
```

### 4. Analyze Log Consistency
```bash
python log_analyse.py
```

## 📦 Installation

```bash
pip install -r requirements_asr.txt
pip install -r requirements_qabot.txt
pip install -r requirements_search.txt
pip install -r requirements_recommend.txt
```

## 🧠 Technical Highlights

- Four-level geographic dictionary (country → province → city → county)
- Rule-based extraction + whitelist fallback
- Prevents false matches through context-aware filtering
- Designed for batch TSV/JSONL processing
- Useful for ASR correction, POI search, and NLU verification

## 📄 License

MIT License (or another license of your choice)
