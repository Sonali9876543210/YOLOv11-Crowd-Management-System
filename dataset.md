# Dataset Description

This project uses two separate datasets to train YOLO11 models for crowd management:

1. Full-Body Person Detection Dataset
2. Human Face Detection Dataset

## 1. Full-Body Person Detection Dataset

**Purpose:** Detect and localize people in images for crowd monitoring and counting.

**Source:** Locally downloaded and annotated dataset.

**Dataset Format:** CVAT XML annotations and PNG images.

### Dataset Structure

```text
person_detection_dataset/
├── annotations.xml
└── boxes/
    ├── frame_000001.PNG
    ├── frame_000002.PNG
    ├── frame_000003.PNG
    └── ...
```

### Dataset Details

* Contains sequential image frames extracted from video.
* Images are stored in PNG format.
* Annotations are provided in CVAT XML format.
* Bounding boxes identify individual people.
* The detection class is `person`.
* XML annotations are converted into YOLO format before training.

### Data Splitting

| Dataset Subset | Percentage |
| -------------- | ---------: |
| Training       |        70% |
| Validation     |        15% |
| Testing        |        15% |

## 2. Human Face Detection Dataset

**Purpose:** Detect human faces in images for face-based crowd estimation.

**Source:** [Kaggle – Human Faces Object Detection](https://www.kaggle.com/datasets/sbaghbidi/human-faces-object-detection)

**Dataset Format:** Images with CSV-based bounding-box annotations.

### Dataset Details

* Contains images of human faces.
* Face locations are represented using bounding boxes.
* Annotations are provided in `faces.csv`.
* CSV annotations are converted into YOLO format.
* The detection class is `person` in the training configuration, although the annotated objects are faces.

### Annotation Fields

| Field        | Description               |
| ------------ | ------------------------- |
| `image_name` | Image filename            |
| `width`      | Image width               |
| `height`     | Image height              |
| `x0`         | Top-left X coordinate     |
| `y0`         | Top-left Y coordinate     |
| `x1`         | Bottom-right X coordinate |
| `y1`         | Bottom-right Y coordinate |

### Data Splitting

| Dataset Subset | Percentage |
| -------------- | ---------: |
| Training       |        80% |
| Validation     |        10% |
| Testing        |        10% |

## Important Notes

* Both datasets are processed separately.
* Annotations are converted into YOLO-compatible format before model training.
* The first dataset focuses on full-body person detection.
* The second dataset focuses on human face detection.
* Face detection may not count people whose faces are occluded or not visible.
* Dataset files and trained model weights may be excluded from GitHub because of their size.

## Applications

These datasets support the development of a YOLO11-based crowd management system for:

* Person detection.
* Face detection.
* Crowd estimation.
* Crowd monitoring.
* Visual analysis of crowded environments.
