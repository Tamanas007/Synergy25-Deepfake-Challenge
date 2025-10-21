# Synergy'25 Deepfake Challenge: Predicting the Distribution

This repository contains our winning approach for the Synergy'25 Deepfake Challenge. This project focuses on building a model to accurately mimic the outputs of a proprietary deepfake detector.


 # Project Overview


 The core challenge of this hackathon was not to create a state-of-the-art deepfake detector from scratch, but to reverse-engineer and replicate the predictive behavior of an existing "black box" model. Our initial data analysis revealed that this proprietary model was imperfect, occasionally misclassifying both real and fake images. This discovery became the cornerstone of our strategy: to succeed, we had to teach our model to replicate the target model's unique quirks and errors.


#  Key Methodology



  pipeline was designed to systematically address this unique challenge:

Unified Data Preparation: We began by creating a single master_labels.csv file. This crucial step mapped all 2,000 training images to their true target labels as defined by the proprietary model's JSON predictions, including its mistakes.

Optimized Model Architecture: We chose a ResNet18 model, pre-trained on ImageNet. This architecture is powerful yet efficient, making it highly effective for the 32x32 image size of the dataset and helping to mitigate overfitting.

Robust Training & Regularization: To ensure our model generalized well and didn't simply memorize the data, we implemented several key regularization techniques:

Increased Dropout

Weight Decay in the AdamW optimizer

Random Erasing data augmentation

# Final Prediction: 
The final, trained model was used to generate predictions on the 500 unseen test images, resulting in our final submission file.




# Getting Started


 Prerequisites

Python 3.8+

Jupyter Notebook or Jupyter Lab

PyTorch & Torchvision

Pandas

Scikit-learn

tqdm

You can install all dependencies with a single command:



pip install notebook torch torchvision pandas scikit-learn tqdm



# Data Setup

Download the official hackathon dataset.(links given below)

Unzip the contents into a folder named hackathon_dataset.

Place this hackathon_dataset folder in the same root directory as the Jupyter Notebook/COLAB
https://drive.google.com/file/d/1HlpoKbFAIUORexzLpB14x0sS17eBAj69/view?usp=sharing, https://drive.google.com/drive/folders/1UkrHA7DhWaIqaaqN98ZYncUa7gFo2K84?usp=sharing, https://drive.google.com/drive/folders/1iimPVX95QDGHtUz7DrAEmseRWRaAF-n8?usp=sharing, https://drive.google.com/drive/folders/1uPO7R4cP9DohAwqazD_20JvQYC3fTqln?usp=sharing, https://drive.google.com/file/d/1xphKCuODz8WawUaJpmMtiQY_Q7Y0pp9a/view?usp=sharing




# How to Run

The entire pipeline, from data preparation to final prediction, is contained in the Synergy25_Submission.ipynb notebook.

Launch Jupyter Notebook from your terminal:

jupyter notebook


Open the Synergy25_Submission.ipynb file.

To execute the entire project, click Kernel -> Restart & Run All from the menu.




 Results

Our best model achieved a validation accuracy of 89.75% on the held-out validation set.
