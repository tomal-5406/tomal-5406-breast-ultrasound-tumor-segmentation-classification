**Phase I: Processing and Organizing Dataset**


---
1. Unzip the Training Dataset of original images and their corresponding masks
2. Separate the Masks from Original USG image and save them into another directory.
3. Sort/ Allign the masks with their corresponded USG images.
4. Count total masks and original images.
5. If there any multiple masks are detected, merge them into single mask.
6. Again check if the number of masks and their corresponded USG image is equal or not.
7. Preprocess,resize and enhance the training dataset as well as removing writings and artifacts.
8. Evaluate the processed images with previous unprocessed images through some common image quality metrices.
9. Save the processed images and delete the unprocessed images to clean memory.
10. Now, Masks and their corresponding Processed images are Ready as Training inputs for next phase.

**Phase II: Building Hybrid Segmentation Model**

---
1. Split the datast(Processed in Phase-I) into train and test sets.
2. Apply Spatial Attention.
3. Fed it to Convo2D Block attention.
4. Fed the extracted features into Unet Model Architecture.
5. Initialize the model and set hyperparameter.
6. A Hybrid Architecture is ready. Train the defined Model.
7. Now, The Hybrid model is successfully trained.
8. Save and preserve the generated model weights for further use.

**Phase III: Segmenting a different Breast USG image Dataset**

---
1. Unzip and clean the dataset which is to be used for segmenting ROI.
2. Load the dattaset for inspecting.
3. There found some images in the wrong class.eg. some malignant images are found in benign class and some benign images found in malignat class.
4. Transfer the miss-classed images to their correct class.
5. Preprocess the dataset in the same technique as mentioned in Phase-I, point 7.
6. Save the processed files and delete pervious unprocessed files.
7. Load trained weight generated from Hybrid Unet segmantation model.
8. Apply the model weights to segment ROI of Benign and Malignant tumor from breast USG images.
9. Inspect the segmentation masks for both benign and malignant classes.
9. ROIs are segmented successfully and saved as segmentation masks.
10. Now, perform Bitwise AND operation between segmentation masks and their corresponded proccessed images to locate the exact positions of tumors.
11. Save and Zip the result of point 11 for classification tasks.
12. ROI of a different Dataset is successfully segmented for a classification tasks.

**Phase IV: Classification of newly segmented dataset**

---
1. Unzip and Load the newly segmented dataset for classification.
2. Check if the classes are imbalance or not.
3. The imbalanceness of the classes are later handled through image augmentation during traing time.
4. Split the dataset into train, test and validation sets.
5. Initially applied a custom hybrid classification model-RkoNet13 for classification task but it poorly performed in validation accuracy.
6. Then some pre-trained Trasfer-Learnig models (VGG16, ResNet50, InceptionV3 and DenseNet121) are implemented for classification tasks.
7. The model performances are evaluated by Confusion Matrix, ROC-AUC curve, Training-Validation accurcy and loss curve.
8. Now, the best performing model can be considered for ablation study or as the base of a hybrid classification model.
