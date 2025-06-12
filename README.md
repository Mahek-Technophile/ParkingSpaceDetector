# Smart Parking Space Detector

The Parking_Space_Detector is a Python-based computer vision project that detects available parking spots in a parking lot using a static overhead video feed. It uses OpenCV for image processing and allows users to define parking zones manually, then continuously analyzes whether each spot is occupied or free based on pixel analysis.

This solution can be useful for smart parking systems, mall/office parking monitoring, or integrating into IoT-based parking guidance apps.
## 🔧 Features

- Detects free and occupied parking slots from video footage
- Saves parking slot coordinates using a simple GUI-based selector
- Visualizes space availability with color-coded overlays (Green = Free, Red = Occupied)
- Adjustable threshold values via interactive trackbars for calibration
- Displays real-time slot usage count on screen

## 🧰 Tech Stack

- Python
- OpenCV
- cvzone
- Numpy
- Pickle (for data persistence)

## 🖼️ Components

- `ParkingSpacePicker.py`: GUI to manually select and save parking slot coordinates
- `main.py`: Core logic for detecting space availability from a video feed
- `main.py (with Trackbars)`: Advanced version with dynamic tuning via GUI trackbars

## 📂 Usage

1. Run `ParkingSpacePicker.py` to select and save parking space positions
2. Use `main.py` to detect and visualize free spaces in real time
3. Optionally, use the version with trackbars for fine-tuning detection

## 📽️ Input

- `carPark.mp4`: Video input of a parking lot
- `carParkImg.png`: Image input for manual space selection

## 📌 Requirements

Install dependencies via pip:

pip install opencv-python cvzone numpy 

# Detailed Overview & Purpose of Each File

## 1. createpolygons.py:
To manually define the parking space regions in a frame of the parking video.

How it works:

> Loads an image (carParkImg.png).

> Allows the user to draw polygons using mouse clicks. [Right click = Add & Left Click = Delete]

> Saves the polygon coordinates in a file called CarParkPos. and Polygons 

This file is run only once to set up the layout of the parking spots.
**➡️ This lets your detector adapt to any parking layout**


**createpolygons.py                  	Define parking spot coordinates manually using mouse input
CarParkPos	                           Stores saved polygon coordinates for each parking space
checkParkingSpace()	                  Detects if space is free or occupied based on pixel analysis
polygons / posList	                   List of all defined parking spot polygons used for detection**

## 2. main.py
 To analyze a video frame-by-frame and detect which parking spaces are occupied or free.

How it works:

Loads a parking video (carPark.mp4) and predefined parking space polygons from CarParkPos.

Converts each frame to grayscale, applies Gaussian blur, and adaptive thresholding.

For each parking space polygon:

Crops the region of interest (ROI).

Calculates the number of non-zero pixels.

Compares it against a threshold to detect whether the spot is free or occupied.

Overlays green or red polygons on the video to indicate free or occupied spots.

Displays the total count of free spaces in the top-left corner.

## 3. parkingspace.py

Purpose:
Contains the helper functions used in main.py — specifically for processing each parking spot polygon.

What it includes:

checkParkingSpace(): Given a frame and polygon points, it processes the region and checks occupancy.

Handles pixel counting and drawing overlays.


## 🧱 Detailed Tech Stack Overview
✅ 1. Programming Language
Python

Core language used for image processing, video analysis, and logic implementation.

🧰 2. Libraries & Frameworks
Library	Purpose
OpenCV	Core image & video processing (grayscale, blur, thresholding, masking)
pickle	Saving and loading parking spot coordinates (as binary data)
NumPy	(Optional/implicitly used by OpenCV) Efficient array/matrix operations

📂 3. Project Files
createpolygons.py → Interactive tool to define parking zones (GUI using OpenCV mouse events).

main.py → Video loop and live analysis of each frame.

parkingspace.py → Modular detection logic for each parking spot.

🎥 4. Input Media
.mp4 Video file → Pre-recorded parking lot footage

.png Image file → For selecting parking space regions

📦 5. Storage / Data
Binary file (CarParkPos) → Stores all polygon coordinates of parking spots
 
