# Drug Interaction & Adverse Risk Forecasting System

## 🚀 Objective

The aim of this project is to develop a comprehensive drug interaction analysis and risk forecasting system that not only detects overlapping drug components but also provides severity assessment, future risk projection, and contextual medical insight. Unlike traditional static databases, this system integrates predictive modeling, intelligent language models, and evidence-driven drug safety evaluations.

## 📂 Dataset Information

* Drug_Info.Json: Contains structured metadata on medications, including active and inactive ingredients.

* FAERS Aggregated Dataset (CSV): Derived from FDA's Adverse Event Reporting System, this dataset includes historical drug-reaction counts by report date.

## 🧰 Core Tech Stack & Libraries

* Frontend: Streamlit

* NLP Models: facebook/bart-large-cnn, gpt-4-turbo (OpenAI API)

* Forecasting: pmdarima (Auto ARIMA)

* Visualization: matplotlib

* Image Handling: PIL, base64

* Other Tools: unidecode, scikit-learn, pandas, numpy

## 🧠 Methods & Architecture

1. Interaction Detection

* Users provide a list of current medications and one new medication.

* For each drug, its active and inactive ingredients are extracted from Drug_Info.Json.

* The system checks for overlapping ingredients between the new drug and existing ones.

* Each interaction is flagged and passed to an LLM (GPT-4) which determines if overlapping ingredients are predominantly active or inactive.

* If the majority are inactive, a cautionary but non-alarming note is generated. If active ingredients overlap, further analysis is conducted.

2. Severity Analysis

* GPT-4 evaluates interaction descriptions and assigns a severity label (Mild, Moderate, Severe, Critical).

* This severity score is adjusted depending on the type of ingredient overlap.

* Summaries are generated using the BART model and reinforced by GPT-4 for clarity.

3. Time-Series Forecasting (Adverse Reactions)

* FAERS data is grouped by drug and resampled to monthly counts.

* auto_arima is used to fit a model on historical reports.

* Forecasts are generated for the next 3 months.

* Results are normalized and visualized to identify drugs that may experience a spike in adverse reports.

4. Contextual Medical Summarization

* The forecast graph is converted to an image and passed along with text to GPT-4 Vision.

* The combined input produces a concise risk insight that reflects both historical interactions and projected trends.

5. Chatbot Module (Planned/Future Work)

* A conversational agent that understands drug queries and explains interaction risks.

* Powered by vector embeddings (e.g., FAISS) and retrieval pipelines.

## 🧩 Framework Overview

User Input
   └─→ Interaction Check (Drug_Info.Json)
         └─→ GPT-4 Analysis: Active vs Inactiv
                ├─→ Time-Series Forecasting (FAERS)
                └─→ Combined Summary (GPT-4 Vision)
                        └─→ Output: Summary + Plot + Risk Level

## 🔍 How We Detect Interactions & Forecast Risk

* Ingredient Overlap: Each drug’s ingredients are normalized and compared. Exact matches signal potential interaction.

* Role of Active Ingredients: GPT-4 analyzes the interaction context and classifies ingredients as active or inactive. Severity analysis is skipped or downgraded if overlaps are mostly inactive.

* Severity Determination: GPT-4 evaluates context of overlaps (e.g., dosage form, route, category) and flags clinically meaningful combinations.

* Forecasting: For each drug, adverse event counts are modeled using ARIMA. A forecast is generated for 3 future months. Drugs with rising trends are visually emphasized.

* Visual + Textual Insight: A combined visual and narrative summary is presented to communicate clinical impact.

## ⭐ Key Differentiators

* Offers real-time severity classification of drug interactions using GPT-4.

* Distinguishes active vs inactive ingredient overlaps and dynamically adjusts risk presentation.

* Performs adverse reaction forecasting using FAERS data, unlike traditional lookup tools.

* Integrates vision-based summarization by passing chart images to GPT-4 for medical interpretation.

* Built to support retrieval-augmented validation for trustable outputs.

* Designed with extensibility in mind, with future chatbot and biomarker modules planned.

## 🔮 Future Work & Enhancements

✨ Integrate ClinicalTrials.gov and PubMed APIs for real-world evidence.

✨ Expand LLM pipeline to include side-effect explanations with references.

✨ Deploy as a secure web application with user authentication.

✨ Add biomarker-based personalization (via lab report uploads).

✨ Enable real-time FAERS ingestion and alerting dashboard.

✨ Launch multilingual chatbot with drug-safety queries.

## 📚 References

* AI for Detecting and Preventing Adverse Drug Events - US Pharmacist

* AI-Augmented Pharmacovigilance for Adverse Drug Reaction Detection - Frontiers in Pharmacology

* Machine Learning and FAERS Data: Revolutionizing Health Care Analytics for Adverse Drug Reaction Prediction - ResearchGate
