<div align="center">

# Emotion Detector

Real-time face emotion detection using **OpenCV** and **DeepFace**

[![Python](https://img.shields.io/badge/Python-3.6%2B-blue?style=flat&logo=python)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?style=flat&logo=opencv)](https://opencv.org/)
[![DeepFace](https://img.shields.io/badge/DeepFace-Latest-orange)](https://github.com/serengil/deepface)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## Overview

Emotion Detector captures video from your webcam, detects faces in real-time, and analyzes the dominant emotion for each face using a deep learning model. It displays bounding boxes with emotion labels directly on the video feed.

## Demo

```
┌──────────────────────────────────┐
│  ┌──────────┐                    │
│  │  Happy   │  ┌──────────┐      │
│  │  ┌──┐    │  │  Neutral │      │
│  │  │  │    │  │  ┌──┐    │      │
│  │  └──┘    │  │  └──┘    │      │
│  └──────────┘  └──────────┘      │
│     Emotion Detection             │
└──────────────────────────────────┘
```

## Features

- **Real-time face detection** using Haar Cascade classifier
- **Emotion analysis** powered by DeepFace deep learning model
- **Multi-face support** — detects and analyzes all faces in frame
- **Performance optimized** — frame skipping reduces computation
- **Live overlay** — bounding boxes with emotion labels

## Supported Emotions

| Emotion | Description |
|---------|-------------|
| 😠 Angry | Signs of anger or frustration |
| 🤢 Disgust | Signs of disgust or aversion |
| 😨 Fear | Signs of fear or anxiety |
| 😊 Happy | Signs of happiness or joy |
| 😐 Neutral | Calm or neutral expression |
| 😢 Sad | Signs of sadness or sorrow |
| 😲 Surprise | Signs of surprise or shock |

## Requirements

- Python **3.6** or higher
- A working **webcam**

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/emotion-detector.git
   cd emotion-detector
   ```

2. **Install dependencies**

   ```bash
   pip install opencv-python deepface
   ```

   > DeepFace automatically downloads the required model weights on first run.

## Usage

```bash
python emotion_detector.py
```

- Press **`q`** to quit the application
- Press **`Ctrl + C`** in terminal to force exit

### What to expect

1. A window titled "Emotion Detection" will open showing your webcam feed
2. Faces are highlighted with green bounding boxes
3. The predicted emotion appears above each face
4. During analysis, you may see "Analyzing..." or "Processing..." briefly

## How It Works

```
Webcam Frame
     │
     ▼
Convert to Grayscale
     │
     ▼
Face Detection (Haar Cascade)
     │
     ▼
┌─────────────────────────────┐
│  Every 10 frames:           │
│  Run DeepFace emotion       │
│  analysis on each face      │
└─────────────────────────────┘
     │
     ▼
Draw bounding boxes + labels
     │
     ▼
Display frame
```

- **Face Detection**: OpenCV's Haar cascade (`haarcascade_frontalface_default.xml`) detects faces in grayscale frames.
- **Emotion Analysis**: DeepFace analyzes the face region to predict one of 7 emotions.
- **Frame Skipping**: Analysis runs every 10 frames to keep the application responsive.
- **Emotion Persistence**: Detected emotions remain displayed until the next analysis cycle.

## Project Structure

```
emotion-detector/
├── emotion_detector.py   # Main application script
├── .gitattributes        # Git LFS/text settings
├── .vscode/              # VS Code settings
└── README.md             # This file
```

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Webcam not opening | Check if another app is using the camera |
| No faces detected | Ensure adequate lighting and face visibility |
| Slow performance | Reduce `frame_skip` value or use a faster detector backend |
| DeepFace model download fails | Check internet connection and retry |

## Customization

You can tweak these parameters in `emotion_detector.py`:

| Variable | Default | Description |
|----------|---------|-------------|
| `frame_skip` | `10` | Process emotion every N frames |
| `minSize` | `(100, 100)` | Minimum face size for detection |
| `scaleFactor` | `1.1` | Scale factor for cascade detector |
| `detector_backend` | `'opencv'` | DeepFace detector backend |

## License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

<div align="center">
Made with ❤️ using OpenCV & DeepFace
</div>
