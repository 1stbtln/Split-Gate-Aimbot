# Splitgate Aimbot

A computer vision-based aimbot for Splitgate using YOLOv8 object detection.

## Overview

This project uses computer vision and deep learning to detect enemies in Splitgate and assist with aiming. The system captures a portion of the screen, processes it through a custom-trained YOLOv8 model to detect enemies, and can control mouse/joystick movement to aim at targets.

## Features

- **Real-time enemy detection** using YOLOv8 object detection
- **Configurable screen capture region** for optimized performance
- **Toggle functionality** with keyboard shortcuts
- **Multiple control options**:
  - Mouse movement-based aiming
  - Virtual joystick input via pyvjoy
- **Video analysis tools** for debugging and improvement

## Project Structure

```
split-gate aimbot/
├── scripts/
│   ├── aimbot.py              # Main aimbot using mouse movement
│   ├── aimbot_native_input.py # Aimbot using virtual joystick
│   ├── debugScript.py         # Tool for annotating gameplay videos
│   └── train.py               # YOLOv8 model training script
├── runs/
│   └── detect/
│       └── splitgate_aimbot_yolov8n/ # Trained model and parameters
├── splitgate_dataset/         # Training dataset
└── cpp/
    └── mouse_mover.cpp        # C++ mouse movement implementation
```

## Installation

1. Clone this repository
2. Install the required Python packages:
   ```
   pip install ultralytics opencv-python numpy mss pynput pyvjoy
   ```
3. Build the C++ mouse mover (if using):
   ```
   g++ -o cpp/mouse_mover.exe cpp/mouse_mover.cpp
   ```

## Usage

### Running the Aimbot

1. Start Splitgate
2. Run one of the aimbot scripts:
   ```
   python scripts/aimbot.py
   ```
   Or for virtual joystick input:
   ```
   python scripts/aimbot_native_input.py
   ```

### Controls

- **Hold C**: Temporarily pause aimlock
- **Release C**: Resume aimlock
- **ESC**: Exit the application

### Configuration

You can adjust the screen capture region by modifying the `monitor` variable in the aimbot scripts:

```python
monitor = {"top": 240, "left": 420, "width": 1080, "height": 600}
```

## Model Training

The aimbot uses a custom-trained YOLOv8n model. To train your own model:

1. Prepare your dataset in the YOLOv8 format
2. Run the training script:
   ```
   python scripts/train.py
   ```

The model was trained on 101 images with the following parameters:
- 100 epochs
- Image size: 640x640
- Batch size: 4

## Debugging

You can use debugScript.py to analyze gameplay footage and see detection performance:

```
python scripts/debugScript.py
```

This will process a video file and create an annotated version showing enemy detections.

## Disclaimer

This project is for educational purposes only. Using aimbots in online games may violate terms of service and result in account bans. Use at your own risk and only in private/offline gameplay scenarios or for learning computer vision techniques.

## License

This project uses a dataset under CC BY 4.0 license.
