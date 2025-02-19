# Object Detection and Tracking (Webcam / External Video)

This project demonstrates a basic motion detection and object tracking system using OpenCV. It captures a video stream, processes the frames to detect motion, and highlights areas of movement with bounding rectangles. The processed video is saved to an output file.

## Features

1. **Real-Time Video Processing**:
   - Captures live video from a webcam or other video source.
   - Detects motion by comparing consecutive video frames.

2. **Motion Detection Pipeline**:
   - Computes the difference between consecutive frames to identify motion.
   - Applies preprocessing techniques (grayscale conversion, Gaussian blur, and thresholding) for noise reduction and clearer motion detection.
   - Identifies moving objects by detecting contours in the preprocessed frames.

3. **Object Tracking**:
   - Draws bounding rectangles around regions of detected motion.
   - Displays a status message indicating motion detection.

4. **Video Output**:
   - Saves the processed video, including bounding boxes and status text, to an AVI file.

## Workflow

### Step 1: Frame Capture
The program uses OpenCV's `VideoCapture` to capture video frames from the default camera. Two consecutive frames are read to calculate differences.

### Step 2: Frame Differencing
The difference between two consecutive frames is computed using `cv2.absdiff`. This highlights regions where movement has occurred.

### Step 3: Preprocessing
The difference image undergoes:
- **Grayscale Conversion**: Converts the image to grayscale for simplicity.
- **Gaussian Blur**: Smoothens the image to reduce noise.
- **Thresholding**: Binarizes the image to separate foreground (motion) from the background.
- **Dilation**: Expands the areas of motion to make them more distinct.

### Step 4: Contour Detection
Contours are detected using `cv2.findContours`, which identifies the boundaries of moving objects. Small contours (noise) are ignored based on a size threshold.

### Step 5: Motion Annotation
For each valid contour:
- A bounding rectangle is drawn around the detected motion region.
- A status message, "Movement," is displayed on the frame.

### Step 6: Output
The processed frames are resized and saved to an AVI file using OpenCV's `VideoWriter`. The frames are also displayed in a live window.

### Step 7: Cleanup
The program releases the video capture and writer objects and closes all OpenCV windows upon termination.

## Usage
- Python 3.7+
- OpenCV library
- A webcam or video input device

### Running the Code
1. Ensure the required libraries are installed.
2. Run the Python script in the notebook:
3. The live video feed with motion detection will appear in a window.
4. Press `Esc` to stop the program.

### Output File
The processed video is saved as `output.avi` in the current working directory. It includes bounding boxes and motion status messages.

