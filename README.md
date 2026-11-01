# YOLOv11-Based Crowd Management System

This repository contains two Jupyter notebooks exploring YOLO11-based detection and tracking for crowd-monitoring use cases.

## Projects

### 1. Person detection and tracking
**Notebook:** `Crowd_Management_YOLO_Training.ipynb`

Uses a locally supplied dataset archive with images and CVAT XML annotations. The notebook processes annotations into YOLO format, trains a YOLO11 model, runs inference, and explores tracking/crowd counting.

### 2. Face detection and tracking
**Notebook:** `Crowd_Management_Human_Faces_YOLO_Complete.ipynb`

Downloads the Kaggle dataset `sbaghbidi/human-faces-object-detection` using KaggleHub, processes face annotations, and trains a face-detection model. Because it detects faces rather than full bodies, it may miss people whose faces are not visible.

## Technologies
- Python and Jupyter Notebook
- Ultralytics YOLO11n
- OpenCV
- Pandas
- KaggleHub
- ByteTrack (where configured in the notebook)
- Matplotlib

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
├── Crowd_Management_YOLO_Training.ipynb
├── Crowd_Management_Human_Faces_YOLO_Complete.ipynb
├── datasets..md
├── outputs/
│   ├── crowd_detection/
│   └── face_detection/
```

## Setup

Use Python in a virtual environment where possible:

```bash
python -m venv .venv
```

Activate it, then install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebooks in Jupyter or upload them to Google Colab. Follow each notebook's cells in order and update dataset paths if your local directory differs.

## Dataset notes

- The person-detection dataset archive included in this downloadable package is for local experimentation. Before publishing this dataset or its contents, check the original source's license and redistribution terms.
- The face-detection notebook downloads `sbaghbidi/human-faces-object-detection` using KaggleHub. Kaggle access/authentication may be required.
- The dataset files are intentionally excluded from Git tracking by `.gitignore`. Do not commit large datasets or credentials to a public repository.

## Results
```markdown
![Person detection result](outputs/crowd_detection)
![Face detection result](outputs/face_detection)
```

Only report precision, recall, mAP, FPS, counting error, or deployment performance when you have verified the measurements from your own runs.

## Jetson Orin Nano

The notebooks explore deployment-related steps. Treat deployment as planned/experimental unless you have run and benchmarked the model on the physical Jetson device. Confirm compatibility between the JetPack, CUDA, PyTorch, and Ultralytics versions before installing dependencies on Jetson.

## Limitations
- Detection performance depends on annotation quality and how representative the training data is.
- Face detection is not equivalent to full-person detection.
- Tracking IDs can change when detections are lost or objects are occluded.
- Real-world crowd-counting accuracy should be evaluated on independent videos.

