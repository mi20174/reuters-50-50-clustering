# Reuters-50-50 Dataset – Istraživanje podataka

Projekat iz predmeta **Istraživanje podataka 2** – klasterovanje Reuters-50-50 tekstualnog dataseta korišćenjem algoritama nenadgledanog mašinskog učenja.

---

## 📋 Opis projekta

Ovaj projekat predstavlja analizu **Reuters-50-50** dataseta koji sadrži:

- **5000 tekstualnih dokumenata**
- **50 autora**
- **100 novinskih clankova po autoru**

Cilj projekta je analiza tekstualnih podataka i primena **klasterovanja** kako bi se otkrile prirodne grupe dokumenata bez korišćenja oznaka klasa.

Projekat uključuje:

- ✅ Učitavanje i pripremu tekstualnih podataka  
- ✅ Preprocesiranje teksta  
- ✅ Transformaciju teksta u numerički oblik (**TF-IDF**)  
- ✅ Redukciju dimenzionalnosti (**PCA**)  
- ✅ 2D i 3D vizualizaciju dokumenata  
- ✅ Implementaciju algoritama klasterovanja  
- ✅ Evaluaciju kvaliteta klastera  
- ✅ Analizu i interpretaciju rezultata  

---

## 📁 Struktura projekta

```
Reuters50_Project/

├── data/                     # Podaci
│   └── reuters50└──C50train  # Originalni dataset
│                └──C50test
├── models/                   # Sačuvani modeli
│   ├── tfidf_vectorizer.pkl
│   ├── min_max_scaler.pkl
│   ├── .pkl
│   
│
├── notebooks/                # Jupyter notebook
│   └── Reuter_50_50_Klasterovanje.ipynb
│
├── results/                  # Rezultati i grafikoni
│   ├── *.png
│
├── report/                   # Seminarski rad
│   └── report.pdf
│
└── README.md
└── requirements.txt

```

---

## 🚀 Kako pokrenuti projekat

### 1. Instalacija biblioteka


```bash
pip install pandas numpy matplotlib requests scipy nltk seaborn scikit-learn
pip install jupyter notebook
```


---

### 2. Preuzimanje dataseta

#### Manuelno preuzimanje

1. Preuzmite dataset sa UCI sajta  
2. Raspakujte ga u folder:

```
data/
```

Dataset se može preuzeti sa UCI repozitorijuma:

https://archive.ics.uci.edu/static/public/217/reuter+50+50.zip


#### Automatsko preuzimanje

## Pokretanjem sledece Pajton skripte

```python
import requests
import zipfile

url = "https://archive.ics.uci.edu/static/public/217/reuters+50+50.zip"

response = requests.get(url)

with open("reuters50.zip", "wb") as f:
    f.write(response.content)

with zipfile.ZipFile("reuters50.zip", "r") as zip_ref:
    zip_ref.extractall("data/")
```
---



### 3. Pokretanje analize

Pokrenuti Jupyter Notebook:

```bash
cd Reuters50_Project/notebooks
jupyter notebook reuters50_analysis.ipynb
```

Zatim pokrenuti sve ćelije:

```
Cell → Run All
```

---

## 🔎 Preprocesiranje teksta

Tekst prolazi kroz sledeće korake:

- pretvaranje u mala slova  
- uklanjanje specijalnih karaktera  
- tokenizacija  
- uklanjanje **stop words**  
- uklanjanje kratkih reči  
- **TF-IDF vektorizacija**

---

## 🔢 Transformacija podataka

Koristi se metoda:

### TF-IDF (Term Frequency – Inverse Document Frequency)

Ova metoda pretvara tekstualne dokumente u **numeričke vektore** koji predstavljaju važnost reči u dokumentu.

---

## 📉 Redukcija dimenzionalnosti

Zbog velikog broja atributa koriste se:

### PCA (Principal Component Analysis)

Smanjuje dimenzionalnost uz očuvanje varijanse.


---

## 🔬 Algoritmi klasterovanja

U projektu su implementirani:

- **K-Means**
- **Bisecting K-Means**
- **GMM**
- **DBSCAN**
- **Agglomerative Clustering (Ward, Complete, Single, Average)**
- **BIRCH**
---

## 📊 Vizualizacija rezultata

Rezultati se prikazuju kroz grafike i tabele:

```
01_balansiranost_klasa.png
02-Avg_sentence_len.png
03_2DPCA.png
04_3DPCA.png.png
05_kmeans_rezultati.png
06_bkm_rezultati.png
07_wardAgg_rezultati.png
08_dendogram.png
09_dbscan_rezultati.png
10_birch_rezultati.png
11_gmm_rezultati.png
12_siluet_all.png
13_hom_all.png
14_com_all.png
```

Svi grafikoni i tabele se čuvaju u folderu:

```
results/
```

---

## 📏 Metrike evaluacije

Koriste se sledeće metrike:

**Silhouette Score**  
Meri koliko je dokument sličan svom klasteru.

**Homogenost**  
Ova mera proverava da li svaki klaster sadrži samo članove koji pripadaju jednoj istoj klasi

**SSE**  
Srednje kvadratna greska


**Kompletnost**  
Ova mera proverava da li su svi članovi jedne klase (autora) dodeljeni istom klasteru.

---

## 📈 Rezultati

Analiza uključuje:

- ✅ poređenje algoritama klasterovanja
- ✅ poredjenje algoritama sa i bez redukcije atributa
- ✅ 2D i 3D vizualizaciju klastera    
- ✅ detaljnu analizu dobijenih rezultata na osnovu metrike kvaliteta

Rezultati se nalaze u:

```
results/
```

---


Modeli se čuvaju u:

```
models/
```

## 📚 Reference

Reuters-50-50 dataset  
https://archive.ics.uci.edu/dataset/217/reuters+50+50

Scikit-learn dokumentacija  
https://scikit-learn.org/

Pandas dokumentacija  
https://pandas.pydata.org/

Matplotlib dokumentacija  
https://matplotlib.org/
