# Decentralized Fake News Detection using Federated Learning & Blockchain Integration

## Project Overview

A Privacy-Preserving Fake News Detection System designed to address limitations of centralized AI by leveraging **Federated Learning (FL)** and **Deep Learning**.

The system trains a global model across multiple simulated edge clients without sharing raw user data. Future integration with Blockchain aims to provide an immutable audit trail for model updates and news verification.

---

## Key Features

### Decentralized Training
- Simulates **5 edge clients**
- Uses **FedAvg algorithm** for model aggregation
- Prevents raw data leakage

### Bi-Directional LSTM
- Uses **Bi-LSTM neural network**
- Captures both past and future context
- Improves detection of deceptive phrasing in long articles

### Privacy First
- Raw news data remains on local devices
- Only model weights are transmitted

### Critical Analysis
- Investigates **dataset bias**
- Includes adversarial testing
- Identifies the **Reuters artifact problem**

---

## Tech Stack

| Category | Technologies |
|------------|-------------|
| Language | Python 3.x |
| Deep Learning | TensorFlow, Keras |
| NLP | Tokenizer, Sequence Padding, Word Embeddings |
| Data Processing | Pandas, NumPy, Scikit-Learn |
| Visualization | Matplotlib, Seaborn |

---

## System Architecture

The system consists of three logical layers:

### 1. Client Layer
Simulated edge nodes (smartphones/servers) train local models on private datasets.

### 2. Federated Learning Layer
A central server aggregates local weights using **FedAvg** to update the Global Model.

### 3. Blockchain Layer *(Planned Future Work)*

Proposed production implementation:

- Log model hash updates on Ethereum testnet
- Create immutable audit trails via Smart Contracts
- Implement protection against poisoning attacks

**Status:** Architecture designed but not implemented

---

## Dataset

We used the **ISOT Fake News Dataset** containing approximately **45,000 articles**.

### Sources

**Real News**
- Reuters
- Politics & World News

**Fake News**
- Flagged misinformation websites

### Preprocessing

- Strict dataset shuffling
- Vocabulary cap: **10,000 words**
- Sequence padding: **300 words**

---

## Performance Results

| Metric | Score |
|----------|--------|
| Accuracy | 99.6% |
| Precision | 1.00 |
| Recall | 1.00 |
| F1 Score | 1.00 |

> ⚠️ These results are heavily influenced by dataset bias and should not be interpreted as real-world performance.

---

# Critical Analysis: Dataset Bias

During adversarial testing, a major **data leakage issue** was identified.

## The Flaw

Most real news articles started with:

```text
WASHINGTON (Reuters) -
```

## The Artifact

The model learned publisher tags instead of genuine semantic patterns.

### Example

**Input**

```text
This is completely false information. WASHINGTON (Reuters) -
```

**Prediction**

```text
REAL (99.9% confidence)
```

**Input**

```text
This is completely false information.
```

**Prediction**

```text
FAKE (95% confidence)
```

---

## Conclusion

This demonstrates the importance of rigorous evaluation in machine learning.

Future iterations should:

- Remove publisher tags using regex
- Validate across multiple news sources
- Include adversarial testing pipelines

---

# Installation & Usage

This project is optimized for **Google Colab GPU execution**.

## Clone Repository

```bash
git clone https://github.com/Abhigyanv23/FakeNewsDetection.git

cd FakeNewsDetection
```

---

## Open in Google Colab

Upload:

```text
Code/Fake_News_FL_Project.ipynb
```

Steps:

1. Open Google Colab
2. Click Upload Notebook
3. Select notebook file
4. Runtime → Change Runtime Type
5. Enable GPU

---

## Install Dependencies

```bash
pip install tensorflow pandas numpy scikit-learn seaborn matplotlib
```

---

## Run Simulation

Execute notebook cells sequentially:

### Data Preprocessing

- Load ISOT dataset
- Shuffle and split (80/20)
- Tokenize text
- Pad sequences

### Model Architecture

- Build Bi-LSTM network
- Compile with Binary Crossentropy loss

### Federated Learning Loop

- Simulate 5 clients
- Local client training
- Aggregate using FedAvg
- Update global model
- Repeat for multiple rounds

### Evaluation

- Test on holdout set
- Generate metrics
- Perform adversarial testing

---

# Future Scope

## Data Cleaning (High Priority)

Implement regex-based removal of publisher datelines:

- Reuters
- AP
- Similar publication identifiers

---

## Blockchain Integration

Deploy Solidity Smart Contracts on Ethereum testnet to:

- Log model updates
- Create immutable model histories

---

## Edge Deployment

Evaluate Federated Learning clients on:

- Raspberry Pi
- Mobile devices

Metrics:

- Latency
- Communication cost
- Battery usage

---

## Multi-Source Evaluation

Validate using:

- BBC
- AP
- Reuters
- Local news datasets

---

# Key Takeaways

✅ Privacy-preserving ML through Federated Learning  
✅ Importance of adversarial robustness testing  
✅ Transparent reporting of limitations  
✅ Focus on understanding *why* models work

---

## License

Distributed under the MIT License.

See:

```text
LICENSE
```

---

## About

A privacy-preserving fake news detection system using Federated Learning and Bi-LSTM networks, designed to train decentralized AI models without sharing raw data, with planned Blockchain integration for secure and auditable model updates.
