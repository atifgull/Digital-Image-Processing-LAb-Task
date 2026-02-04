# DIP_OEL_2023_SE_26: Lesion Segmentation & Classification from Dermoscopic Images

## SUBMITTED BY: ATIF GULL KHAN
## Overview
This project focuses on the segmentation and classification of skin lesions from dermoscopic images, using the PH2 dataset. The workflow includes image enhancement, hair removal, lesion segmentation, feature extraction, and classification using machine learning. The project is implemented in Python and is designed to run in a Google Colab environment with Google Drive integration for dataset access.

## Project Structure
- **DIP_OEL_2023_SE_26.ipynb**: Main Jupyter notebook containing all code, explanations, and results.
- **PH2Dataset**: Directory in Google Drive containing the PH2 dataset images and labels.
- **generated_masks**: Directory where generated lesion masks are saved.

## Workflow & Steps

### 1. Environment Setup
- Mount Google Drive to access the dataset.
- Set base paths for images, masks, and label files.

### 2. Data Exploration
- List and verify the contents of the dataset directory.
- Preview the label file (`PH2_dataset.txt`).

### 3. Image Processing Pipeline
#### a. Image Enhancement
- Enhance image contrast using CLAHE in LAB color space.

#### b. Hair Removal
- Remove hair artifacts using black-hat morphological operation and inpainting.

#### c. Lesion Segmentation
- Convert image to grayscale, apply Gaussian blur, and use Otsu's thresholding.
- Post-process with morphological closing and hole filling to refine lesion mask.

### 4. Mask Generation
- For each image folder:
  - Load the dermoscopic image and ground truth mask.
  - Apply enhancement and hair removal.
  - Segment the lesion and save the predicted mask.
  - Collect ground truth and predicted masks for evaluation.

### 5. Segmentation Evaluation
- Compute confusion matrix, accuracy, sensitivity, and specificity for the generated masks.

### 6. Feature Extraction
- Extract mean and standard deviation for each BGR channel within the lesion mask.
- Build a feature matrix for all images.

### 7. Classification
- Load labels from the dataset file.
- Split data into training and test sets.
- Train a Random Forest classifier on extracted features.
- Evaluate classifier performance (accuracy, classification report).

## Key Functions
- `enhance_image(img)`: Enhances image contrast.
- `remove_hairs(img)`: Removes hair artifacts.
- `segment_lesion(img)`: Segments the lesion area.
- `extract_features(img, mask)`: Extracts features from the masked region.

## Requirements
- Python 3.x
- OpenCV
- NumPy
- Pandas
- scikit-learn
- tqdm
- Google Colab (for Drive integration)

## How to Run
1. Open the notebook in Google Colab.
2. Mount your Google Drive.
3. Ensure the PH2 dataset is available at the specified path in your Drive.
4. Run all cells sequentially to perform segmentation, feature extraction, and classification.

## Notes
- Paths are set for Google Colab; adjust if running locally.
- The project assumes the PH2 dataset folder structure as used in the code.
- The code includes checks for missing images/masks and prints summary statistics.

## Results
- The notebook prints segmentation metrics and classification accuracy.
- Sample outputs and label distributions are displayed for verification.

---
**Author:** DIP_OEL_2023_SE_26 Team
