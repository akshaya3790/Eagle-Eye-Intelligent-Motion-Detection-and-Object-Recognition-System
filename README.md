# Eagle-Eye-Intelligent-Motion-Detection-and-Object-Recognition-System

EagleEye is an AI-powered video surveillance system that combines OpenCV-based motion detection with YOLOv8 object recognition for intelligent monitoring and activity logging.
The system processes video feeds frame-by-frame to detect motion using frame differencing and contour analysis, while YOLOv8 performs real-time object detection with confidence scoring.
Each motion or object detection event is timestamped and logged for post-analysis, and the processed video is annotated and saved with bounding boxes and labels.

⚙️ Key Features
1) Real-time motion detection using frame differencing and Gaussian blur.
2) Object recognition powered by YOLOv8 deep learning model.
3) Automatic timestamped event logging for motion and detected objects.
4) Annotated video output with bounding boxes and confidence scores.
5) Works with CCTV footage or live webcam feeds.

🧠 Tech Stack
1) Python 3
2) OpenCV — for video processing and motion detection
3) Ultralytics YOLOv8 — for real-time object recognition
4) Google Colab — for easy execution and visualization

Flow chart of the code :-

               ┌────────────────────────────────────┐
               │          Start Program             │
               └────────────────────────────────────┘
                             │
                             ▼
          ┌────────────────────────────────────┐
          │  Load Video File or Webcam Stream  │
          └────────────────────────────────────┘
                             │
                             ▼
          ┌────────────────────────────────────┐
          │   Read First Two Video Frames       │
          └────────────────────────────────────┘
                             │
                             ▼
        ┌──────────────────────────────────────────┐
        │      Perform Frame Differencing          │
        │ (absdiff → grayscale → blur → threshold) │
        └──────────────────────────────────────────┘
                             │
                             ▼
          ┌────────────────────────────────────┐
          │ Detect Contours (Moving Objects)   │
          └────────────────────────────────────┘
                             │
                             ▼
                ┌──────────────────────────┐
          ┌───► │ Is Motion Detected?      │
          │     └──────────────────────────┘
          │               │
          │        Yes ───┘
          │               │
          │               ▼
          │  ┌────────────────────────────────────┐
          │  │ Draw Motion Bounding Boxes         │
          │  │ Log Timestamp in "motion_logs.txt" │
          │  └────────────────────────────────────┘
          │               │
          └───────────────┘
                             │
                             ▼
       ┌────────────────────────────────────────────┐
       │ Pass Each Frame to YOLOv8 Model (Detection)│
       └────────────────────────────────────────────┘
                             │
                             ▼
     ┌─────────────────────────────────────────────────┐
     │  For Each Detected Object:                      │
     │  → Get Class, Confidence, and Bounding Box      │
     │  → Annotate Frame with Label & Confidence Score │
     │  → Log Detection Timestamp to File              │
     └─────────────────────────────────────────────────┘
                             │
                             ▼
       ┌────────────────────────────────────────────┐
       │  Display Annotated Frame (cv2_imshow)      │
       │  Write Frame to Output Video File          │
       └────────────────────────────────────────────┘
                             │
                             ▼
         ┌───────────────────────────────────────┐
         │ Read Next Frame / Check for End of Video │
         └───────────────────────────────────────┘
                             │
                  ┌──────────┴──────────┐
                  │                     │
                  ▼                     ▼
        Continue Processing         End of Video
                  │                     │
                  ▼                     ▼
          ┌────────────────────────────────────┐
          │  Close Log File & Release Resources │
          └────────────────────────────────────┘
                             │
                             ▼
               ┌────────────────────────────┐
               │        End Program         │
               └────────────────────────────┘
