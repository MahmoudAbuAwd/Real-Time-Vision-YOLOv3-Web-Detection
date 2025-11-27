# Real-Time Vision YOLOv3 Web Detection

A powerful real-time object detection application using YOLOv3 (You Only Look Once) with OpenCV. This project detects objects from a webcam feed in real-time and displays the results with bounding boxes and confidence scores.

⚠️ **IMPORTANT:** The `yolov3.weights` file (~250MB) is **NOT** included in this repository. You must download it separately before running the application. See **Step 4** in Quick Start.

## 🎯 Features
- **Real-time object detection** using YOLOv3
- **Webcam integration** for live video stream processing
- **80+ object classes** detection (COCO dataset)
- **Confidence thresholding** for filtering low-confidence detections
- **Non-max suppression** for handling overlapping detections
- **GPU support** (optional, requires CUDA-enabled OpenCV)

## 📋 Prerequisites
- **Python 3.8+** (see `.python-version`)
- **pip** (Python package manager)
- **Webcam** (for real-time detection)
- **4GB+ RAM** (recommended)
- **Disk space**: ~250MB for YOLOv3 weights

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/MahmoudAbuAwd/Real-Time-Vision-YOLOv3-Web-Detection.git
cd Real-Time-Vision-YOLOv3-Web-Detection
```

### 2. Create a Virtual Environment (Recommended)
```bash
# Windows
python -m venv venv
.\venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Download YOLOv3 Weights ⚠️ REQUIRED

The `yolov3.weights` file is **required** but **NOT** included in this repository due to its large file size (~250MB).

**Download steps:**
1. Download the weights file here: [YOLOv3 Weights](https://pjreddie.com/media/files/yolov3.weights) (File size: ~250MB)
2. Save it to your project folder:
   ```
   config/yolov3.weights
   ```
3. Verify the file exists:
   ```bash
   # Windows
   dir config\yolov3.weights
   
   # macOS/Linux
   ls -lh config/yolov3.weights
   ```
   You should see the file size is approximately 250MB.

### 5. Run the Application
```bash
python main.py
```

## 📁 Project Structure
```
Real-Time-Vision-YOLOv3-Web-Detection/
├── main.py                  # Main application script
├── requirements.txt         # Python dependencies
├── README.md               # This file
├── .gitignore              # Git ignore file
├── .python-version         # Python version specification
├── config/
│   ├── yolov3.cfg         # YOLOv3 network architecture
│   └── yolov3.weights     # ⚠️ DOWNLOAD REQUIRED (~250MB) - See Step 4
└── data/
    └── coco.names         # Object class names (80 classes)
```

**⚠️ Note:** `yolov3.weights` is NOT included in the repository. You must download it in Step 4 above.

## ⚙️ Configuration

The main configuration options in `main.py`:

```python
CONFIDENCE_THRESHOLD = 0.5  # Detections with confidence < 0.5 will be filtered
NMS_THRESHOLD = 0.4         # Overlapping boxes with IOU > 0.4 will be merged
```

**To adjust:**
1. Open `main.py`
2. Modify the threshold values
3. Save and re-run

Lower thresholds = more detections (more false positives)
Higher thresholds = fewer detections (fewer false positives)

## 🐛 Troubleshooting

### Error: "Failed to parse NetParameter file: yolov3.weights"
**Cause:** YOLOv3 weights file is missing or not in the correct location

**Solution:**
1. Download `yolov3.weights` from the link above
2. Place it in `config/yolov3.weights`
3. Verify the path in `main.py` is correct

### Error: "Cannot open camera"
**Cause:** Webcam is not available or not connected

**Solution:**
1. Check if your webcam is properly connected
2. Try changing the camera index: `cap = cv2.VideoCapture(1)` instead of `0`

### Slow Performance
**Solutions:**
1. Lower the input frame resolution
2. Increase confidence threshold
3. Enable GPU acceleration (requires CUDA support)
4. Reduce the frequency of object detection (process every 2nd or 3rd frame)

## 🔌 GPU Acceleration (Optional)

To use GPU acceleration with CUDA:

1. Install CUDA-enabled OpenCV:
   ```bash
   pip install opencv-python-headless opencv-contrib-python
   ```

2. Uncomment GPU lines in `main.py`:
   ```python
   net.setPreferableBackend(cv2.dnn.DNN_BACKEND_CUDA)
   net.setPreferableTarget(cv2.dnn.DNN_TARGET_CUDA)
   ```

## 📊 Detectable Objects (COCO Dataset)
The model can detect 80 different object classes including:
- People, animals, vehicles, furniture, and more
- See `data/coco.names` for the complete list

## 📝 License
MIT License - See LICENSE file for details

## 🤝 Contributing
Contributions are welcome! Please feel free to submit pull requests or open issues.

## 👨‍💻 Author
[MahmoudAbuAwd](https://github.com/MahmoudAbuAwd)

## 📚 Resources
- [YOLOv3 Official Website](https://pjreddie.com/darknet/yolo/)
- [OpenCV Documentation](https://docs.opencv.org/)
- [COCO Dataset](https://cocodataset.org/)
