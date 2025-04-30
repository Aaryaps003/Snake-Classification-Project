## 📌 Project Overview
A deep learning solution for classifying snake images as **venomous** or **non-venomous** using EfficientNet-B0 with:
- **Test-Time Augmentation (TTA)** for robust predictions
- **GUI interface** for user-friendly interaction
- **Speech recognition** for voice commands
- **Audio alerts** for dangerous species

## 📂 Dataset
| Category          | Samples | Image Size | Format |
|-------------------|---------|------------|--------|
| Venomous          | X,XXX   | 224×224    | JPEG   |
| Non-Venomous      | X,XXX   | 224×224    | PNG    |

> 🔍 **Dataset Notes**:
> - Curated from : datasets

## ⚙️ Installation
### Prerequisites
- NVIDIA GPU (recommended) with CUDA 12.1 and cuDNN 8.9
- Python 3.8+

### Setup
git clone https://github.com/Aaryaps003/Snake-Classification-Project.git
cd Snake-Classification-Project

# Create environment (conda recommended)
conda create -n snake python=3.8
conda activate snake

# Install dependencies
pip install -r requirements.txt  # Includes:
# tensorflow==2.12.0
# opencv-python
# pyttsx3==2.90
# SpeechRecognition==3.8.1

🧠 Model Architecture
EfficientNet-B0 Pipeline
1.Input: 224×224 RGB images
2.Preprocessing: img = tf.keras.applications.efficientnet.preprocess_input(img)
3.Base Model: base_model = EfficientNetB0(weights='imagenet', include_top=False)
4.Custom Head: x = GlobalAveragePooling2D()(base_model.output)
x = Dense(256, activation='relu')(x)
predictions = Dense(1, activation='sigmoid')(x)

Test-Time Augmentation
5-crop ensemble with:
Horizontal flips
±15° rotations
Brightness adjustments

🚀 Usage
Command Line: python predict.py --image path/to/image.jpg --tta True

GUI Features
Real-time prediction visualization
Confidence score display
Voice command support
Danger alerts (visual + audio)

API Example
from model import SnakeClassifier

classifier = SnakeClassifier()
result = classifier.predict(
    image_path="snake.jpg",
    apply_tta=True,
    verbose=True
)

📊 Performance Metrics
Metric	Score	Improvement
Accuracy	91.10%	+4.2% with TTA
Precision	0.94	
Recall	0.95	
Inference Speed	86ms	(RTX 3060)

Confusion Matrix:
                Predicted
Actual     Non-Venomous  Venomous
Non-Venomous     94        15
Venomous          7       120

🛠️ Libraries Used
Library	Version	Purpose
TensorFlow	2.12.0	Model training/inference
OpenCV	4.7.0	Image processing
PyQt5	5.15.7	GUI interface
pyttsx3	2.90	Audio alerts

🚧 Roadmap
Mobile app deployment
Live camera integration
Multi-species classification
Habitat analysis module

⚠️ Safety Notice: Always consult professional herpetologists for real-world snake encounters. This tool provides preliminary identification only.


