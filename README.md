# Real-Time Body Part Tracking with MediaPipe

A webcam app that detects hand, face, iris and body landmarks with MediaPipe, draws them on a black canvas, and traces the movement of one selected point per body part. A small Tkinter window lets you choose which traces to show.

All code is in [`tracking_algo.py`](tracking_algo.py).

---

## Results

![Screenshot (644)](https://github.com/user-attachments/assets/8e2ef8d5-4f1f-4d43-a818-fbc6eb489b6e)
![GIFMaker_hand](https://github.com/user-attachments/assets/2dd82fbb-ade2-4b62-8562-abf92cbbc070)

![Screenshot (645)](https://github.com/user-attachments/assets/674cbd23-3881-469d-91b9-c822fec4b94f)
![GIFMaker_face](https://github.com/user-attachments/assets/28729023-0e3f-448e-9c96-a67ce4a08b5d)

![Screenshot (646)](https://github.com/user-attachments/assets/8a0e60ac-2f0d-40b1-bfa7-1022973cd346)
![GIFMaker_me](https://github.com/user-attachments/assets/0f081ba6-7b74-4d9b-9c01-b2125f500499)

---

## What It Does

* **Always drawn:** hand skeleton (green), face mesh (blue), body pose skeleton (cyan) and iris points (orange), on a black frame
* **Optional movement traces**, chosen in the GUI:

| Option | Point traced |
| --- | --- |
| Hand | index fingertip (right-hand side of the image preferred) |
| Face | nose tip |
| Iris | centre of one iris |
| Body | right shoulder |

* When you quit, the last frame with all traces is saved as `tracking_result.png` and opened.

---

## How to Run

```bash
pip install -r requirements.txt
python tracking_algo.py
```

1. Tick the parts you want to trace and click **Start**.
2. Move in front of the webcam.
3. Press `q` or `Esc` in the video window to stop.

---

## Fixes in This Version

* Uses the default webcam (`VideoCapture(0)`); it previously opened camera 1
* Iris points now appear: `refine_landmarks=True` is needed for MediaPipe to return iris landmarks, and the image width and height used to place them were not defined
* `q` now quits as well as `Esc`, matching these instructions

---

## Limitations

* Landmarks are drawn in 2D only
* No gesture recognition is implemented
* The video window runs in a background thread, which may not work on macOS

---

## Tools

Python, MediaPipe, OpenCV, NumPy, Tkinter, Pillow
