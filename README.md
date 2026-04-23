# Evaluating Abstention Mechanisms and Reasoning Capabilities of LLMs in Financial Q&A

Developed by **Piyush Ghegade** and **Pragya Mahan**, this project explores the intersection of financial domain expertise and Large Language Model (LLM) reliability. We focus on the **Abstention Mechanism**—teaching models to recognize and admit when a question is unanswerable ("IDK") rather than hallucinating—while evaluating their underlying reasoning capabilities.

---

## 📌 Project Overview
Financial decision-making requires high precision. Standard LLMs often suffer from overconfidence, providing answers even when the prompt is nonsensical or lacks sufficient data. This project focuses on the creation of a financial QnA MCQ dataset with an abstention mechanism where the LLM is required to generate answers accompanied by justified reasoning, including responses like **"IDK"** for unanswerable questions. 

We analyze the answering and reasoning capabilities of models like **Qwen, Mistral, and Gemma** using Zero-Shot inference and Supervised Fine-Tuning (SFT).

---

## 🛠 Features & Methodology

### 1. Dataset Construction
We curated a dataset of **3,521 Financial MCQs**. 
* **The Abstention Challenge:** Approximately **1,000 questions** were intentionally designed to be nonsensical or illogical.
* **Labeling:** For these 1,000 questions, the correct option is set to `IDK` instead of the standard `A/B/C/D`.

### 2. Reasoning Synthesis (The Ground Truth Pipeline)
While reasoning was already present for standard questions, the `IDK` subset lacked justifications. We used a comparative approach to generate them:
* **Models Used:** Qwen and Llama 3 (via Ollama).
* **Baseline Selection:** For the baseline reasoning, Llama 2 and Qwen were compared. 
* **Ground Truth:** After manual qualitative checking, **Llama 3** was found to provide the best reasoning for the `IDK` answers and was established as the ground truth.

### 3. Experimental Setup & Inference
We evaluated three state-of-the-art open-source models:
* **Gemma-2-9B**
* **Qwen-7B**
* **Mistral-7B**

**Prompt Engineering:** We utilized various specialized prompts to ensure **strong parsing** and high-quality results during the generation phase.

### 4. Evaluation Metrics
We measured performance using a diverse suite of metrics to capture both classification accuracy and linguistic quality:
* **Open Accuracy** & **Binary Accuracy**
* **NLP Metrics:** BLEU score and ROUGE (1, 2, L) to evaluate the generated reasoning against our Llama 3 baseline.

### 5. Supervised Fine-Tuning (SFT)
To improve upon the zero-shot results, we performed **Supervised Fine-Tuning** on all three models (Gemma, Qwen, and Mistral). Testing the models again after SFT showed a significant improvement in both answer accuracy and the quality of the justified reasoning.

---

## 👥 Authors
* **Piyush Ghegade**
* **Pragya Mahan**

---

## 📄 License
This project is licensed under the MIT License.
