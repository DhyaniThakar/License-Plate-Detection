# License-Plate-Detection
This project is associated with the course **APS360 (Fundamentals of Deep Learning) in the University Of Toronto**.
### Project Overview
This project focuses on large-scale license plate detection using machine learning techniques. The primary goal is to develop a robust system capable of automatically detecting and recognizing license plates from vehicle images, which can be applied to traffic management, security, and theft prevention. The project leverages both traditional image processing methods and deep learning models to achieve accurate license plate detection and character recognition.

### Key Components
#### 1. License Plate Detection and Character Segmentation
- Tools: OpenCV
- Dataset: A custom dataset of **50** car images sourced from Kaggle, Flickr and Google was constructed. 
- Process:
  - Resizing to 256 x 256 pixels.
  - Convert vehicle images to grayscale.
  - Apply edge detection and contour identification to locate the license plate.
  - Crop the image to isolate the license plate area.
  - Further segment individual characters from the cropped license plate image for recognition.

#### 2. Alphanumeric Character Recognition
- Tools: Convolutional Neural Network (CNN)
- Dataset: A custom dataset containing **35 classes (A-Z and 0-9)**, excluding letter “O” to avoid confusion with the number “0”. The alphanumeric dataset contains **350** images per class, resulting in **12,250** images in total.
- Process:
  - Train a CNN model to recognize individual characters from the license plate.
  - The model uses two convolutional layers, batch normalization, pooling layers, and a fully connected layer.
  - Hyperparameters include a learning rate of 0.0001, batch size of 64, and 15 epochs.

#### 3. License Plate Prediction
- Process:
  - The segmented characters from the detection phase are passed through the trained CNN model.
  - The predictions for each character are combined to reconstruct the full license plate number.

#### 4. Performance Evaluation: Character-by-Character Accuracy
- Process:
  - To assess the model's performance, especially in cases where predictions are close but not exact, character-by-character accuracy is calculated.
  - The **Levenshtein Distance metric** is used to compare the predicted license plate with the actual label, providing a more nuanced evaluation of model accuracy.
  - This approach allows for partial credit when the model correctly predicts some characters but not others, offering a more fair and detailed assessment.

### Results
#### Quantitative Results
- The final CNN model for alphanumeric recognition achieved a validation accuracy of **98.50%** and a test accuracy of **99.64%**.
- The character-by-character accuracy metric showed that even in cases of partial prediction, the model was able to achieve an accuracy score of **75.79%**.
  
#### Qualitative Results
- The model performs well on clear images with high contrast between the license plate and the background.
- Challenges remain with angled, low-quality, or blurry images where the model struggles to detect and recognize the characters accurately.


