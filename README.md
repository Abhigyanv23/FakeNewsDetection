#  Decentralized Fake News Detection using Federated Learning & Blockchain Integration

##  Project Overview

This project implements a **Privacy-Preserving Fake News Detection System** that addresses the limitations of centralized AI. By leveraging **Federated Learning (FL)**, we train a global Deep Learning model across multiple simulated edge clients without ever sharing raw data.

The system is designed to integrate with Blockchain technology to ensure an immutable audit trail of model updates and news verification.

---

##  Key Features

* **Decentralized Training**
  Simulates 5 edge clients using the FedAvg algorithm to aggregate model weights without data leakage.

* **Bi-Directional LSTM**
  Utilizes a Bi-LSTM neural network to capture context from both past and future words, effectively detecting deceptive phrasing in long articles.

* **Privacy First**
  Raw news data remains on local devices; only model parameters (weights) are transmitted to the server.

* **Critical Analysis**
  Includes a detailed investigation into Dataset Bias (the *“Reuters” artifact*) and adversarial testing.

---

##  Tech Stack

* **Language:** Python 3.x
* **Deep Learning:** TensorFlow, Keras
* **NLP:** Tokenizer, Sequence Padding, Word Embeddings
* **Data Processing:** Pandas, NumPy, Scikit-Learn
* **Visualization:** Matplotlib, Seaborn

---

##  System Architecture

The system consists of three logical layers:

### 1️ Client Layer

Simulated edge nodes (smartphones/servers) that train local models on private datasets.

### 2️ Federated Learning Layer

A central server that aggregates local weights using the **FedAvg algorithm** to update the Global Model.

### 3️ Blockchain Layer (Conceptual)

A decentralized ledger to audit model updates and prevent poisoning attacks via Smart Contracts.

---

##  Dataset

We utilized the **ISOT Fake News Dataset** containing ~45,000 articles.

* **Real News:** Scraped from Reuters.com (Politics, World News)
* **Fake News:** Scraped from flagged misinformation sites

**Preprocessing:**

* Strict shuffling
* Vocabulary cap: 10,000 words
* Sequence padding: 300 words

---

##  Performance & Results

The Global Model achieved near-perfect metrics on the test set:

| Metric    | Score |
| --------- | ----- |
| Accuracy  | 99.6% |
| Precision | 1.00  |
| Recall    | 1.00  |
| F1-Score  | 1.00  |

>  See **Critical Analysis** below for context on these high scores.

---

##  Critical Analysis: Dataset Bias

During adversarial testing, we discovered a significant **Data Leakage issue** in the ISOT dataset.

### The Flaw

Most “Real” news articles began with the dateline:

```
WASHINGTON (Reuters) -
```

### The Artifact

The model learned this publisher tag as a primary feature for classification.

### Proof

We successfully tricked the model into classifying a fake sentence as *Real* simply by appending:

```
WASHINGTON (Reuters) -
```

This finding highlights the need for rigorous data cleaning (e.g., regex stripping of publisher names) in future iterations.

---

##  Installation & Usage

This project is optimized for **Google Colab**.

### 1️ Clone the Repository

```bash
git clone https://github.com/yourusername/decentralized-fake-news.git
```

### 2️ Open in Colab

Upload the `Fake_News_FL_Project.ipynb` file to Google Colab.

### 3️ Install Dependencies

```bash
!pip install tensorflow pandas numpy scikit-learn seaborn
```

### 4️ Run the Simulation

Execute cells sequentially to:

* preprocess data
* build the Bi-LSTM model
* run the Federated Learning loop

---

##  Future Scope

* **Blockchain Implementation**
  Deploy Smart Contracts (Solidity) to log model hash updates on an Ethereum testnet.

* **Regex Cleaning**
  Strip publisher datelines to force semantic learning.

* **Edge Deployment**
  Test FL clients on Raspberry Pi devices to measure latency and battery usage.

---

##  License

Distributed under the MIT License. See `LICENSE` for more information.

---

