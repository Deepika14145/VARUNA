# VARUNA 🚦

**AI-powered accident detection and smart traffic control system.**

Varuna uses a live camera feed, YOLOv8-based object detection, and adaptive signal algorithms to detect road accidents in real time and automatically adjust traffic signals to prioritize emergency response.

---

## Features

- **Real-time detection** — YOLOv8 model identifies accidents, fire, and traffic congestion from a live IP webcam or video feed.
- **Smart signal control** — Multi-junction support (2–6 way intersections) with incident-aware signal timing.
- **Live dashboard** — React frontend with a real-time map, camera stream, and signal state visualization via WebSocket.
- **Evidence archiving** — Auto-saves annotated frames when an incident is detected.
- **Nearest hospital routing** — Maps the closest hospital to the incident location.

---

## Tech Stack

| Layer     | Technology                        |
|-----------|-----------------------------------|
| Backend   | Python, FastAPI, WebSocket, OpenCV |
| Detection | YOLOv8 (Ultralytics)              |
| Frontend  | React 18, React-Leaflet            |
| Camera    | IP Webcam (Android) / Local webcam |

---

## Quick Start

### 1. Install Python dependencies
```bash
pip install -r requirements.txt
# or
install_deps.bat
```

### 2. Set camera URL (optional)
Edit `main.py` or set the environment variable:
```
MOBILE_CAMERA_URL=https://<phone-ip>:8080
```

### 3. Start the backend
```bash
python start_system.py
# or
start_system.bat
```

### 4. Start the dashboard
```bash
cd dashboard
npm install
npm start
```

Dashboard runs at `http://localhost:3000`, backend API at `http://localhost:8000`.

---

## Project Structure

```
VARUNA/
├── main.py                 # FastAPI backend + detection loop
├── signal_algorithms.py    # Multi-junction signal control logic
├── start_system.py         # System launcher
├── dashboard/              # React frontend
│   └── src/App.js
├── evidence_archive/       # Saved incident frames
└── archives/               # Older experiment code
```

---

## Notes

- Requires a CUDA-capable GPU for best performance (CPU fallback supported).
- Tested with Android IP Webcam app on a local LAN.
- Optimized for Maharashtra & Karnataka traffic junction patterns.
