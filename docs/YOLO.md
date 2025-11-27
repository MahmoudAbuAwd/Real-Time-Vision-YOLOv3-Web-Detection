# YOLO (You Only Look Once) - Overview

## What is YOLO?

YOLO is a real-time object detection system that frames object detection as a single regression problem. Unlike traditional methods that use classifiers to perform detection, YOLO can predict multiple bounding boxes and class probabilities in a single evaluation of the network.

## Key Features

- **Real-time Processing**: YOLO processes images at 30+ FPS on standard GPUs
- **End-to-end Learning**: The entire detection pipeline is trained end-to-end
- **Generalizable**: YOLO learns generalizable representations of objects, making it excellent for cross-domain applications
- **Global Context**: YOLO sees the entire image during training and test time, so it encodes contextual information about classes and their appearance

## How YOLO Works

1. **Single Neural Network**: Divides the image into a grid
2. **Grid Prediction**: Each grid cell predicts:
   - Bounding boxes (x, y, width, height)
   - Confidence scores
   - Class probabilities
3. **Non-Maximum Suppression (NMS)**: Removes duplicate detections and keeps the best ones

## YOLOv3 Architecture

YOLOv3 (the version used in this project) improvements include:

- **Multi-scale Predictions**: Detects objects at different scales using multiple layers
- **Darknet-53 Backbone**: More powerful feature extraction network
- **More Accurate**: Improved accuracy while maintaining speed
- **Detects 80 COCO Classes**: Can identify 80 different object types

## COCO Dataset Classes

The model is trained on the COCO (Common Objects in Context) dataset, which includes 80 object classes:

### People & Animals
- Person, bicycle, dog, cat, bird, horse, sheep, cow, elephant, bear, zebra, giraffe

### Vehicles
- Car, motorcycle, airplane, bus, train, truck, boat

### Furniture & Household Items
- Bench, chair, couch, table, laptop, mouse, keyboard, microwave, oven, etc.

### Sports & Recreation
- Baseball, basketball, frisbee, skateboard, tennis racket, etc.

And many more! See `data/coco.names` for the complete list of 80 classes.

## Detection Pipeline

```
Input Image
    ↓
Resize to 416x416
    ↓
Forward pass through YOLOv3
    ↓
Generate predictions for 3 scales
    ↓
Apply Non-Maximum Suppression (NMS)
    ↓
Filter by confidence threshold
    ↓
Output: Bounding boxes + Class labels + Confidence scores
```

## Performance Metrics

- **mAP (mean Average Precision)**: 57.9% on COCO test-dev
- **Speed**: ~51 ms per image on Titan X GPU
- **FPS (Frames Per Second)**: ~20 FPS on typical hardware

## Advantages of YOLOv3

✅ Fast and real-time capable  
✅ Can detect multiple objects in a single image  
✅ Good at generalizing to new domains  
✅ Lower false positive rate compared to other methods  
✅ Robust performance across different scales  

## Limitations

❌ Struggles with very small objects  
❌ Sensitive to object aspect ratio changes  
❌ Requires specific input size (416x416)  
❌ Large model size (~250MB weights)  

## Resources

- [YOLOv3 Official Paper](https://arxiv.org/abs/1804.02767)
- [Darknet GitHub Repository](https://github.com/pjreddie/darknet)
- [COCO Dataset](https://cocodataset.org/)
- [YOLOv3 Official Website](https://pjreddie.com/darknet/yolo/)

## References

Redmon, J., & Farhadi, A. (2018). YOLOv3: An Incremental Improvement. arXiv preprint arXiv:1804.02767.
