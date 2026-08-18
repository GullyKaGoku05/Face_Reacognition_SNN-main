# Face Recognition using Siamese Neural Network

**Author: Nikhil Kshirsagar**

A computer vision project implementing **face recognition using a Siamese Neural Network** and one-shot learning. Instead of training a conventional classifier for every person, the system learns a similarity function that compares a captured face with reference images stored in a database.

## Overview

Traditional face classification systems require multiple labeled images for every person and need to be retrained whenever a new person is added. This project addresses that limitation using a **Siamese Neural Network**, where two face images are compared to determine whether they belong to the same person.

The approach is useful for small datasets because a new person's identity can be added using only a **single reference image**, without retraining the complete model.

## Problem Statement

A conventional face classification system requires:

* Multiple training images for every person
* A separate output class for every identity
* Complete retraining when a new person is added
* Additional labeled data as the organization grows

This project instead learns **face similarity rather than direct identity classification**.

```text
Reference Face ───────┐
                      ├──► Siamese Network ──► Similarity Score
Input Face ───────────┘
```

A similarity score closer to **1** indicates greater similarity, while a score closer to **0** indicates that the faces are unlikely to belong to the same person.

## Key Features

* Implemented **Siamese Neural Network** for face verification
* Applied **one-shot learning** with limited examples
* Used a pre-trained **FaceNet/Inception-based feature extraction pipeline**
* Built a webcam-based face recognition system
* Created a local face database for reference images
* Added preprocessing and face extraction before recognition
* Used similarity comparison to identify known faces
* Returns **"Unknown"** when a matching identity is not found

## Dataset

The system supports two methods for creating the face database:

1. **Existing Images** — Add a folder containing images of the person to be recognized.
2. **Webcam Dataset Generation** — Capture approximately **50 face samples** directly using the webcam.

Each image passes through a preprocessing pipeline before being added to the database.

## Working

### 1. Build Face Database

Reference images are stored in an `images` directory. Faces can be added from existing images or captured directly through the webcam.

### 2. Face Preprocessing

The input image is processed to detect and extract the face before feature comparison.

### 3. Feature Extraction

The pre-trained network converts the face image into a numerical feature representation.

### 4. Similarity Comparison

The captured webcam face is compared with reference faces stored in the database.

### 5. Recognition

The identity corresponding to the highest similarity is returned. If no sufficiently similar face is found, the system outputs **Unknown**.

## Project Structure

```text
Face_Reacognition_SNN/
│
├── face functions.py
├── add_to_database.py
├── face_cutter.py
├── face_recogniser.py
├── fr_utils.py
├── inception_network.py
├── weights/
├── haarcascade_frontalface_default.xml
├── requirements.txt
└── README.md
```

### File Description

| File                                  | Purpose                                               |
| ------------------------------------- | ----------------------------------------------------- |
| `face functions.py`                   | Face preprocessing and supporting functions           |
| `add_to_database.py`                  | Captures webcam images and adds faces to the database |
| `face_cutter.py`                      | Detects and extracts faces from images                |
| `face_recogniser.py`                  | Main face recognition application                     |
| `fr_utils.py`                         | Utility functions for the feature extraction network  |
| `inception_network.py`                | Defines Inception network components                  |
| `weights/`                            | Pre-trained network weights                           |
| `haarcascade_frontalface_default.xml` | Haar Cascade face detector                            |

## Technology Stack

**Language:** Python
**Deep Learning:** Siamese Neural Network, FaceNet, Inception Network
**Computer Vision:** OpenCV, Haar Cascade
**Learning Approach:** One-Shot Learning

## Results

The system performs webcam-based face recognition by comparing an input face against stored reference images using learned facial representations and similarity scoring.

## Limitations & Future Improvements

Recognition performance can be affected by image quality, lighting, camera resolution, and face size. Potential improvements include:

* Applying image enhancement and deblurring techniques
* Upsampling low-resolution face images
* Improving face alignment and preprocessing
* Using larger and more diverse reference datasets
* Optimizing inference for real-time deployment

## Conclusion

This project demonstrates how **Siamese Neural Networks and one-shot learning** can be applied to face recognition without requiring a conventional multi-class classifier. By learning similarity between facial representations, the system can recognize newly added identities using only a small number of reference images.

## Author

**Nikhil Kshirsagar**
IIT Bombay
