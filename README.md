# Tree Classification for SEO Content Prioritization

## Overview

This project implements a lightweight machine learning workflow for prioritizing SEO content optimization opportunities using anonymized FlyRank internship data. The system uses search-related signals such as search volume, CTR, average position, engagement rate, and impressions to identify pages that may require optimization or monitoring.

## Who is this for?

This project is designed for:

* SEO analysts
* Content strategists
* Digital marketing teams
* Students learning applied machine learning on tabular business data

The output is a ranked content action queue that helps decide which pages should be refreshed first.

## Project Structure

```text
Internship/
├── work/
│   ├── notebooks/
│   ├── outputs/
│   └── figures/
├── submission/
│   └── paper_url.txt
├── paper.html
└── README.md
```

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Aadirwt/Internship.git
cd Internship
```

### 2. Install dependencies

```bash
pip install pandas scikit-learn matplotlib seaborn jupyter
```

### 3. Open the notebooks

```bash
jupyter notebook
```

Open the notebooks from:

```text
work/notebooks/
```

## Usage Example

Run the Week 5 modeling notebook:

```text
work/notebooks/w05_modeling_lane.ipynb
```

The notebook:

1. Loads the anonymized dataset
2. Creates the priority label
3. Splits the data by client groups
4. Trains a Decision Tree classifier
5. Compares it with the Week 4 rule-based baseline
6. Produces evaluation metrics and a ranked action queue

## Architecture Sketch

```text
SEO Dataset
     |
     v
Feature Selection
(search_volume, ctr, avg_position,
 engagement_rate, impressions_90d)
     |
     v
Priority Label Creation
     |
     v
Group-Based Train/Test Split
     |
     v
Decision Tree Classifier
     |
     v
Evaluation
(accuracy, confusion matrix, classification report)
     |
     v
Ranked Content Action Queue
```

## Evaluation Results

| Model           | Accuracy |
| --------------- | -------- |
| Week 4 Baseline | 1.00     |
| Decision Tree   | 1.00     |

Additional observations:

* Group-based validation was used to reduce client leakage risk.
* The model reproduced the rule-based logic very closely.
* Most prediction stability came from search volume and average position features.

## Example Output

| content_id | recommended_action                 | reason_code |
| ---------- | ---------------------------------- | ----------- |
| 101        | Refresh title and meta description | RC-01       |
| 102        | Add internal links                 | RC-02       |
| 103        | Improve search snippet             | RC-03       |
| 104        | Update outdated content            | RC-04       |
| 105        | Monitor only                       | RC-05       |

## Limitations

* The target label is derived from a heuristic baseline, not from real business outcomes.
* The dataset is anonymized, so domain-level SEO effects cannot be analyzed.
* The model supports **decision prioritization**, not causal claims about search ranking improvements.
* Additional historical time-window data would be needed for production deployment.

## Guardrails

This project avoids:

* client names
* domain names
* private search queries
* raw production exports
* claims that a recommendation will improve Google rankings

Human review is required before applying any recommendation to a real website.

## Reproducibility

The repository contains:

* the modeling notebook
* validation notebooks
* exported ranked action queue
* the deployed research paper (`paper.html`)

The exact deployed paper URL is stored in:

```text
submission/paper_url.txt
```

## Author

**Aaditya Singh Rawat**

Machine Learning Internship – FlyRank

## Data Credit

Built on the **FlyRank ML Internship dataset** and learning materials.

https://flyrank.ai
