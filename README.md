# Korean License Plate Recognition

**Faster R-CNN + EasyOCR**

A simple two-stage framework for recognizing **Korean license plates** from car images.

## Project Summary

This project detects Korean license plates and reads their characters using a two-step pipeline:

1. **Object Detection (OD)**: Locate license plates in car images
2. **Optical Character Recognition (OCR)**: Read characters from cropped plates

## Pipeline

```
Input Image
   ↓
Faster R-CNN (Plate Detection)
   ↓
Cropped Plate
   ↓
EasyOCR (Text Recognition)
   ↓
License Plate Number
```

## Models

- **Object Detection**: Faster R-CNN (ResNet-50, pretrained on COCO)
- **OCR**: EasyOCR (CRAFT + CRNN)

## Dataset

- **OD**: Kaggle Car License Plate Detection Dataset (433 images)
- **OCR**: AI Hub Korean License Plate Dataset (≈62k images after preprocessing)
- **End-to-End Test**: 107 real-world car images collected by team members

## Results

- **Faster R-CNN**
  - Mean IoU: **0.72**
- **EasyOCR**
  - Character accuracy: **87.60%**
- **End-to-End System**
  - Correctly recognized **87 / 107** license plates
  - Character accuracy: **97.55%**

## Key Challenges

- Lack of Korean license plate datasets with bounding boxes

  - Used separate datasets for OD and OCR
  - OD: Kaggle license plate detection dataset (including car plate images from other countries)
  - OCR: AI Hub Korean license plate dataset with large-scale character annotations

- Large variation in lighting, plate design, and image quality

  - Applied preprocessing (grayscale conversion, resizing, sharpening) before OCR

  - Example: `361머2301.png`

  - ![Preprocessing Example](361머2301_preprocessed.png)

    

    - After preprocessing and OCR inference, the recognized license plate characters are:

      ```
      ['3', '6', '1', '머', '2', '3', '0', '1']
      ```

- Limited computational resources for training OCR models

  - Focused on system-level performance evaluation and tuning rather than full model training

- Irrelevant Text Detection Outside License Plates

  - Applied object detection first to tightly crop license plate regions

## Applications

- Intelligent Transportation Systems (ITS)
- Traffic monitoring and analysis
- Parking management systems
- Urban planning

## Team

- Yeongjun Go
- Minseo Kim
- Hyunsoo Kim
- **Saehee Eom**

Department of Interdisciplinary Major in AI
 Seoul National University

## Contribution

- OCR model evaluation and integration (EasyOCR)
- Object detection model evaluation (Faster R-CNN)
