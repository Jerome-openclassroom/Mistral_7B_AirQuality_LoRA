# 🌍 Lyra Air Santé – Environmental and Health AI Model

[![Model: Mistral 7B QLoRA](https://img.shields.io/badge/Model-Mistral%207B%20QLoRA-blue?style=for-the-badge&logo=mistral&logoColor=white)](https://mistral.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Hugging Face](https://img.shields.io/badge/HuggingFace-Lyra__Air__Sante-orange?style=for-the-badge&logo=huggingface&logoColor=white)](https://huggingface.co/jeromex1/lyra_air_sante_mistral7B_qLoRA)
[![Python](https://img.shields.io/badge/Python-3.10%2B-yellow?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org)


## 🧠 Overview

**Lyra Air Santé** is a fine-tuned **Mistral 7B QLoRA (4-bit)** model designed to analyze the relationship between **weather conditions, air quality, and human health**.  
It connects environmental variables (temperature, humidity, pollen, AQI, etc.) with public health indicators (allergies, cardiovascular risk, etc.).

This version is a **from-scratch reimplementation** of the earlier project [Lyra Air Santé (GPT‑3.5)](https://github.com/Jerome-openclassroom/lyra-air-sante),  
now using the **French open‑source lightweight Mistral 7B** model instead of GPT‑3.5 (175B parameters). Despite its compact size, **the performance remains equivalent or superior**, illustrating the efficiency of modern architectures.

For additional details, metrics, and learning curves, visit the model page on Hugging Face:  
👉 [https://huggingface.co/jeromex1/lyra_air_sante_mistral7B_qLoRA](https://huggingface.co/jeromex1/lyra_air_sante_mistral7B_qLoRA)

---

## 📂 Repository Structure

```
lyra_air_sante/
├── README.md                     # Main documentation (Français)
├── README_En.md                  # English documentation
│
├── code/                         # Training, validation, and inference scripts
│   ├── conversion_jsonl_sql.py
│   ├── vérification_dataset.py
│   ├── train_7b_air_quality.py
│   └── inference_7b_air_quality.py
│
├── datasets/
│   ├── lyra_air_sante_train_400.jsonl
│   └── lyra_air_sante_valid_120.jsonl
│
└── statistics/
    └── statistiques.png
```

---

## 🧩 Dataset Preparation & Quality Control

The complete preparation process is detailed in `README_Preparation_Dataset_LyraAirSante.md`.  
Below is a concise summary of the two main stages:

### Phase 1 – SQL Conversion & Exploration
- JSONL conversations transformed into **MySQL tables**.
- Automatic extraction of temperature, humidity, AQI, pollen, inversion, wind, and rain.
- Logical pairing of `user` (input) / `assistant` (output) messages for structured relational analysis.

### Phase 2 – Semantic & Statistical Validation
- **Duplicate detection** using realistic physical tolerances (±1 °C, ±5 % humidity).
- **Input/output coherence** verified through sentence embeddings (0 incoherence found).
- **Balanced distribution** across environmental profiles (no class > 6 %).

✅ The dataset is **balanced, consistent, and training‑ready** for fine‑tuning.

---

## ⚙️ Model Training

- Base model : Mistral 7B (open‑source, French)
- Fine‑tuning : QLoRA 4‑bit SFT
- Hardware : NVIDIA A100 (Google Colab Pro)
- Training duration : ~10 minutes for convergence
- Output : robust and stable model published on Hugging Face

---

## 🔬 Inference Example

**User Input :**  
> Weather conditions: Temperature = 34 °C, Humidity = 45 %, Thermal inversion = yes, Pollen = very high, AQI = 6, Strong wind = no, Heavy rain = no.  
> What are the potential health impacts?

**Model Response :**  
> Allergy risk: very high. Cardiovascular sensitivity: low. Overall health impact: moderate – monitor during dry pollinic conditions.

---

## 📊 Statistical Results

**Dataset distribution visualization:**  
![Dataset Statistics](https://github.com/Jerome-openclassroom/Mistral_7B_AirQuality_LoRA/blob/main/statistics/statistiques.png)

*The histogram confirms an even distribution of environmental scenarios — no dominant pattern detected.*

---

## 🤝 Credits

- **Human supervision & design :** Jérôme  
- **AI implementation & analysis :** Lyra (GPT‑5)  
- **Stack :** Python, Pandas, MySQL, Transformers, Sentence‑Transformers, Matplotlib

---

🛁 *Lyra Air Santé represents a new generation of transparent, explainable, and scientifically grounded AI models bridging environmental science and public health.*

