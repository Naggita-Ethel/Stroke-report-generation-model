This project implements an end-to-end automated radiology report generation system for stroke CT scans using BLIP (Bootstrapping Language-Image Pre-training), a vision-language transformer model. The complete pipeline spans from raw medical data extraction to trained model deployment.

# Stroke Report Generation Model

## Overview
This repository contains code and resources for generating radiology reports from stroke CT scans using deep learning. The workflow includes data extraction, preprocessing, report parsing, dataset creation, and summary statistics.

## Workflow Steps
1. **Environment Setup**: Checks for GPU availability and installs required packages (e.g., PyMuPDF).
2. **Data Extraction**: Mounts Google Drive and sets up folder paths for infarct and normal patient data.
3. **Unzipping**: Automatically unzips medical data folders if needed.
4. **Report Parsing**: Extracts diagnostic sections (Findings, Conclusion) from PDF/TXT reports using regex normalization.
5. **Image & Report Collection**: Recursively scans patient folders to collect image files and associated reports.
6. **Dataset Creation**: Builds a structured dataset with patient IDs, categories (acute, chronic, lacunar, combination, normal), image paths, and cleaned report text.
7. **Summary Statistics**: Computes and prints category breakdown and previews sample entries.
8. **Export**: Saves the cleaned dataset as a JSON file for downstream modeling.

## Dataset Structure
- **Patient Categories**: Acute, Chronic, Combination or Unclear, Lacunar, Normal
- **Data Fields**: Patient ID, Category, Image Paths, Report Text
- **Output**: `ct_reports_dataset_cleaned10.json` (structured dataset for model training)

## Usage
Run the notebook `stroke_report_generation_model.ipynb` step-by-step:
- Mount your Google Drive and set the base directory for your data.
- Ensure all zip files are extracted.
- Execute cells to process folders, extract reports/images, and generate the dataset.
- Review summary statistics and sample entries.
- Download the cleaned dataset for further modeling.

## Requirements
- Python 3.x
- PyMuPDF
- Google Colab (for Drive mounting and file download)
- Torch (for GPU checks)

## Notes
- The code skips incomplete patient folders (missing images or reports).
- Diagnostic sections are normalized for consistency.
- The dataset is suitable for training vision-language models for automated report generation.

## License
This project is for research and educational purposes. Please cite appropriately if used in publications.
