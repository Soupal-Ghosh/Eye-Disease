DATA SET LINK :
https://drive.google.com/drive/folders/1GiNX_xvw2u6CHnzWWon5C4CGwma53LN3?usp=drive_link
(CONTAINS DATASET + TRAIN+ TEST+ VALIDATION NUMPY ARRAYS )
🧠 Overview

This project uses transfer learning with a pre-trained ResNet50 model (ImageNet weights) for detecting and classifying eye diseases from medical eye images. The classification is performed into 4 classes, typically including conditions such as:

    Cataracts

    Diabetic Retinopathy

    Glaucoma

    Normal

🧬 Model Architecture
🔧 Base Model

    ResNet50 (pre-trained on ImageNet)

    include_top=False to remove original classification head

    Input size: 224x224x3

    Last 100 layers are unfrozen for fine-tuning

🧱 Custom Head

GlobalAveragePooling2D
Dense(256, ReLU, L2=0.001) + BatchNormalization + Dropout(0.4)
Dense(128, ReLU, L2=0.001) + BatchNormalization + Dropout(0.3)
Dense(32, ReLU, L2=0.001) + BatchNormalization
Dense(16, ReLU, L2=0.001)
Dense(4, Softmax)  # 4-class output

🏋️‍♂️ Training Details

    Optimizer: Adam

    Loss Function: Categorical Crossentropy

    Metrics: Accuracy

    Regularization: L2 (weight decay) on Dense layers

    Dropout: 0.3–0.4 to prevent overfitting

    Batch Normalization used after dense layers

    Epochs: 20–50 (adjustable)

<img width="649" height="547" alt="Untitled" src="https://github.com/user-attachments/assets/029824dc-40ea-47e4-9d56-09b5d55b6c66" />
