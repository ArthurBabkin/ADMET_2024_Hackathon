# ADMET 2024 Prediction Hackathon Solution

Welcome to the repository for our solution to the ADMET 2024 Prediction Hackathon! This project involves building predictive models for various ADMET (Absorption, Distribution, Metabolism, Excretion, and Toxicity) properties, which are crucial in drug discovery to determine how a drug behaves in the human body.

# Link to original competition
- https://www.kaggle.com/competitions/admet-prediction
- https://aistudy.innopolis.university/admet

## Competition overview

In this competition, we focused on predicting specific ADMET properties using machine learning models. We worked with three classification datasets, each utilizing SMILES (Simplified Molecular Input Line Entry System) strings to represent molecular structures. The challenge was to build accurate models that can generalize well and perform effectively on an independent test set.

Our approach involves generating new molecular structures by modifying existing ones, featurizing them using molecular fingerprints, and training a RandomForestClassifier model for each property.

## Repository overview
The project repository contains the following files and folders:
- notebooks/: This folder contains notebooks with various experiments and models, including GNN, RandomForest, CatBoost, GradBoost and etc. Also we tried to extend data and tried to use ensemble of trees. We compared all of them using ROC AUC score.
- README.md: A file describing the project.
- best_algorithm.ipynb: The main notebook with the best of the algorithm in the meaning of ROC AUC score. The description of this algorithm below.
- train_set_example.csv: The training dataset containing labeled data used to train our models. Includes chemical structures, binary outcomes, and other relevant properties. NOT FULL VERSION, just example, ask the organizers to give you full version or use open-source data from internet.
- test_set_example.csv: The test dataset used to generate predictions for model evaluation. NOT FULL VERSION, just example, ask the organizers to give you full version or use open-source data from internet.
- sample_submission_example.csv: A sample submission file format to Kaggle.

### Columns

- **Drug_ID**: Unique identifier for each drug or compound.
- **Drug**: The chemical structure represented in SMILES notation.
- **Y**: The target variable for classification (binary outcome).
- **Property**: The specific ADMET property being predicted.

## Approach

1. **Data Augmentation**: We generated new molecular structures by systematically altering existing ones, ensuring the augmented data retained meaningful chemical properties.
   
2. **Featurization**: We used molecular fingerprints, combining MACCS keys, ECFP4, and 2D RDKit descriptors, to represent the chemical structures numerically.
   
3. **Modeling**: We trained separate RandomForestClassifier models for each property, employing stratified train-test splits and data upsampling to address class imbalances.

4. **Evaluation**: Models were evaluated based on the Area Under the ROC Curve (ROC AUC) metric, with higher scores indicating better performance.

## Installation

To run the code, you'll need the following Python packages:

```bash
pip install rdkit scikit-learn imbalanced-learn datamol
```

## Usage

1. **Train the Model**: Use the provided code to train the model on the training dataset. The code is organized to handle each ADMET property separately.

2. **Generate Predictions**: After training, use the model to generate predictions on the test dataset. These predictions can be saved in the format required for submission.

3. **Submission**: The final predictions should be formatted as specified in the competition guidelines and submitted for evaluation.

## Code Overview

The main steps in our code include:

- Loading and preprocessing the data.
- Augmenting the data by generating new molecular structures.
- Featurizing the molecules using fingerprint vectors.
- Training RandomForest models for each ADMET property.
- Generating predictions and formatting them for submission.

## Contributing

Feel free to fork this repository and submit pull requests. We welcome improvements and suggestions!

Here's how you can include the future research topics in your README file:

## Future Research Directions
1. **Unified Model for All Features**
   - We see promising perspectives in the development of a single, unified model that can efficiently handle all features. This approach could potentially enhance the model's generalizability and predictive power across different ADMET properties, streamlining the process and improving performance.

2. **Expanded Use of Descriptors with Feature Selection**
   - Future work will explore the integration of a broader range of descriptors, including but not limited to:
     - **desc3D** and **desc2D**
     - **mordred**
     - **cats2D** and **cats3D**
     - **pharm2D** and **pharm3D**
     - **scaffoldkeys** and **skeys**
     - **electroshape**
     - **usr** and **usrcat**
   - Alongside the inclusion of these descriptors, we will implement robust feature selection techniques to identify the most predictive and relevant features, enhancing the model's accuracy and reducing computational complexity.

3. **Further Oversampling and Data Augmentation**
   - We aim to continue refining our oversampling strategies to address class imbalances more effectively. Additionally, further data augmentation techniques will be explored to enrich the dataset, potentially uncovering new patterns and relationships that can improve model performance.

## Meet the Team
Our project was developed by a dedicated team of students from various universities, bringing together a diverse set of skills and expertise:

- Ilyas Galiev - Innopolis University
- Nikita Tsukanov - Innopolis University
- Nikita Zagainov - Innopolis University
- Maksim Demekhin - ITMO University
- Arthur Babkin - Innopolis University
- Khusejin Agadzhanov - HSE University

## License

This project is licensed under the MIT License.
