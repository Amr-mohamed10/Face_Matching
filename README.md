# Face Recognition

This repository contains a Python script that compares two images and determines if they contain the same face using face recognition techniques. It utilizes the `opencv-python` and `face-recognition` libraries.

## Installation

To run the script, you need to install the following dependencies:
!pip install opencv-python
!pip install face-recognition

## Usage
 Upload Image Files:
  If you are using Google Colab, you can upload your image files by running the following code
  Make sure to upload the images you want to compare.

## Results:
The script will compare the faces in the provided images and display the results:

-If the faces are the same, it will print "The images are the same" along with the accuracy level.
-If the faces are not the same, it will print "The images are not the same."
-If face encodings cannot be extracted from one or both images, it will print "Failed to extract face encodings from one or both images."

