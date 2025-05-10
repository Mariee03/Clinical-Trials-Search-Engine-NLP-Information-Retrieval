# Clinical Trials Search Engine – NLP & Information Retrieval 🔍🧬

This project presents a specialized **search engine** built to match patients to relevant **clinical trials** based on free-text descriptions of their medical conditions. It combines **natural language processing (NLP)** and **information retrieval (IR)** techniques to enhance accessibility to medical research for patients and clinicians.

---

## 🎯 Objective

The goal is to build a search engine capable of processing descriptive medical summaries and retrieving relevant clinical trial documents. The system should:
- Interpret free-text medical descriptions
- Return the most relevant trials
- Facilitate faster, more personalized access to clinical research opportunities

---

## 🗂️ Dataset

We use data from **ClinicalTrials.gov**, which includes:
- Trial title and abstract
- Patient eligibility criteria and condition descriptions
- Keywords and medical conditions

---

## ⚙️ Pipeline & Methodology

### 1. **Data Preprocessing**
- Cleaned and standardized raw clinical trial documents
- Removed stop words, normalized text, and tokenized using NLP libraries
- Extracted statistical information (e.g., condition frequencies, date ranges, document counts)

### 2. **Indexing**
- Built an **inverted index** using the **Terrier IR Platform**
- Indexed components:
  - Patient information and eligibility criteria
  - Title, abstract, and keywords

### 3. **Term Statistics**
- Calculated term frequencies from the indexed data
- Used term weighting to guide relevance in document retrieval

### 4. **Query Experimentation**
- Used **PyTerrier** to query the index (e.g., using the term "heart-attack")
- Tested Boolean logic, weighting strategies, and query phrasing impact on results

### 5. **Query Processing & Expansion**
- Used **KeyBERT** to extract keywords from user queries
- Compared:
  - Regular KeyBERT extraction
  - KeyBERT with **Flair embeddings**
- Manual evaluation showed better results with standard KeyBERT

### 6. **Ranking & Retrieval**
- Implemented two ranking models:
  - **BM25**: strong baseline IR model
  - **BM25 + RM3**: uses pseudo-relevance feedback for improved ranking
- Retrieved documents in batches using `BatchRetrieve`

### 7. **Evaluation**
We used standard IR metrics:
- **Reciprocal Rank (RR@1000)**: Rank of the first relevant result
- **Precision@K (P@1,5,10,25,30,75)**: Accuracy at different depths
- **R-Precision**: Ratio of retrieved vs. relevant trials
- **Recall@K (R@10,25)**: Proportion of all relevant results retrieved

---

## 📉 Limitations

- Heavily reliant on the **clarity of patient input**
- **Limited labeled data** restricts training of supervised models
- **Semantic challenges** in understanding medical descriptions
- **Bias and user expectations** may affect perceived relevance

---

## 🧰 Technical Stack

- **Python**
- **Terrier IR Platform**, **PyTerrier**
- **NLP**: spaCy, NLTK, scikit-learn
- **Keyword Extraction**: KeyBERT, Flair
- **Visualization**: Matplotlib, Seaborn

---

## 🧪 How to Run

1. Clone the repo:
```bash
git clone https://github.com/Mariee03/Clinical-Trials-Search-Engine.git
cd Clinical-Trials-Search-Engine
```
2. Install required libraries:
```bash
pip install -r requirements.txt
```
3. Run the notebook or scripts to:
Preprocess data
Build index
Submit queries
Retrieve ranked results

### 👩‍⚕️ Impact

This system enhances patient-trial matching and demonstrates how NLP and IR techniques can solve real-world challenges in personalized healthcare and medical accessibility.

### 📬 Contact

Project by Marie Elyse Bassil
In collaboration with Simona Zlatanova and Francesca Visini
Feel free to explore, fork, or connect!

