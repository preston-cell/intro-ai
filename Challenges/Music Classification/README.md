# Music Genre Classification with Traditional Audio Features

## 1 · Project Overview
This project explores how well tempo, spectral statistics, MFCCs, etc.—can distinguish musical genres.

We merged two open CSV datasets into one 1 000‑track corpus of 10 genres (blues, classical, country, disco, hip‑hop, jazz, metal, pop, reggae, rock).  
After label clean‑up and duplicate/NaN checks, we took several iterative steps:

* **Random Forest** – quick baseline with different feature subsets  
* **Feature‑importance analysis** – isolated the six most informative features  
* **Regularised Random Forest** – shallower trees 
* **XGBoost** – gradient boosting

---

## 2 · Technologies Used

| Purpose | Library / Framework |
|---------|--------------------|
| Data | **pandas**, **numpy** |
| Classical ML | **scikit‑learn** (`RandomForestClassifier`, `train_test_split`, metrics) |
| Gradient boosting | **XGBoost** (`xgboost.XGBClassifier`) |
| Visualisation | **matplotlib** (feature‑importance bars, tree plots) |
| Runtime | **Kaggle** Python Docker image (CPU session) |

---

## 3 · How to Run

### A. Kaggle Notebook  
1. Fork the original notebook (link in repo).  
2. Attached datasets `musicfeatures` & `musicfeatures2` are pre‑mounted.  
3. Click **Run All** and review printed metrics / tweak hyper‑parameters.

## 4. Challenges Faced  
* **Label clean‑up** – numeric genre codes (`1`, `2`) mapped back to `pop`, `classical`.  
* **Class imbalance** – classical & pop dominated early splits; switched to stratified sampling.  
* **Over‑fitting forests** – deep trees hit 97 % train accuracy but <50 % validation; pruning helped.  
* **Feature limitations** – six top features plateaued at ~50 % accuracy; adding more MFCCs pushed ≥60 %.  
* **Runtime limits** – model sizes kept small to fit Kaggle CPU quotas.

---

## 5. Future Improvements  
* **Increase dataset size** so each genre has similar sample counts.  
* **Persist the best model** with `joblib.dump` and add a lightweight CLI script to predict the genre of any new WAV file.

---
