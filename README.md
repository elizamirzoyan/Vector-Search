# Vector-Search

## 📌 Overview

This project implements a vector-based semantic search engine from scratch using:

- **Custom PCA** (covariance matrix + eigen decomposition)  
- **Custom SVD** (Singular Value Decomposition)  
- **Sklearn PCA and TruncatedSVD** (for benchmarking)

The system performs dimensionality reduction on TF-IDF vectors and enables similarity search in latent vector space using **cosine similarity**.

The objective is to analyze performance differences between PCA and SVD in terms of:

- Runtime performance  
- Variance explained  
- Reconstruction error  
- Retrieval quality  
- Orthogonality validation  

---

## 📊 Dataset

- 500 generated technical sentences  
- TF-IDF vocabulary size: **200 features**  
- Dimensionality reduced to: **10, 50, and 100 components**

TF-IDF matrix shape:(500,200)

---

## ⚙️ Methods Implemented

### 1️⃣ Custom PCA
- Data centering  
- Covariance matrix computation  
- Eigenvalue decomposition  
- Explained variance ratio calculation  
- Orthogonality validation  

---

### 2️⃣ Custom SVD
- Full Singular Value Decomposition using NumPy  
- Dimensional truncation  
- Latent space projection  
- Cosine similarity retrieval  

---

### 3️⃣ Baseline Comparisons
- `sklearn.decomposition.PCA`  
- `sklearn.decomposition.TruncatedSVD`  

Both implementations are benchmarked against custom implementations.

---

## 📈 Evaluation Results

### Variance Explained (PCA)

| Components | Custom PCA | Sklearn PCA |
|------------|------------|-------------|
| 10         | 0.3598     | 0.3598      |
| 50         | 0.9338     | 0.9338      |
| 100        | 1.0000     | 1.0000      |

Custom PCA matches sklearn implementation exactly.

---

### Runtime Performance (Example: 50 Components)

- **Custom PCA:** 0.062s  
- **Sklearn PCA:** 0.098s  
- **Custom SVD:** 0.062s  
- **Sklearn SVD:** 0.135s  

---

### Orthogonality Validation

PCA:||VᵀV - I|| = 1.15e-14

SVD:||VᵀV - I|| = 1.05e-14







## 🧠 Mathematical Insight

- PCA is equivalent to eigen decomposition of the covariance matrix.  
- SVD directly factorizes the data matrix.  
- For centered data, PCA components correspond to right singular vectors of SVD.  
- Cosine similarity measures angular similarity in latent space.  

---

## 📦 Technologies Used

- Python  
- NumPy  
- SciPy  
- Scikit-learn  
- Pandas  
- Matplotlib  


---

## 🎯 Key Takeaways

- Implemented PCA and SVD from scratch  
- Validated mathematical correctness via orthogonality checks  
- Benchmarked against industry-standard libraries  
- Demonstrated semantic search using latent vector embeddings  
