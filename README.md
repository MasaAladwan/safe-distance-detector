# Smart Car Distance Violation Detection 🚗

This project is a **fun experiment** that uses computer vision to detect vehicles violating the safe distance rule on streets using a simple phone camera and a bit of Python magic.

---

## Project Overview

analyzed traffic footage to detect cars that are too close to one another. Instead of relying on depth sensors, the road is manually divided into 3 regions with separate distance thresholds to approximate safe following distances.

The result is:

* A snapshot of the violating vehicle
* The car's license plate number (detected using OCR)
* Timestamp of the violation
* All results are logged into **Google Sheets** with a link to the screenshot stored in **Google Drive**
![Image](https://github.com/user-attachments/assets/4b5b0a3e-d61a-4ac3-bc37-d35ae0c02a94)
![Image](https://github.com/user-attachments/assets/c5899285-2d21-4771-bcce-411c3d869110)
---

## Tech Stack

* **Yolo11n** (via Ultralytics) – Object detection
* **BOT-SORT** – Multi-object tracking
* **EasyOCR** – Optical Character Recognition
* **OpenCV** – Frame processing and manipulation
* **NumPy** – Mathematical operations
* **Google Sheets API + Google Drive API** – Saving results

---

## How It Works

1. You input a **video of a street**
2. YOLO detects vehicles and tracks them
3. Manual lane regions are used to estimate distance
4. If a car violates the defined threshold, it:

   * Takes a screenshot
   * Crops the license plate
   * Performs OCR to extract the plate number
   * Uploads the image to Google Drive
   * Logs everything to Google Sheets

---

## Setup Instructions

### 1. Clone this repo

```bash
git clone https://github.com/your-username/safe-distance-detector.git
cd safe-distance-detector
```

### 2. Create and activate a virtual environment (optional but recommended)

```bash
python3 -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add your Google Service Account credentials

* Save your JSON credentials as `credentials.json` in the root directory

---

## ⚠️ Before You Use It

To adapt this project to your own video/street, you **must manually edit** the following parts of the code:

* **Horizon line** and region coordinates for depth approximation
* **Lane detection mask** by providing your own `lane_detection.npy`
* **Google credentials** and Drive/Sheet setup

---

## Notes

* This is **not production-grade** and was made for learning and experimentation.
* The accuracy depends on video quality, camera angle, and region calibration.
* It works best on low-traffic roads with a fixed camera angle.

---

## 📷 Example Output

| Plate Number | Timestamp | Drive Link                           |
| ------------ | --------- | ------------------------------------ |
| 1234567      | 10:22:01  | [View](https://drive.google.com/...) |

---

##  Future Improvements

* Switch to PaddleOCR for better plate recognition
* Replace manual region calibration with perspective transform
* Add a GUI for easier configuration

---

## 😎 Supervisor

Special thanks to my supervisor **Mahmood** for the support and guidance during this project.

---

## License

This project is open-source and free to use. Feel free to modify or improve!
