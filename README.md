# Face Recognition

This repository contains a Python script that compares two images and determines if they contain the same face using face recognition techniques. It utilizes the `opencv-python` and `face-recognition` libraries.

## Installation

To run the script, you need to install the following dependencies:

```shell
!pip install opencv-python
!pip install face-recognition
```
## Usage

1. **Upload Image Files:**

   - If you are using Google Colab, you can upload your image files by running the following code:

     ```python
     from google.colab import files

     # Upload image files
     uploaded = files.upload()

     # Access the uploaded files
     for filename, file_content in uploaded.items():
         # Save the file
         with open(filename, 'wb') as f:
             f.write(file_content)
         print(f"File '{filename}' uploaded successfully.")
     ```

   - Make sure to upload the images you want to compare.

2. **Run the Script:**

   - After uploading the image files, you can run the script by executing the following code:

     ```python
     import cv2
     import face_recognition

     def find_face_encodings(image_path):
         # Read the image
         image = cv2.imread(image_path)

         # Get face encodings from the image
         face_encodings = face_recognition.face_encodings(image)

         # Return the face encodings
         return face_encodings[0] if face_encodings else None

     # getting face encodings for the first image
     image_1 = find_face_encodings("Image1.jpg")
     # getting face encodings for the second image
     image_2  = find_face_encodings("Image2.jpg")

     if image_1 is not None and image_2 is not None:
         # Compare the faces
         is_same = face_recognition.compare_faces([image_1], image_2)[0]

         if is_same:
             # Calculate the distance between the faces
             distance = face_recognition.face_distance([image_1], image_2)
             distance = round(distance[0] * 100)

             # Calculate the accuracy level
             accuracy = 100 - distance

             print("The images are the same.")
             print(f"Accuracy Level: {accuracy:.2f}%")
         else:
             print("The images are not the same.")
     else:
         print("Failed to extract face encodings from one or both images.")
     ```

3. **Results:**

   - The script will compare the faces in the provided images and display the result:
     - If the faces are the same, it will print "The images are the same" along with the accuracy level.
     - If the faces are not the same, it will print "The images are not the same."
     - If face encodings cannot be extracted from one or both images, it will print "Failed to extract face encodings from one or both images."

**Note:** Make sure to replace `"Image1.jpg"` and `"Image2.jpg"` with the actual filenames of the images you uploaded.
