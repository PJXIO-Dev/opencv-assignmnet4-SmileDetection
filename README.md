# Smile Detection with OpenCV and YOLO Face Landmarks

This project contains a Jupyter notebook assignment that detects smiles in video frames using facial landmarks predicted by a lightweight YOLO face model. The repository includes a sample video (`smile.mp4`) and expects the YOLO checkpoint (`yolov8n_face_kpts.pt`) to be available in `data/` relative to the notebook.

## Contents
- **Assignment - Smile Detection.ipynb** – main notebook implementing the smile detector, generating an annotated output video, and producing a debug visualization video with per-frame landmarks.
- **smile.mp4** – sample input video used by the notebook.

## Requirements
- Python 3.8+
- OpenCV (`cv2`)
- NumPy
- Ultralytics YOLO (`ultralytics` package)

Install dependencies (example):
```bash
pip install opencv-python-headless numpy ultralytics
autonb  # if you plan to run the notebook in Jupyter
```

## Running the Notebook
1. Place the YOLO facial keypoints checkpoint at `data/yolov8n_face_kpts.pt` relative to the notebook.
2. Open and run all cells in `Assignment - Smile Detection.ipynb` in order.
3. The notebook will read `smile.mp4`, perform per-frame smile detection, and produce two videos:
   - `output_smile.mp4` (primary annotated output)
   - `output_smile_debug.mp4` (debug video with green/red landmark overlays showing which smile conditions pass or fail)

## Smile Detection Logic
The detector classifies a frame as smiling when:
- Mouth corners pull outward relative to jaw width.
- Mouth corners lift slightly above the mouth center.
- An optional eye-squint check can invalidate a smile if eyes are too wide relative to jaw width.

Laughing (wide open mouth) is treated as smiling but an open mouth is **not required**. The logic updates per frame without relying on previous state.

## Notes
- Do not modify the autograder cell or change video/model paths when completing the assignment.
- The primary video output remains unaltered; the debug video is additional for visualization.
