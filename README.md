# Weapon-Detection-System
# Overview
The Weapon Detection System is an AI-powered prototype designed to enhance security by detecting handguns in real-time. By leveraging libraries like OpenCV, Imutils, and NumPy, this project identifies guns in images or video streams using Haar cascade classifiers
#Objective
The primary goal of this project is to improve security systems by enabling the detection of firearms through video cameras. Although currently limited to handguns, the project aims to expand its capabilities to detect various types of weapons in diverse environments.
# Features
Real-time handgun detection using a webca
Background subtraction and object classification with Haar cascades.
Integration with Python libraries for image processing and machine learning.
# Scope and Applications
# Scope
Enhanced security for homes, offices, and public space
Potential integration into security camera systems for real-time monitoring
# Applications
Home security systems.
Bank and office surveillance.
Public safety in crowded areas.
# Libraries and Tools
OpenCV (cv2): Used for computer vision tasks such as object detection and background subtraction.
NumPy: Facilitates numerical computations for image processing.
Imutils: Assists with image resizing and rotation.
Datetime: Adds timestamps to frames.
# Programming Language and IDE
Language: Python
IDE: PyCharm and IDLE Python 3.11 (64-bit)

# Dataset
The project uses a Haar cascade XML file for training and detecting objects. The cascade function is trained using numerous positive and negative images, allowing the system to identify handguns effectively.
 # Installation
 To set up the environment, follow these steps:
 1. Install Python 3.11.
 2. Install the required libraries:
    pip install opencv-python imutils numpy
# How It Works
1. The system captures frames from a video stream
2. Each frame is processed to identify potential firearms using Haar cascades.
3. Detected objects are marked with bounding boxes.
4. A timestamp is displayed on each frame.
5. Results are logged, indicating whether a firearm was detected.


# Code Example

import numpy as np
import cv2
import imutils
import datetime

gun_cascade = cv2.CascadeClassifier('cascade.xml')
camera = cv2.VideoCapture(0)

while True:
    ret, frame = camera.read()
    frame = imutils.resize(frame, width=500)
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    gun = gun_cascade.detectMultiScale(gray, 1.3, 5, minSize=(100, 100))

    for (x, y, w, h) in gun:
        frame = cv2.rectangle(frame, (x, y), (x + w, y + h), (255, 0, 0), 2)

    cv2.putText(frame, datetime.datetime.now().strftime("%A %d %B %Y %I:%M:%S %p"),
                (10, frame.shape[0] - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.35, (0, 0, 255), 1)

    cv2.imshow("Weapon Detection Cam", frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

camera.release()
cv2.destroyAllWindows()



# Conclusion
The Weapon Detection System is a significant step toward smarter security solutions. With further development, it can serve as a robust tool for public and private safety.






