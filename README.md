# Intelligent-document-processing
🚀 Intelligent Document Processing (IDP) – Final Robust Version
📌 Project Overview

This project demonstrates an AI-based Intelligent Document Processing (IDP) pipeline implemented using Google Colab.
It extracts structured information from scanned documents using a combination of:

OCR (EasyOCR)

Rule-based NLP (Regex + business logic)

Optional Generative AI (Google Gemini) for refinement

The solution is designed to be practical, explainable, and reliable, aligning with real-world document processing requirements.

🎯 Objective

Extract text from a document image using OCR

Identify and structure key fields in JSON format

Demonstrate how NLP and LLMs can improve extraction accuracy

📄 Selected Document Type

GST Tax Invoice

This document type was chosen because it contains structured but layout-varying fields such as:

Company name & GSTIN

Invoice number and date

Taxable amount, GST, and total amount

🛠️ Tools & Technologies Used
Category	Tool
Programming Language	Python
OCR	EasyOCR
NLP	Regex-based rule extraction
LLM (Optional)	Google Gemini
Environment	Google Colab
Visualization	PIL, Matplotlib
🔁 Processing Pipeline
1️⃣ Dependency Installation

Required libraries are installed at runtime in Google Colab:

pip install easyocr pillow matplotlib google-generativeai

2️⃣ Image Upload

The user uploads an invoice image during execution.

No hardcoded file paths or URLs are used.

3️⃣ OCR – Text Extraction

EasyOCR is used to extract raw text from the image.

OCR bounding boxes are visualized to verify text detection accuracy.

4️⃣ Rule-Based NLP Extraction

Regex rules and heuristics are applied to extract:

Company name

GSTIN

Invoice number

Invoice date

Monetary values

Business Logic Validation

GST rules are applied to improve reliability:

IGST = 18% of Taxable Amount
Taxable Amount + IGST ≈ Total Amount


This step helps disambiguate numeric values produced by OCR.

5️⃣ Optional LLM Refinement (Gemini)

The user can optionally provide a Gemini API key at runtime.

Gemini refines extracted fields from noisy OCR text.

If the API key is skipped or fails, the pipeline safely falls back to rule-based extraction.

📤 Output Format (JSON)

Example structured output:

{
    "document_type": "GST Tax Invoice",
    "company_name": "Gujarat Freight Tools",
    "gstin": "24HDE7487RFSR14",
    "invoice_number": "GST112020",
    "invoice_date": "04-Mar-2020",
    "taxable_amount": 1154.0,
    "igst": 103.86,
    "total_amount_after_tax": 1258.0
}

🧠 Improving Accuracy Using NLP / LLMs

To improve accuracy beyond basic OCR, the following NLP and LLM-based strategies can be applied:

1️⃣ Context-Aware Extraction

Regex relies on fixed patterns, which may fail with noisy OCR or layout changes.
LLMs can use contextual understanding to infer fields based on surrounding text (e.g., identifying invoice numbers near “Invoice No”).

2️⃣ OCR Noise Correction

OCR outputs often contain spelling mistakes or broken words.
LLMs can perform post-OCR normalization, correcting common OCR errors before extraction.

3️⃣ Schema-Guided JSON Extraction

LLMs can be prompted with a strict JSON schema, ensuring:

Correct field names

Proper data types

Missing values returned as null instead of hallucinated data

4️⃣ Hybrid Validation with Business Rules

Deterministic rules (such as GST percentage validation) are applied first.
LLMs can then:

Re-check mismatched values

Suggest corrections

Flag low-confidence fields

This hybrid approach prevents blind trust in AI outputs.

5️⃣ Generalization Across Layouts

LLMs can adapt to different invoice formats and vendors, reducing the need for document-specific regex rules.



This project uses rule-based NLP as the primary extraction layer and LLMs only as an optional refinement step.
This ensures:

Explainability

Reduced hallucination

Reliable and auditable results

▶️ How to Run (Google Colab)

Open the provided Colab notebook

Run the cell

Upload an invoice image

(Optional) Enter Gemini API key

View extracted structured JSON output

✅ Key Highlights

Single-cell execution in Colab

Clean, readable Python code

Explainable extraction logic

Business-rule validation (GST math)

Optional AI enhancement

Evaluation and interview ready

👤 Author

Manan Ramani
B.Tech CSE (2nd Year)
Interests: AI, NLP, Intelligent Document Processing
