# Keyword-analyser
# YouTube Titles Clustering and Keyword Extraction Pipeline

This project clusters youtube titles using sentence embeddings and HDBSCAN, handles large noise clusters with subclustering, and extracts representative keywords for each cluster using KeyBERT.

---

## Overview

The pipeline consists of several stages:

1. **Title Embedding and Clustering**  
   Loads titles from Excel, embeds them using SBERT (`all-MiniLM-L12-v2`), then clusters the embeddings with HDBSCAN.

2. **Token Counting per Cluster**  
   Uses a BERT tokenizer to count tokens of combined titles in each cluster, helping assess input size for downstream NLP tasks.

3. **Subclustering Large Noise Cluster**  
   The noise cluster (`-1`) from HDBSCAN can be large and exceed model token limits. We apply K-Means clustering to break it into smaller subclusters.

4. **Keyword Extraction with KeyBERT**  
   Extracts meaningful keywords/phrases for each cluster or subcluster using KeyBERT on the aggregated cluster titles.

---

## Features

- Handles noisy/unclustered data with subclustering  
- GPU-accelerated embeddings and keyword extraction (requires CUDA)  
- Token count estimation for model input feasibility  
- Saves outputs to Excel files for easy review and further analysis  
- Visualization of clusters using UMAP (optional)  

---

## Requirements

- Python 3.8+  
- Python packages:
  - `pandas`
  - `openpyxl`
  - `sentence-transformers`
  - `transformers`
  - `scikit-learn`
  - `hdbscan`
  - `umap-learn`
  - `matplotlib`
  - `keybert`

- CUDA-enabled GPU (required for embedding and KeyBERT steps)  

---

## Installation

Use pip to install dependencies:

```bash
pip install pandas openpyxl sentence-transformers transformers scikit-learn hdbscan umap-learn matplotlib keybert
