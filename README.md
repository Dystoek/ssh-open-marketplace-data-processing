# ssh-open-marketplace-data-processing
SSH Open Marketplace – Data Processing Tasks (Duplicate Detection &amp; Item Type Conversion)

## Overview

This repository contains my submission for the Research Software Engineer / Technical Developer take-home assessment for the SSH Open Marketplace (DARIAH ERIC).

The goal of the assessment was to explore the public API, process its data using Python, and present the results in a clear, explainable, and reproducible way.

I completed two tasks:

- **Option A – Item Type Conversion**
- **Option B – Duplicate Detection**

The focus throughout the work is on clarity, reasoning, and practical applicability rather than building overly complex solutions.

---

## Option A – Item Type Conversion

In this task, I convert a **Publication** record into a draft **Dataset** record.

### Key aspects:
- Field-by-field mapping between source and target schemas
- Explicit handling of:
  - directly reusable fields
  - fields requiring transformation
  - fields that cannot be safely inferred
- Preservation of provenance using a `derivedFrom` block
- Inclusion of a `curation` section to flag manual review requirements

The output is a **valid JSON draft** that could, in principle, be submitted back to the API after curator validation.

---

## Option B – Duplicate Detection

In this task, I identify likely duplicate or near-duplicate records in the **tool-or-service** category.

### Approach:
- Fetch a sample of records using API pagination
- Normalize text and URLs for consistent comparison
- Apply layered matching:
  - exact matches (URLs, identifiers)
  - fuzzy matching on normalized titles
- Assign confidence levels (high / medium / low)
- Produce a review table for human validation

### Outcome:
The approach reduces a large dataset into a small, actionable list of candidate duplicates supported by clear evidence.

---

## Key Design Principles

- **Explainability over complexity**
- **Safe data handling (no assumptions or fabricated metadata)**
- **Human-in-the-loop workflow**
- **Reproducible and readable code**

---

## Project Structure
├── option_a/
│ ├── SSH_Open_Marketplace_Publication_to_Dataset_Conversion.ipynb
│ └── converted_publication_to_dataset_draft.json
│
├── option_b/
│ └── SSH_Open_Marketplace_Duplicate_Detection.ipynb
│
├── requirements.txt
└── README.md



---

## How to Run

1. Create a Python environment (Python 3.9+ recommended)
2. Install dependencies:

```bash
pip install -r requirements.txt
