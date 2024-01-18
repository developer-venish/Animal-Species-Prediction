# Animal-Species-Prediction
---------------------------------------------------------------------------------------
![](https://github.com/developer-venish/Animal-Species-Prediction/blob/main/e.png)
---------------------------------------------------------------------------------------
![](https://github.com/developer-venish/Animal-Species-Prediction/blob/main/2.png)

---------------------------------------------------------------------------------------
This code is a Python script using the TensorFlow and OpenCV libraries to perform real-time image classification on video frames using a pre-trained neural network model. 
Here's an overview of the code:

1. **Import Libraries:**
   - `tensorflow.keras`: TensorFlow's high-level neural networks API.
   - `cv2`: OpenCV library for computer vision tasks.
   - `numpy`: Library for numerical operations in Python.

2. **Load Pre-trained Model:**
   - `load_model("simple_animal_classification_model.h5")`: Loads a pre-trained neural network model from the specified file ("simple_animal_classification_model.h5").

3. **Capture Video:**
   - `cv2.VideoCapture("https://192.0.0.4:8080/video")`: If provided, captures video from a specified IP camera address. Note: The provided URL seems incomplete.
   - `cv2.VideoCapture(0)`: If the camera IP address is not specified, it captures video directly from the webcam (camera index 0).

4. **Define Classes:**
   - `all_classes`: A dictionary mapping class names to their corresponding numerical labels. The labels are used in the output of the neural network.

5. **Define Function to Get Key from Value:**
   - `get_key(val)`: A function that returns the key (class name) for a given value (class label) from the `all_classes` dictionary.

6. **Main Loop for Real-time Video Processing:**
   - The script enters a loop (`while(True)`) to continuously process video frames.
   - `cap.read()`: Reads a video frame from the capture object (`cap`).
   - The code checks if the frame is not `None` and proceeds to process it.
   - The frame is resized to (32, 32) and converted to grayscale.
   - The processed image is then expanded to 4 dimensions to match the input format expected by the model.
   - `model.predict(test_image)`: The pre-trained model predicts the class probabilities for the given frame.
   - The class with the highest probability is identified, and its corresponding class name is obtained using `get_key`.
   - The class name is displayed on the video frame using `cv2.putText`.
   - The processed frame is then displayed.

7. **Exit Condition:**
   - If the 'q' key is pressed (`cv2.waitKey(1) & 0xFF == ord('q')`), the script breaks out of the loop.

8. **Release Resources:**
   - After exiting the loop, the capture object is released (`cap.release()`), and all OpenCV windows are destroyed (`cv2.destroyAllWindows()`).

Note: Ensure that the necessary Python libraries and the pre-trained model file ("simple_animal_classification_model.h5") are available before running this script. Also, the script assumes a valid video source, either an IP camera or a webcam.
