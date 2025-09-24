Skin Lesion Classification with CNN

Overview

This project explores automated skin lesion classification using the HAM10000 augmented dataset. A compact ResNet-style Convolutional Neural Network is implemented to classify dermatoscopic images into seven diagnostic categories. The study focuses on handling class imbalance and evaluating performance with metrics beyond accuracy, including precision, recall, and macro F1.

Dataset

HAM10000 augmented dataset: 39,500 dermatoscopic images with additional augmentation to address class imbalance.
Classes: melanocytic nevi (nv), melanoma (mel), benign keratosis-like lesions (bkl), actinic keratoses (akiec), basal cell carcinoma (bcc), dermatofibroma (df), vascular lesions (vasc). All images resized to 160×160.
Data split into training, validation, and test sets.

Model Architecture

Initial 3×3 convolution (32 filters) + BatchNorm + ReLU
Four residual stages with channel sizes: 32 → 64 → 128 → 256
Each stage consists of two BasicBlocks with skip connections
Global Average Pooling → Dropout (0.25) → Fully connected layer (7 outputs)
Total parameters: ~1.3M

Training Setup

Optimizer: Adam
Loss function: CrossEntropy
Batch size: 64
Early stopping on validation loss
Evaluation metrics: Accuracy, Precision, Recall, Macro F1

Results

Overall accuracy: ~80.4% on the test set
High precision and recall for vascular lesions and dermatofibroma
Melanoma and akiec show higher recall than precision (sensitive but prone to false positives)
Benign keratosis-like lesions show the opposite trend (precise but low recall)
Macro F1 highlights that performance is strong on frequent classes but weaker on rare ones
