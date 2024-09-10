# Face Recognition Using Python

## Overview
This project uses Python with the `face_recognition` and `OpenCV` libraries to implement a basic face recognition system. The program detects faces from a webcam feed, compares them with a set of pre-encoded faces, and identifies them with a confidence score.

## Requirements
To run this project, you will need the following Python packages:
- `face_recognition`
- `opencv-python`

You should also have a folder named `faces`, where you store the reference images for face encoding.

## Key Functions and Classes

### `face_confidence()`

This function calculates the confidence score for a match. It uses the distance between the detected face and the known face encodings to calculate a percentage that reflects how confident the system is that the faces match. If the distance exceeds the threshold, it returns a lower confidence score.

**Parameters:**
- `face_distance`: The distance between the known face encoding and the detected face encoding.
- `face_match_threshold`: The threshold that determines what is considered a match.

### `FaceRecognition` Class

This class manages the face recognition process, including encoding faces from reference images and running the recognition on live video frames.

**Attributes:**
- `face_locations`: Holds the locations of detected faces in the video frame.
- `face_encodings`: Holds the encodings for detected faces in the current frame.
- `face_names`: Holds the recognized names of faces in the current frame.
- `known_face_encodings`: Holds the face encodings for the known faces loaded from reference images.
- `known_face_names`: Holds the names corresponding to the known face encodings.
- `process_current_frame`: Used to toggle frame processing for better performance.

**Methods:**

- `encode_faces(self)`:  
  This method reads all images from the `faces` directory and encodes them using the `face_recognition` library. Each face encoding is stored in `self.known_face_encodings` along with the corresponding name in `self.known_face_names`.

- `run_recognition(self)`:  
  This is the main loop of the program. It captures video from the webcam, detects faces in the video, compares them with known face encodings, and draws rectangles and labels around recognized faces.

## Running the Program

1. **Prepare the faces directory:**
   Create a folder named `faces` in the project directory. Place images of faces that you want to recognize in this folder. Ensure that the file names are descriptive (e.g., `john.jpg`), as the file name will be used as the label for the face.

2. **Run the script:**
   Execute the script. It will start the webcam, and the face recognition process will begin.

3. **Quit the program:**
   To quit the face recognition program, press the `q` key.

## Notes

- **Performance:** To improve performance, the system only processes every other frame, which reduces computational load.
- **Confidence Scores:** The confidence score is calculated based on the distance between the detected face and the known face encodings. A higher confidence score indicates a closer match.
- **Face Encodings:** This implementation uses pre-encoded faces from images stored in the `faces` directory. For each image, the first face it detects will be encoded.

## License
This project is licensed under the MIT License.