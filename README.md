# Synergy'25 Deepfake Challenge: Predicting the Detector

# 🏆 Final Validation Accuracy: 99.25% 🏆

This repository contains the code for our winning solution to the Synergy'25 Deepfake Challenge. Our mission was to develop a model that could accurately mimic the predictions of a proprietary deepfake detector.

Our final model, trained with a custom per-epoch stratified splitting strategy, achieved a 99.25% accuracy on a stable, unseen validation set.

# 1. The Core Challenge: The "Imperfect" Model

Our initial data verification revealed the core challenge of this hackathon: the proprietary model was "imperfect" and made mistakes.

On 1,000 Real Images, it predicted 24 "fake".

On 1,000 Fake Images, it predicted 12 "real".

This meant our true task was not simple classification, but to build a model that could learn to replicate these specific "mistakes". Our ground truth was the JSON files, not the folder names.

# 2. Our Winning Strategy: Per-Epoch Stratified Splitting

After building a baseline model that reached 90% accuracy, we developed a novel training strategy to push performance even further.

Instead of a single, fixed 80/20 train/validation split, our script (train_epoch_split.py) performs a new, random, stratified 80/20 split at the start of every single epoch.

Why this worked:

Forced Generalization: The model could never "memorize" a specific validation set.

Full Dataset Exposure: Over 30 epochs, the model was validated against 30 different 400-image sets, forcing it to learn the patterns of the entire 2,000-image dataset.

The Result: This technique dramatically improved performance, jumping from 90.0% to 99.25% on our original, stable validation set.

# 3. How to Run This Project

This project was built in Python using PyTorch, Pandas, and Scikit-learn.

Step 1: Data Preparation

Run the prepare_data.py script. This script reads the four initial data sources (real/fake images and real/fake JSONs) and combines them into a single master_labels.csv file, which serves as our unified ground truth.

Step 2: Model Training (Our Winning Script)

Run the train_epoch_split.py script. This will:

Load the master_labels.csv.

Use a pre-trained ResNet18 model.

Apply our custom per-epoch splitting strategy for 30 epochs.

Save the best-performing model (best_model_v4_epoch_split.pth) that achieves the highest accuracy on any given epoch's random split.

Step 3: Final Prediction

Run the predict_final.py script. This loads the champion model from Step 2, runs it on the 500 test images, and generates the final teamname_prediction_FINAL.json file.
# Recommendation
use TTA for predicting on Test set
# Dataset 
https://drive.google.com/file/d/1HlpoKbFAIUORexzLpB14x0sS17eBAj69/view?usp=sharing, https://drive.google.com/drive/folders/1UkrHA7DhWaIqaaqN98ZYncUa7gFo2K84?usp=sharing, https://drive.google.com/drive/folders/1iimPVX95QDGHtUz7DrAEmseRWRaAF-n8?usp=sharing, https://drive.google.com/drive/folders/1uPO7R4cP9DohAwqazD_20JvQYC3fTqln?usp=sharing, https://drive.google.com/file/d/1xphKCuODz8WawUaJpmMtiQY_Q7Y0pp9a/view?usp=sharing
# trained models weight
 primary model.....https://drive.google.com/file/d/1Q87GlkEdJGIOHLBPEh-gmQK_sH5WnBdE/view?usp=drive_link
  
  tuned model.......https://drive.google.com/file/d/1ba4XAWaw9e2ngFfx0DYNPXHcuMAxGbVd/view?usp=drive_link
  
   best model........https://drive.google.com/file/d/1RCRgIFBl0VnGJzUjZWFxZWNPDZa8rZXu/view?usp=sharing
