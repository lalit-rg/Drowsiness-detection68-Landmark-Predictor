# Drowsiness-detection68-Landmark-Predictor
This project aims to detect drowsiness in a person's eyes using facial landmarks and the eye aspect ratio. It utilizes the dlib library for face detection and facial landmark detection, as well as OpenCV for image processing.

Here's an explanation of the code:

1. Importing Libraries:
   - `scipy.spatial.distance`: It provides the `euclidean` function for calculating the Euclidean distance between points.
   - `imutils.face_utils`: It contains various utility functions for working with facial landmarks.
   - `imutils`: It provides convenient functions for resizing and manipulating images.
   - `dlib`: It is a powerful library for various computer vision tasks, including face detection and facial landmark detection.
   - `cv2`: It is the OpenCV library for computer vision and image processing.
   - `winsound`: It is used to play a sound alert.

2. Defining Eye Aspect Ratio Function:
   - `eyeAspectRatio()`: It calculates the eye aspect ratio (EAR) using the Euclidean distances between the eye landmarks.

3. Initializing Variables:
   - `blink`: It keeps track of the number of blinks.
   - `count`: It counts the consecutive frames where the eyes are closed.
   - `earThresh`: It sets the threshold for detecting drowsiness based on the eye aspect ratio.
   - `earFrames`: It determines the number of consecutive frames where the eyes must be closed to trigger a drowsiness alert.
   - `shapePredictor`: It specifies the path to the shape predictor model for facial landmarks.

4. Initializing Video Capture:
   - `cam = cv2.VideoCapture(0)`: It initializes the video capture object to read frames from the camera (device index 0).

5. Eye Detection and Drowsiness Alert Loop:
   - The code enters a loop to continuously read frames from the camera, detect eyes, calculate the eye aspect ratio, and check for drowsiness.
   - `cam.read()`: It reads a frame from the camera.
   - `imutils.resize()`: It resizes the frame for faster processing.
   - `detector(gray, 0)`: It detects faces in the grayscale frame using the dlib frontal face detector.
   - For each detected face, the code extracts the facial landmarks using the shape predictor model.
   - The eye aspect ratio is calculated for both eyes, and the average is obtained.
   - Contours of the eyes are drawn on the frame using `cv2.drawContours()`.
   - If the eye aspect ratio falls below the threshold, it indicates drowsiness. The count is incremented, and if it exceeds the specified number of frames, a drowsiness alert is displayed and a sound is played.
   - If the eye aspect ratio is above the threshold, the count is reset, and the number of blinks is displayed.
   - The frame with annotations is displayed using `cv2.imshow()`.
   - The loop continues until the 'q' key is pressed.

6. Exiting the Program:
   - `cam.release()`: It releases the camera.
   - `cv2.destroyAllWindows()`: It closes all windows.

This project demonstrates a basic implementation of drowsiness detection using eye aspect ratio. It can be further improved by incorporating additional features and techniques, such as facial landmarks tracking and more advanced alert mechanisms.
