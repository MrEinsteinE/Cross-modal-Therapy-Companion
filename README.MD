# 🧠 Therapy Companion - AI-Powered Wellbeing Application

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Flask](https://img.shields.io/badge/Flask-3.0%2B-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Active-success)

**An intelligent mental health companion that uses AI to analyze emotions through facial expressions and voice, providing personalized wellbeing insights and coping strategies.**

[Features](#features) • [Installation](#installation) • [Usage](#usage) • [Technologies](#technologies) • [Contributing](#contributing)

</div>

---

## 📋 Overview

Therapy Companion is a comprehensive mental health application that combines **computer vision**, **voice emotion recognition**, and **AI-driven insights** to help users track and improve their emotional wellbeing. The application provides real-time emotion analysis, stress assessments, and personalized coping techniques.

### Key Highlights

- 🎭 **Facial Emotion Detection** - Real-time emotion analysis using DeepFace with 8 detection backends
- 🎤 **Voice Emotion Recognition** - Advanced audio analysis using Wav2Vec2 transformer models
- 📊 **Interactive Dashboards** - Beautiful charts showing stress trends, emotion patterns, and wellness metrics
- 🧘 **Coping Techniques** - Guided exercises including breathing, meditation, and grounding techniques
- 🆘 **Crisis Support** - Immediate access to mental health crisis resources
- 📈 **Progress Tracking** - Comprehensive check-in history with data visualization

---

## ✨ Features

### 1. Emotion Analysis
- **Face Detection**: Supports 8 detection backends (RetinaFace, MediaPipe, MTCNN, OpenCV, SSD, Dlib, YOLO, YuNet)
- **Voice Analysis**: Recognizes emotions from voice patterns (Happiness, Sadness, Anger, Neutral, etc.)
- **Real-time Processing**: Instant feedback on emotional state

### 2. Wellbeing Assessment
- Comprehensive stress scoring (0-8 scale)
- Multi-factor analysis including:
  - Facial expressions
  - Voice tone
  - Sleep duration
  - Activity level
  - Self-reported mood

### 3. AI-Powered Insights
- Personalized recommendations based on user data
- Context-aware coping strategies
- Progress tracking and trend analysis

### 4. Interactive Visualizations
- **Stress Trend Chart**: Line graph showing stress levels over time
- **Emotion Distribution**: Pie chart of emotion frequency
- **Wellness Patterns**: Bar chart comparing sleep and activity levels

### 5. Mental Health Support
- 24/7 crisis hotline information
- Guided coping techniques:
  - Deep Breathing (4-7-8 technique)
  - Grounding Exercise (5-4-3-2-1 method)
  - Progressive Muscle Relaxation
  - Mindful Meditation

---

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- FFmpeg (for audio processing)
- Webcam and microphone access

### Step 1: Install FFmpeg

#### Windows:
```
# Using Chocolatey
choco install ffmpeg

# Or download from: https://ffmpeg.org/download.html
# Extract to C:\ffmpeg and add C:\ffmpeg\bin to PATH
```

#### macOS:
```
brew install ffmpeg
```

#### Linux (Ubuntu/Debian):
```
sudo apt update
sudo apt install ffmpeg
```

### Step 2: Clone the Repository

```
git clone https://github.com/yourusername/therapy-companion.git
cd therapy-companion
```

### Step 3: Set Up Virtual Environment

```
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate
```

### Step 4: Install Dependencies

```
pip install -r requirements.txt
```

### Step 5: Configure FFmpeg Path (Windows Only)

If FFmpeg is not in your system PATH, edit `app.py` and set the correct path:

```
# At the top of app.py
ffmpeg_path = r"C:\ffmpeg\bin"  # Update this to your FFmpeg location
AudioSegment.converter = os.path.join(ffmpeg_path, "ffmpeg.exe")
AudioSegment.ffprobe = os.path.join(ffmpeg_path, "ffprobe.exe")
```

---

## 🎯 Usage

### Running the Application

1. **Activate the virtual environment** (if not already activated):
   ```
   # Windows
   venv\Scripts\activate
   
   # macOS/Linux
   source venv/bin/activate
   ```

2. **Start the Flask server**:
   ```
   python app.py
   # Or
   flask run
   ```

3. **Access the application**:
   Open your web browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```

### Using the Application

1. **Select Your Mood** - Click on the emoji that best represents how you're feeling
2. **Capture Face Emotion** - Allow camera access and capture your facial expression
3. **Record Voice** - Speak naturally for 5-10 seconds to analyze voice emotion
4. **Set Wellness Factors** - Adjust sleep hours and activity level
5. **Complete Assessment** - Click the assessment button to get personalized insights
6. **View Dashboard** - Track your progress with interactive charts and history

---

## 🛠 Technologies

### Backend
- **Flask** - Python web framework
- **DeepFace** - Facial emotion recognition
- **Transformers** (Hugging Face) - Voice emotion analysis with Wav2Vec2
- **librosa** - Audio processing and feature extraction
- **OpenCV** - Computer vision and image processing
- **PyTorch** - Deep learning framework
- **pandas** - Data manipulation and CSV handling
- **pydub** - Audio file format conversion

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with CSS Grid and Flexbox
- **JavaScript (ES6+)** - Interactive functionality
- **Chart.js** - Data visualization
- **Web Audio API** - Real-time waveform visualization
- **MediaRecorder API** - Voice recording

### AI/ML Models
- **Wav2Vec2-base-superb-er** - Voice emotion recognition
- **DeepFace** - Multi-backend facial emotion detection

---

## 📂 Project Structure

```
therapy-companion/
│
├── app.py                      # Flask application & backend logic
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
├── .gitignore                  # Git ignore rules
│
├── static/                     # Static assets
│   ├── css/
│   │   └── style.css          # Application styling
│   └── js/
│       └── main.js            # Frontend JavaScript
│
├── templates/                  # HTML templates
│   └── index.html             # Main application page
│
├── captured_images/            # Stored facial captures (not in Git)
├── temp_audio/                 # Temporary audio files (not in Git)
└── wellbeing_logs.csv          # User check-in data (not in Git)
```

---

## 📊 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Serve main application page |
| `/analyze_face` | POST | Analyze facial emotion from image |
| `/analyze_voice` | POST | Analyze voice emotion from audio |
| `/log_checkin` | POST | Save check-in data and generate insights |
| `/get_logs` | GET | Retrieve all check-in history |
| `/clear_logs` | POST | Clear all user data |
| `/get_crisis_resources` | GET | Get crisis support information |
| `/get_coping_techniques` | GET | Get coping strategy details |

---

## 🔒 Privacy & Security

- **Local Processing**: All emotion analysis happens on your local machine
- **No Cloud Storage**: User data is stored locally in CSV format
- **Optional Data Deletion**: Users can clear their history at any time
- **No External APIs**: No data is sent to third-party services

---

## 🐛 Troubleshooting

### Common Issues

#### 1. **Charts Not Loading**
```
# Ensure Chart.js is properly loaded
# Check browser console for errors
# Verify data is being fetched from /get_logs endpoint
```

#### 2. **Voice Recording Fails**
```
# Grant microphone permissions in browser
# Verify FFmpeg is installed and configured
# Check temp_audio/ directory permissions
```

#### 3. **Face Detection Error**
```
# Grant camera permissions
# Try different detection backends
# Ensure good lighting conditions
```

#### 4. **NoBackendError (Audio)**
```
# Install FFmpeg: brew install ffmpeg (macOS) or choco install ffmpeg (Windows)
# Set FFmpeg path in app.py if not in system PATH
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guide for Python code
- Use meaningful commit messages
- Add comments for complex logic
- Test thoroughly before submitting PR

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **DeepFace** - For facial emotion recognition framework
- **Hugging Face** - For transformer models and libraries
- **Chart.js** - For beautiful data visualizations
- **Flask Community** - For excellent web framework and documentation

---

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Open an issue on GitHub
3. Contact: your.email@example.com

---

## 🌟 Future Enhancements

- [ ] Multi-language support
- [ ] Database integration (SQLite/PostgreSQL)
- [ ] User authentication system
- [ ] Mobile app version
- [ ] Export reports as PDF
- [ ] Integration with wearable devices
- [ ] Group therapy session support
- [ ] Therapist dashboard

---

## ⚠️ Disclaimer

This application is designed as a **supplementary mental health tool** and is **not a substitute for professional medical advice, diagnosis, or treatment**. Always seek the advice of qualified health providers with any questions you may have regarding a mental health condition.

---

<div align="center">

**Made with ❤️ for mental health awareness**

[⬆ Back to Top](#-therapy-companion---ai-powered-wellbeing-application)

</div>

