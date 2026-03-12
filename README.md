# VARUNA - AI Accident Detection & Smart Traffic Control

An intelligent traffic management system that detects accidents in real-time and automatically optimizes traffic signals to reduce congestion and improve emergency response.

## What It Does

- **Accident Detection**: Uses YOLOv8 models to identify accidents, damaged vehicles, and emergency situations from camera feeds
- **Smart Signal Control**: Dynamically adjusts traffic light timings based on road conditions and incident severity
- **Multi-Junction Support**: Handles intersections from 2-way (T-junction) to 6-way complex junctions
- **Real-Time Dashboard**: Visualizes traffic flow, accident locations, and signal optimization in the browser
- **Emergency Response**: Prioritizes ambulance lanes and fire brigade routes automatically

## Watch Demo Video:

https://www.youtube.com/watch?v=X0kgA0yyBOk

## Key Features

- **Multiple Detection Models**:
  - Accident detection (accident_v2.pt)
  - Vehicle counting (vehicle_counting.pt)
  - Ambulance detection
  - Fire detection
  - Damage assessment

- **Smart Algorithms**:
  - Adaptive signal timing based on vehicle density
  - Incident-aware routing (normal, traffic jam, minor accident, severe accident, fire)
  - Priority-based lane management
  - Real-time signal optimization

- **Interactive Dashboard**:
  - Live video feed with detection overlays
  - Real-time signal status at multiple junctions
  - Accident history and evidence storage
  - Algorithm visualization for debugging

## Quick Start

### Option 1: One-Click Start (Windows)
```batch
Double-click START_SYSTEM.bat
```
This opens both backend and frontend automatically.

### Option 2: Python Script
```powershell
python start_system.py
```

### Option 3: Manual Setup
```powershell
# Terminal 1 - Backend (Port 8000)
python main.py

# Terminal 2 - Frontend (Port 3000)
cd dashboard
npm install
npm start
```

Access the dashboard at `http://localhost:3000`

## Project Structure

```
VARUNA/
├── main.py                 # FastAPI backend with video processing
├── signal_algorithms.py    # Smart signal control logic
├── backend/models/         # YOLO model files
├── dashboard/              # React frontend
├── data/                   # Evidence archive (fire/severe incidents)
└── archives/               # Backup & trial versions
```

## Requirements

- Python 3.8+
- Node.js 14+
- OpenCV (`cv2`)
- FastAPI & Uvicorn
- YOLOv8 (Ultralytics)
- React 18

## How It Works

1. **Video Input**: Reads from camera or mobile stream
2. **Detection**: YOLO models identify vehicles, accidents, and hazards
3. **Analysis**: Signal algorithm decides optimal traffic flow
4. **Control**: Sends signal timings to traffic lights
5. **Dashboard**: WebSocket updates show real-time status

## Configuration

Edit these values in `main.py`:
- `MOBILE_CAMERA_URL`: Video feed source
- `MODEL_NAME`: Detection model path
- `CAMERA_LAT/LON`: Location coordinates
- `TELEGRAM_BOT_TOKEN`: For alerts (optional)

## Supported Intersections

- **2-way**: T-junction
- **3-way**: Y-junction
- **4-way**: Standard cross intersection
- **5-way**: Star junction
- **6-way**: Complex multi-lane intersection

## 🚧 Work In Progress

### Traffic Management Enhancement (YOLOv10 Integration)
We are actively working on improving the traffic management component of the system. This includes:

- **YOLOv10 Migration**: Transitioning from YOLOv8 to YOLOv10 for more accurate and efficient traffic flow analysis
- **Advanced Vehicle Tracking**: Enhanced multi-object tracking for better vehicle count and movement prediction
- **Congestion Pattern Recognition**: Machine learning models to predict and prevent traffic congestion before it occurs
- **Lane-Level Traffic Optimization**: Fine-grained control of individual lanes to maximize throughput

**Status**: Model integration and testing in progress. Expected to significantly improve traffic prediction accuracy and signal optimization response times.

## Troubleshooting

**Backend won't start?**
- Check if port 8000 is already in use
- Ensure YOLOv8 models are in `backend/models/`

**Dashboard won't connect?**
- Verify backend is running on port 8000
- Check browser console for connection errors

**No video feed?**
- Check camera URL config in `main.py`
- Ensure camera is accessible from your network

## Screenshot:
<img width="1905" height="960" alt="image" src="https://github.com/user-attachments/assets/6293eb66-0019-4bca-a38f-5aee705ac456" />


## Notes

- Make sure all model files (`*.pt`) are present in `backend/models/`
- First run downloads required dependencies
- System works best with stable internet connection
- Tested on Windows with Intel i5+ and 8GB RAM minimum

---

Built for the Indian Innovates Hackathon. Real-time processing with ML-based traffic optimization.
