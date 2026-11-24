# Fetal Ultrasound Image Classification Using Deep Learning

## 1. Project Overview

This project focuses on the classification of fetal ultrasound images using deep learning techniques. The objective is to automatically classify ultrasound images into six anatomical or examination-plane categories using a Convolutional Neural Network (CNN).

The project uses a **ResNet18 architecture** with ImageNet pretrained weights and explores different fine-tuning strategies to evaluate their impact on classification performance.

## 2. Dataset

The project uses the **FETAL_PLANES_DB** dataset.

- Dataset: FETAL_PLANES_DB
- Total images: 12,400
- Total patients: 1,792
- Number of classes: 6

### Classification Categories

1. Fetal abdomen
2. Fetal brain
3. Fetal femur
4. Fetal thorax
5. Maternal cervix
6. Other

**Dataset source:**  
[Zenodo – FETAL_PLANES_DB](https://doi.org/10.5281/zenodo.3904280)

Note: The original dataset images are not included in this repository. Download the dataset from the official source and place the images and metadata in the `data/` directory.

## 3. Project Structure

```text
Fetal_Ultrasound_Project/
│
├── data/
│   ├── FETAL_PLANES_DB_data.csv
│   └── splits/
│       ├── train.csv
│       ├── validation.csv
│       └── test.csv
│
├── notebook/
│   ├── 01_Data_Understanding.ipynb
│   ├── 02_Data_Preprocessing.ipynb
│   ├── 03_Baseline_Mode.ipynb
│   ├── 04_Model_Evaluation.ipynb
│   ├── 05_Error_Analysis.ipynb
│   ├── 06_Improved_Model.ipynb
│   ├── 07_Finetuned_ResNet18.ipynb
│   └── 08_Full_Fine_Tuning.ipynb
│
├── models/
│
├── results/
│
├── Original/
│
├── README.md
└── requirements.txt
```

## 4. Data Preprocessing

The following preprocessing steps were applied:

- Image resizing to 224 × 224 pixels.
- Conversion of images into PyTorch tensors.
- Image normalization using ImageNet mean and standard deviation.
- Random rotation and horizontal flipping for training augmentation.
- Patient-level data splitting to prevent patient overlap between training, validation, and test sets.

### Dataset Split

| Dataset | Images | Patients |
|---|---:|---:|
| Training | 6,217 | 761 |
| Validation | 912 | 135 |
| Testing | 5,271 | 896 |
| **Total** | **12,400** | **1,792** |

## 5. Model Architecture

**ResNet18** was selected as the primary deep learning architecture.

Key components:

- Pretrained ResNet18 using ImageNet weights.
- Modified fully connected layer for six output classes.
- Cross-entropy loss function.
- Adam optimizer.
- Batch size: 16.
- Input image size: 224 × 224 pixels.

## 6. Experiments

Four experimental configurations were evaluated:

1. Baseline ResNet18 with pretrained ImageNet weights.
2. Partial fine-tuning with class weights.
3. Partial fine-tuning without class weights.
4. Full fine-tuning of ResNet18.

## 7. Experimental Results

### Test Accuracy Comparison

| Experiment | Test Accuracy |
|---|---:|
| Baseline ResNet18 | **93.72%** |
| Full Fine-tuning ResNet18 | 92.51% |
| Partial Fine-tuning without Class Weights | 89.96% |
| Partial Fine-tuning with Class Weights | 89.34% |

The baseline ResNet18 achieved the highest test accuracy of **93.72%** among the evaluated configurations.

### Best Model

- Architecture: ResNet18
- Training strategy: Transfer learning with pretrained ImageNet weights
- Test accuracy: 93.72%
- Weighted F1-score: 93.71%
- Macro F1-score: 92.99%

## 8. Results and Analysis

The project includes:

- Training and validation curves.
- Confusion matrices.
- Classification reports.
- Test predictions.
- Error analysis.
- Comparison of experimental configurations.

These results help evaluate class-wise performance and identify categories that are more difficult to classify.

## 9. Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## 10. How to Run

1. Clone the repository:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Fetal_Ultrasound_Project
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Download the FETAL_PLANES_DB dataset from the official Zenodo source.

4. Place the dataset files in the appropriate `data/` directory.

5. Open Jupyter Notebook:

```bash
jupyter notebook
```

6. Run the notebooks in numerical order, starting with `01_Data_Understanding.ipynb`.

## 11. Limitations

- The experiments were conducted using a limited set of training configurations.
- Training was performed on a CPU environment.
- Further validation on independent datasets is required to assess generalization.
- This project is an academic image-classification study and is not intended for clinical diagnosis or medical decision-making.

## 12. Acknowledgement

We acknowledge the creators of the FETAL_PLANES_DB dataset for making the ultrasound image dataset publicly available for research.

---

**Project:** Fetal Ultrasound Image Classification Using Deep Learning  
**Primary Model:** ResNet18  
**Best Test Accuracy:** 93.72%
