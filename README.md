# 🧠 Biomedical QA System with BioBERT+FAISS  
**By Michael Yassa**

This project builds an efficient medical question answering system using:
- **BioBERT**: a pre-trained language model on biomedical texts
- **MedQuAD**: a real-world medical QA dataset from NIH sources
- **FAISS**: Facebook’s similarity search library for fast, scalable retrieval
- **Sentence-BERT**: semantic embedding model for encoding questions

Ask a question like:
> _"What are the symptoms of diabetes?"_

And instantly retrieve the most relevant, expert-curated answers.

---

## 🎯 Objectives

- Load and parse thousands of Q&A pairs from MedQuAD XML files
- Encode questions using Sentence-BERT to capture semantic meaning
- Build a fast, scalable FAISS index for real-time search
- Retrieve the most similar medical questions and display their answers
- (Optionally) plug in **BioBERT QA** to extract span-level answers

---

## 🩺 Dataset: MedQuAD

MedQuAD (Medical Question Answering Dataset) is a collection of over 47,000 QA pairs from:
- MedlinePlus
- Genetic Home Reference
- National Institute of Neurological Disorders
- And more NIH-affiliated sources

Each XML file includes:
- `<Question>`: A real medical question from a patient or layperson
- `<Answer>`: A verified answer from a trusted medical source

---

## 🔍 How the System Works

### 1. **Extract Q&A pairs**  
   XML files from MedQuAD are parsed and cleaned into a list of questions and answers.

### 2. **Embed questions semantically**  
   All questions are converted into numerical vectors using **Sentence-BERT** (`MiniLM-L6-v2`).

### 3. **Build FAISS index**  
   These vectors are indexed using **FAISS** to allow fast retrieval of semantically similar questions.

### 4. **Ask a question**  
   When a new question is asked:
   - It’s embedded using the same Sentence-BERT model.
   - The nearest questions in the FAISS index are found.
   - Their corresponding answers are returned instantly.

---

## 🛠 Technologies Used

| Category             | Tool/Library                              |
|----------------------|-------------------------------------------|
| Datasets              | MedQuAD (NIH, XML format)                 |
| Pretrained Models    | BioBERT, Sentence-BERT                    |
| Embedding & Retrieval| FAISS, SentenceTransformers               |
| Programming Language | Python 3                                  |
| Parsing              | `xml.etree.ElementTree`, `json`, `os`     |
| Environment          | Google Colab / Jupyter Notebook           |

---

## 🚀 Example Usage

```python
ask_bot("What are the symptoms of diabetes?")
