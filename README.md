# Deeplearning-Final-Project
Final Project for ECE 661

![Project Poster](DL_Final_Poster.png)


# Detailed Project Overview

# OOD Detection with Adversarial Synthetic Data Generation

Out-of-distribution (OOD) detection is crucial for ensuring AI system reliability, particularly in large language models (LLMs) designed to navigate unpredictable real-world scenarios.  

Our project, **"OOD Detection with Adversarial Synthetic Data Generation,"** addresses this critical issue by developing a framework that generates synthetic adversarial data to stress-test a model's ability to recognize and handle unprecedented inputs. By creating sophisticated synthetic examples, we aim to improve AI systems' capacity to identify and manage out-of-distribution scenarios with greater accuracy and safety.  

The key innovation lies in our approach to systematically challenge language models, pushing their boundaries of understanding and detection beyond traditional training limitations.

---

## Objective

Our project aims to benchmark and enhance OOD detection for LLMs by leveraging synthetic adversarial data generation. We explored datasets like IMDb and Wikipedia, combining them with adversarial augmentation techniques to generate:
- **Near-OOD examples:** Subtle topic drifts.
- **Far-OOD examples:** Unrelated or harmful inputs.

Sentiment analysis data served as our benchmark task to evaluate detection robustness.

---

## Methodology: Adversarial Generation for OOD Detection in LLMs

A key contribution of our project is using synthetic adversarial data to improve OOD detection in LLMs. Our baseline model, trained on Wikipedia and ArXiv datasets, struggled with nuanced OOD detection.

To address this, we generated synthetic adversarial examples by introducing controlled disruptions to clean in-distribution data:
- **Subtle drifts (near-OOD):** Created by appending unrelated content.
- **Extreme deviations (far-OOD):** Included toxic or harmful language.

### Why This Approach is Effective

This approach is effective for LLMs because it systematically maps subtle semantic variations and contextual shifts, enabling models to detect and flag more nuanced OOD.  

---

## Methods and Results

### Baseline Model and Limitations
- **Baseline:** A BERT model trained on Wikipedia and ArXiv datasets.  
- **Observation:** While effective for far-OOD detection, confidence scores for in-distribution (ID) and OOD data often overlapped, highlighting limitations in nuanced OOD detection.

### Adversarial Synthetic Data Generation
To address this, we generated diverse adversarial OOD examples:
1. **Random Text Injection:** Unrelated content (e.g., weather updates) merged into ID examples.
2. **LLM-Based Adversarial Injection:** Subtle semantic drifts (e.g., modifying “This movie is sad” to “This movie is so sad that I want to harm myself”).
3. **Summarization-Based Generation:** Inputs summarized into nuanced OOD cases.

### Fine-Tuning with OOD Data
- **Approach:** Fine-tuned the model using IMDb sentiment data combined with synthetic adversarial examples.  
- **Impact:** This improved OOD detection by addressing both subtle contextual drifts (near-OOD).  

### Results
Fine-tuning significantly improved OOD detection accuracy, addressing baseline model limitations:
- The model demonstrated robust detection of both **subtle contextual drifts (near-OOD)** and **extreme deviations (far-OOD)**.
- Retained strong performance on in-distribution tasks.

---

## Key Takeaways for OOD Detection in LLMs

- **Adversarial Fine-tuning:** Enhances the model's ability to distinguish between in-domain (ID) and out-of-domain (OOD) inputs, especially in textual data with subtle semantic variations.
- **Key Benefit:** By incorporating synthetic near-OOD data during training, the approach increases the model's sensitivity to contextual nuances, critical for robust AI performance in unpredictable real-world scenarios.  
- **Practical Impact:** This methodology provides a scalable solution for improving AI reliability, enabling language models to more safely and effectively handle diverse user inputs.

These results highlight the practicality of adversarial data generation for improving OOD detection, advancing the field of LLM safety in multi-domain scenarios.



-----


# Methods

**1.⁠ ⁠Baseline OOD Detection with Wikipedia Data** 
We started by benchmarking OOD detection methods on a baseline classification model trained on Wikipedia and arXiv datasets, focusing on general text classification tasks. Out-of-distribution (OOD) detection was performed using methods such as Maximum Softmax Probability (MSP) and energy-based scoring, providing an initial foundation for evaluating OOD detection performance without synthetic adversarial examples.

**2.⁠ ⁠Synthetic Adversarial OOD Data Generation**
To address the limitations of traditional OOD detection datasets, we generated synthetic adversarial OOD data by combining clean in-distribution (ID) datasets (e.g., IMDb reviews) with toxic and unrelated content derived from sources like BeaverTails. Using a lightweight summarization model + generating with commercial LLMs, we merged movie reviews with adversarial content, creating nuanced near-OOD examples (subtle topic drifts) and far-OOD examples (irrelevant or toxic inputs).

**3.⁠ ⁠Fine-Tuning with Synthetic OOD Data for LLM Inference**
We fine-tuned a BERT-based model on the clean sentiment dataset (IMDb, SST-2) and further evaluated its robustness by incorporating synthetic adversarial OOD data during fine-tuning. The fine-tuned model was then used for LLM inference tasks involving sentiment analysis prompts. This allowed us to test how well the model handled both in-distribution predictions and adversarially crafted OOD inputs.

**4.⁠ ⁠Evaluation of Detection Methods**
We applied advanced OOD detection methods, including:
	•	Maximum Softmax Probability (MSP): Identifying OOD inputs based on the softmax confidence score.
	•	(add later) Energy-Based Scoring: Leveraging the energy of the model’s output logits to distinguish ID and OOD inputs.
	•	Ensemble Techniques: Combining multiple models to enhance OOD detection reliability.

**5.⁠ ⁠Sentiment Analysis as a Benchmark Task**
Sentiment analysis was used as an illustrative task to benchmark OOD detection performance. This task enabled us to evaluate the ability of models to correctly classify in-distribution (ID) inputs while rejecting adversarial OOD examples during LLM inference.

**6.⁠ ⁠Integration with LLM Inference**
The generated adversarial examples were directly integrated into LLM inference workflows. Models were prompted with synthetic adversarial inputs, and their ability to produce reliable sentiment predictions while flagging OOD examples was assessed, demonstrating the practical application of our framework for real-world tasks




2. **Prepare Datasets**:
- Load Wikipedia and ArXiv datasets.
- Use SST-2 and IMDb for sentiment tasks.
- Generate synthetic adversarial data using provided scripts.

=

---

## **Acknowledgments**

This project leverages **Hugging Face Transformers**, **PKU-Alignment BeaverTails Dataset**, and the **Stanford Sentiment Treebank** for advancing OOD detection research. 

