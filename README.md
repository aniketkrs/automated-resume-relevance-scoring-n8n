## **ATS Resume Relevance Scoring Workflow – n8n**

This project is an automated ATS-style resume relevance scoring system built using n8n. The workflow continuously monitors a Google Drive folder for new resumes, extracts and validates candidate details, handles unreadable or scanned resumes using OCR, compares each resume against a Job Description, and automatically logs the score, reasoning, and candidate status in Google Sheets.

The goal of this project is to demonstrate a real-world, scalable hiring workflow that produces explainable AI-driven resume evaluation instead of just keyword matching.

---

## **🔁 How the Workflow Works**

1. A new resume PDF is uploaded to the Google Drive “Resumes” folder.
2. The resume is downloaded, text is extracted, and key fields are validated (name, email, phone, readable text).
3. If the text is not readable, the workflow runs OCR. If OCR still fails, the resume is marked unreadable and logged.
4. For valid resumes, the Job Description file is downloaded and its text is extracted.
5. The resume text and JD text are merged and sent to an AI model for evaluation.
6. The AI returns a relevance score (0–100), reasoning, and matched / missing skills.
7. If the score is ≥ 85, the candidate is added to the Approved sheet and receives an approval email.
8. If the score is below 85, the candidate is added to the Rejected sheet and receives a rejection email.
9. All results are logged in Google Sheets for transparency and review.

---

## **📂 Project Structure (Single Workspace Folder)**

Inside one main Google Drive folder:

* 📁 **Resumes** — incoming candidate resume PDFs
* 📁 **Job Description** — JD reference file
* 📁 **Results Sheet** — Google Sheet for evaluation logs

This structure keeps the workflow portable, organized, and easy to maintain.

---

## **🛡️ Edge Cases Handled**

* Missing details like name, phone, or email → marked unreadable and logged
* Unscannable or image-only resumes → sent through OCR, then re-validated
* OCR still unreadable → logged and stopped safely
* Blank or very short resumes → treated as invalid
* AI failure or bad JSON → fallback AI agent rescues the scoring
* Duplicate resumes → logged and flagged
* JD missing or inaccessible → workflow stops safely with error note
* Scoring API timeout → retry once, then log as processing failure

---

## **🧠 Why This Workflow Is Valuable**

* Produces **explainable scoring**, not black-box matching
* Handles real hiring scenarios like scanned resumes and missing data
* Reduces manual recruiter effort
* Creates a structured, auditable evaluation trail
* Demonstrates **automation + AI + data validation together**

This system behaves much closer to an **actual ATS pipeline** rather than a simple automation script.

---

## **🚀 Future Enhancements (Ideas for Scalability & Quality)**

* Skill-weighting based on JD priority
* Tiered scoring bands (Strong / Partial / Weak match)
* Resume enrichment via LinkedIn lookup
* Language quality and formatting signals
* Batch resume processing for bulk hiring
* Dashboard analytics report layer

These ideas show how the workflow can evolve into a recruitment intelligence system.

---

## **🧾 Assignment Context**

This project was built as part of an **Automated Resume Relevance Scoring Workflow assignment**, focusing on:

* automation
* explainability
* edge-case handling
* real-world hiring logic

The workflow JSON can be exported directly from n8n and submitted as part of the assignment deliverable.

---

## **📌 Tech Stack**

* n8n (automation engine)
* Google Drive (file storage)
* Google Sheets (result logging)
* OCR API (fallback for unreadable resumes)
* AI model for scoring and reasoning

---
