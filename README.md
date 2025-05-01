# Smart Parking Space Detector

This project is a computer vision-based parking space monitoring system that detects and visualizes available parking spots using OpenCV and Python. It processes live or recorded video feeds to highlight free vs. occupied parking spaces with real-time updates.

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
```bash
pip install opencv-python cvzone numpy
