This Python script performs human activity recognition (HAR) using a combination of preprocessing, dimensionality reduction, data augmentation, and deep learning techniques. It utilizes the UCI HAR dataset, containing time-series data from accelerometers and gyroscopes.

Key Steps in the Code
1. Data Loading, Preprocessing, and Noise Filtering
Data Loading: The train.csv and test.csv datasets are loaded, with features and labels extracted.
Label Encoding: Activity labels are encoded into numerical values using LabelEncoder.
Noise Filtering: A Butterworth filter is applied to smooth and filter noise in the time-series data.
2. Dimensionality Reduction Using Autoencoder
Autoencoder Design: A neural network is trained to compress the data into a lower-dimensional representation and reconstruct it.
Encoder: Reduces features to 125 dimensions.
Decoder: Reconstructs data from the compressed representation.
Training: The autoencoder is trained on the filtered training data, and only the encoder is used to obtain reduced features.
3. Data Augmentation Using GAN
Objective: Generate synthetic data for the "Standing" activity class to balance the dataset.
GAN Architecture:
Generator: Creates synthetic samples from noise.
Discriminator: Distinguishes real samples from synthetic ones.
Training: The generator and discriminator are trained iteratively to improve synthetic data quality.
Synthetic Data: 500 synthetic samples are generated and labeled as "Standing."
4. Data Augmentation
The synthetic samples are added to the training dataset, increasing its diversity.
5. Classification Using CNN-Transformer Hybrid
CNN for Feature Extraction: A 1D convolutional layer captures local patterns in the time-series data.
Transformer for Contextual Understanding: Multi-head attention layers learn dependencies across the time-series data.
Fully Connected Layers: Classify the activities into their respective categories.
Model Training: The model is trained on the augmented dataset, with early stopping to prevent overfitting.
6. Evaluation
Performance Metrics: The model's performance is evaluated using accuracy, precision, recall, and F1 score.
Confusion Matrix: Visualizes classification results across activity classes.
Outputs
Metrics: Prints classification accuracy, precision, recall, and F1 score.
Confusion Matrix: A visual representation of the model's predictions versus true labels.
