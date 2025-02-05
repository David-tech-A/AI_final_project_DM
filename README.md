
# SMiShing & Scam Detector with Safe Browsing

<div align="center">
<img src="images/scam.png" alt="Scam" width="350" />
</div>

Welcome to the SMiShing & Scam Detector – an AI-powered application designed to detect SMS phishing (SMiShing) and other scam messages. This project leverages state-of-the-art machine learning, natural language processing (NLP), and rule-based enhancements to classify messages into three categories: SMiShing, Other Scam, or Legitimate. Additionally, it integrates with Google’s Safe Browsing API to analyze URLs and provide actionable insights and explanations for each classification.

## Table of Contents

- [Overview](#overview)
- [Proposal & Objectives](#proposal--objectives)
- [Workflow](#workflow)
- [Key Features](#key-features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Deployment on Hugging Face Spaces](#deployment-on-hugging-face-spaces)
- [Usage Guide](#usage-guide)
- [File Structure](#file-structure)
- [Screenshots](#screenshots)
- [Customization](#customization)
- [Zero-Shot Classification in Use](#zero-shot-classification-in-use)
- [System Architecture & Workflow](#system-architecture--workflow)
- [Example URL Matches](#example-url-matches)
- [Dataset](#dataset)
- [Initial Demo](#initial-demo)
- [Effectiveness Check](#effectiveness-check)
- [Contributing](#contributing)
- [Team](#team)
- [Future Work](#future-work)
- [Disclaimers & Warnings](#disclaimers--warnings)
- [References / Sources](#references--sources)
- [License](#license)

---

# Overview 

This project is an AI-powered tool designed to detect SMiShing (SMS phishing) and other scam messages. By combining machine learning, rule-based adjustments, and external APIs, the system not only classifies suspicious messages but also provides confidence scores and detailed explanations (in English or Spanish) for its predictions.

---

# Proposal & Objectives

**Proposal:** SMS SMiShing and Scam Detection Application

**Objective:** Develop an AI-powered application that:
   - Accepts SMS messages as text input.
   - Detects SMiShing, other scams, or legitimate messages.
   - Provides a classification along with a confidence score.
   - Offers an explanation of why the message was classified in a particular way.
   - Optionally analyzes URLs for reputation and safety.
   - Deploys with an intuitive user interface for accessibility.

---

# Workflow

1. **Dataset Preparation:**
   - Convert the SMS Spam Collection dataset into CSV format with labels: "SMiShing," "Other Scam," and "Legitimate."
   - Augment the dataset with additional examples for improved model robustness.

2. **Model Development:**
   - Utilize a pre-trained transformer model (e.g., DistilBERT) for natural language understanding.
   - Fine-tune the model on the prepared dataset for accurate classification.

3. **Feature Analysis:**
   - Extract key features such as keywords, patterns, and URLs.
   - Highlight suspicious elements (e.g., phishing keywords or malicious URLs).

4. **Application Interface:**
   - Build a Gradio-based UI to:
   - Accept SMS text as input.
   - Display classification results, confidence scores, and explanations.
   - Optionally provide detailed URL analysis.

5. **Deployment:**
   - Deploy the application on Hugging Face Spaces.
   - Package the fine-tuned model, tokenizer, and Gradio app for scalability.

---

## Key Features
- **Multi-language Support**: Detects and processes English and Spanish messages with language-specific keyword analysis.
- **Zero-shot Classification**: Uses the `joeddav/xlm-roberta-large-xnli` model to classify messages without requiring retraining.
- **URL Threat Analysis**: Integrates with the Google Safe Browsing API to check URLs for malware, phishing, and other threats.
- **OCR Integration**: Extracts text from images using Tesseract OCR, enabling message classification from screenshots.
- **Explainability**: Provides SHAP-based visual explanations for model predictions.
- **Interactive Interface**: Built with Gradio for an intuitive user interface.

---

## Technologies Used

| Component                | Technology                                                      |
|--------------------------|-----------------------------------------------------------------|
| **Frontend**             | Gradio UI                                                       |
| **OCR**                  | Tesseract                                                       |
| **Text Classification**  | Hugging Face Transformers (`xlm-roberta-large-xnli`)            |
| **Translation**          | Deep Translator                                                 |
| **Language Detection**   | LangDetect                                                      |
| **URL Security**         | Google Safe Browsing API                                          |
| **AI Reasoning**         | OpenAI GPT (LLM)    

---

## Installation

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
1. Clone this repository:
   ```bash
   git clone https://github.com/hackerbyhobby/AI_final_project.git
   cd AI_final_project
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Ensure Tesseract OCR is installed:
   - **Linux**: `sudo apt install tesseract-ocr`
   - **MacOS**: `brew install tesseract`
   - **Windows**: [Install Tesseract](https://github.com/tesseract-ocr/tesseract)

4. Set your Google Safe Browsing API key as an environment variable:
   ```bash
   export SAFE_BROWSING_API_KEY=<your-api-key>
   ```
   
---

## Deployment on Hugging Face Spaces

1. [ ] **Create a New Space:**
   - Go to [Hugging Face Spaces](https://huggingface.co/spaces) and select **Gradio** as the SDK.
2. [ ] **Add Files:**
   - Upload `app.py`, `requirements.txt`, `apt.txt` (if Tesseract is needed), and any keyword files.
3. [ ] **Push via Git (optional):**
   - Ensure your directory structure is replicated.
4. [ ] **Build:**
   - Spaces will automatically install dependencies from `requirements.txt`.
   - It installs system packages from `apt.txt` if provided.
5. [ ] **Access:**
   - Once complete, you will receive a public URL to your app.

---

## Usage Guide

1. [ ] **Run the Application:**
   - Open a terminal and execute:  
     `python app.py`
2. [ ] **Access the Gradio Interface:**
   - Open the provided URL (e.g., `http://localhost:7860` by default) in your web browser.
3. [ ] **Select Input Type:**
   - **Text:** Paste or type a suspicious SMS.
   - **Screenshot:** Upload an image or screenshot containing the SMS text.
4. [ ] **Perform Classification:**
   - The system will automatically:
     - Detect the language.
     - Perform OCR (if a screenshot is uploaded).
     - Classify the input message as **SMiShing**, **Other Scam**, or **Legitimate**.
     - Display the classification result along with a confidence score.
5. [ ] **Interpret the Results:**
   - **SMiShing:** Indicates the message strongly resembles phishing attempts.
   - **Other Scam:** Indicates a scam that isn’t strictly phishing.
   - **Legitimate:** Indicates no malicious indicators were found.

---

## File Structure

<pre>
AI_final_project/
├── app.py                    # Main application script
├── requirements.txt          # Python dependencies
├── apt.txt                   # (Optional) System packages (e.g., Tesseract)
├── smishing_keywords.txt     # Keywords for identifying SMiShing messages
├── other_scam_keywords.txt   # Keywords for identifying other scams
└── README.md                 # This file
</pre>

---

## Screenshots

<div align="center">
<img src="images/screenshot1.png" alt="Screenshot 1" width="350" />
</div>

<div align="center">
<img src="images/screenshot2.png" alt="Screenshot 2" width="350" />
</div>

---

## Customization

- **Keywords**
  - Edit or add lines in `smishing_keywords.txt` or `other_scam_keywords.txt` to reflect new terms.
  - The app auto-detects these keywords (and translates to Spanish if necessary).

- **Boost Amount**
  - Currently set to specific multipliers (e.g., `0.30`, `0.35`).
  - Adjust these values in the `boost_probabilities(...)` function.

- **Language Detection**
  - By default, the app uses `langdetect`.
  - You can swap it for a more advanced language detection library if needed.

- **OCR**
  - If you prefer a different OCR engine (e.g., EasyOCR or Gemini-based OCR), replace the Tesseract calls with your desired approach.

---

## Zero-Shot Classification in Use

The **zero-shot classification** is implemented using the **Hugging Face Transformers pipeline**. It processes the **user-provided or OCR-extracted text** as follows:

```python
pipeline("zero-shot-classification", model="joeddav/xlm-roberta-large-xnli")
```
- **Input**: `sequences=combined_text`
- **Candidate Labels**: `["SMiShing", "Other Scam", "Legitimate"]`
- **Hypothesis Template**: "This message is {}."

***Post-processing adjustments*** are applied via:

- boost_probabilities(...) to manually adjust scores based on keywords and URLs.
- incorporate_llm_label(...) to further refine scores using LLM-based classification.

---

## System Architecture & Workflow

1. **User Input:**
   - Accepts SMS text or a screenshot uploaded by the user.
2. **OCR (if needed):**
   - Uses Tesseract OCR to extract text from images.
3. **Language Detection & Translation:**
   - Detects the language using tools like LangDetect.
   - Translates text (if necessary) using Deep Translator.
4. **Zero-Shot Classification:**
   - Processes the text with the Hugging Face Transformers zero-shot classifier.
5. **Keyword & URL Analysis:**
   - Scans the text for suspicious keywords and URLs.
6. **Google Safe Browsing Check:**
   - Validates URLs against the Google Safe Browsing API for potential threats.
7. **Probability Boosting:**
   - Adjusts classification probabilities based on detected keywords and URLs.
8. **LLM-Based Classification & Explanation:**
   - Uses an LLM (e.g., GPT-3.5) to refine classification and generate a detailed explanation.
9. **Final Output:**
   - Displays the final classification (SMiShing, Other Scam, or Legitimate), confidence score, and an explanation via the interactive Gradio UI.

### Diagram Representation

<div align="center">
<img src="images/workflow.png" alt="Workflow Diagram" width="200" />
</div>

---

## Example URL Matches

| **Input**              | **Matched?**               |
|------------------------|----------------------------|
| `https://example.com`  | :white_check_mark: **Yes** |
| `http://test.org/path` | :white_check_mark: **Yes** |
| `example.com`          | :white_check_mark: **Yes** |
| `my-site.io/test`      | :white_check_mark: **Yes** |
| `randomtext`           | :x: **No**                |

---

## Dataset

This project uses the [SMS Spam Collection dataset](https://archive.ics.uci.edu/dataset/228/sms+spam+collection) from the UCI Machine Learning Repository. The dataset is converted into CSV format and augmented with additional examples to include three labels:

- **SMiShing**
- **Other Scam**
- **Legitimate**

---

## Initial Demo

Check out the initial demo deployed on Hugging Face Spaces:  
[SMS Scam Detection Demo](https://huggingface.co/spaces/hackerbyhobby/SMS_scam_detection)

---

## Effectiveness Check

### **1️⃣ Typical Zero-Shot Usage**
- The code **calls** the zero-shot classifier:
  ```python
  pipeline("zero-shot-classification", model="joeddav/xlm-roberta-large-xnli")
  ```
- It **uses candidate labels**:
  ```python
  ["SMiShing", "Other Scam", "Legitimate"]
  ```
- It applies a **hypothesis template**:
  ```python
  "This message is {}."
  ```
- This follows the **standard approach** for **zero-shot classification**, where the model predicts the most relevant label.

### **2️⃣ Overridden by Manual Boosting**
- **After** the zero-shot classification:
  - The function `boost_probabilities(...)` **manually adjusts** scores **based on keywords and URLs**.
  - The function `incorporate_llm_label(...)` **modifies scores further** using the **LLM's classification**.
- These **manual interventions** **significantly shift** probability distributions, sometimes **overriding the model's original predictions**.

## 📊 **Is It Used Effectively?**
The zero-shot classifier **does work**, but its **impact may be reduced** due to large **manual probability boosts**:

- A **URL detection** can **add +0.35** to `SMiShing`.
- The **LLM classification** can **add +0.2** to a label.
- These manual boosts may **overshadow** the original **zero-shot confidence scores**.

💡 **Conclusion:** While the zero-shot classification step is valid, its influence is **heavily adjusted post-processing**. This approach blends **ML-based classification with expert rule-based adjustments**, but it also means the original **model's confidence levels might not be the final determinant**. 🚀


---

## Contributing

Should we revive our final project? Let us know!
We welcome improvements, bug fixes, and new feature ideas. Feel free to open an issue or submit a pull request.

---

## Team

- **Joaquin Fuentes** – *Lead Developer & Repository Manager* 
- **Leslie Barrera Dorantes** – *Technical Documentation Lead* 
- **David Melara** – *Presentation & Visual Communication Specialist*
- **Ray George** – *Quality Assurance & Usability Testing Lead* 
- **Steven Sarvas** – *Keyword Strategy & Data Analyst*

---

## Future Work 

Building on the current capabilities of the SMiShing & Scam Detector, the following enhancements and improvements are planned:

- **Enhanced Safe Browsing Integration:**
  - **Additional Threat Intelligence:** Integrate extra safe browsing signals and threat feeds (e.g., VirusTotal, PhishTank) alongside Google Safe Browsing.
  - **Real-Time URL Monitoring:** Develop a component for continuously scanning and updating URL reputations in real time.

- **Model and Data Enhancements:**
  - **Dataset Expansion:** Augment the existing dataset with more diverse examples (including multi-language messages and emerging scam patterns) to improve model robustness.
  - **Advanced Transformer Models:** Experiment with newer transformer models to improve zero-shot classification performance and minimize the need for manual score adjustments.
  - **Continuous Learning:** Implement periodic retraining using new data and user feedback.

- **Improved Explainability and User Feedback:**
  - **Contextual Explanations:** Enhance model interpretability with deeper LLM-powered insights, offering more detailed context behind each classification.
  - **Interactive Feedback Loop:** Build a user feedback mechanism to report false positives/negatives, which will help in fine-tuning the model over time.

- **User Interface and Dashboard:**
  - **Dashboard Analytics:** Develop an analytics dashboard (within Gradio or as a separate web portal) to display trends, statistics, and overall performance metrics.
  - **Multi-Language & Accessibility Improvements:** Extend language support beyond English and Spanish and incorporate accessibility improvements based on user feedback.

- **Security and Privacy Enhancements:**
  - **Data Privacy:** Implement stricter data privacy measures to ensure no sensitive information is stored or transmitted without consent.
  - **Robust Error Handling:** Enhance logging and error handling to quickly identify and fix issues.

- **Documentation and Community Engagement:**
  - **Expanded Documentation:** Continue refining and expanding the documentation with more examples, tutorials, and best practices.
  - **Open-Source Collaboration:** Encourage community contributions by outlining clear contribution guidelines and hosting regular discussions or hackathons.

---

## Disclaimers & Warnings

   - **False Positives/Negatives:**
   No ML-based system is perfect. Always verify suspicious messages with additional checks.
   - **Privacy:**
   Avoid storing user data or images unless absolutely necessary.
   - **External Dependencies:**
   The performance and accuracy depend on Tesseract OCR, Hugging Face Transformers, and external translation libraries.

---


## References / Sources

- [SMS Spam Collection Dataset](https://archive.ics.uci.edu/dataset/228/sms+spam+collection) – UCI Machine Learning Repository.
- [Hugging Face Transformers Documentation](https://huggingface.co/docs/transformers/).
- [Google Safe Browsing API](https://developers.google.com/safe-browsing/).
- [Mermaid Documentation](https://mermaid.js.org/) – For creating diagrams.

---

## License

This project is licensed under the [MIT License](LICENSE).  
See the `LICENSE` file for details.

---
