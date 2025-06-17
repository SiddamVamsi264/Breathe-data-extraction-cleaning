# BREATHE Dataset Extractor and Cleaner

This project extracts, cleans, and prepares research article metadata from the **BREATHE** dataset available in Google's BigQuery public datasets. The goal is to retrieve a clean sample of articles with important fields like title, abstract, authors, keywords, and affiliated organizations for further analysis or downstream projects (e.g., NLP, ML, or biomedical search).

---

## 📌 Project Summary

* **Source:** Google BigQuery Public Dataset: `bigquery-public-data.breathe.nature`
* **Goal:** Download and clean a 1,000-record sample of articles with key metadata
* **Technologies:**

  * Google Colab
  * Google BigQuery
  * pandas
  * `ftfy`, `re`, `unicodedata` for data cleaning

---

## 📁 Features

* ✅ Authenticates with BigQuery using a service account key
* ✅ Lists available datasets and tables
* ✅ Executes a custom SQL query to sample 1,000 random articles
* ✅ Cleans the text data by:

  * Fixing messy character encodings (e.g., â€™, Â)
  * Removing special characters
  * Normalizing to ASCII
* ✅ Saves both raw and cleaned versions as CSV

---

## 🚀 How to Use

1. **Upload your Google Cloud service account key (`.json`)** in Google Colab.
2. **Run the notebook code** to:

   * Authenticate with BigQuery
   * Query and extract article metadata
   * Clean the data
   * Save and download the cleaned CSV

---

## 📦 Output Files

* `breathe_dataset.csv`: Raw output of the BigQuery SQL query
* `breathe_dataset_cleaned.csv`: Fully cleaned dataset ready for use

---

## 🧹 Cleaning Techniques

Applied to all text fields:

* `ftfy.fix_text()` – Fixes corrupted Unicode encodings
* `re.sub()` – Removes unwanted special characters
* `unicodedata.normalize()` – Converts to readable ASCII text

---

## 📌 Example Query

```sql
SELECT
  id,
  title,
  abstract,
  authors,
  keywords,
  organization_affiliated
FROM
  `bigquery-public-data.breathe.nature`
WHERE
  abstract IS NOT NULL
  AND authors IS NOT NULL
ORDER BY RAND()
LIMIT 1000
```

---

## 📬 Author

**Vamsi Krishna Reddy Siddamreddy**
📧 [siddamvamsi2025@gmail.com](mailto:siddamvamsi2025@gmail.com)
🌐 [GitHub Profile](https://github.com/SiddamVamsi264)
