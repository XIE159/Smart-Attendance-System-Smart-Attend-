# Smart-Attendance-System-Smart-Attend-


# ICAT-2: SmartAttend

SmartAttend is an intelligent attendance management system that leverages face detection and recognition to automate classroom attendance. Built with Python, MongoDB, OpenCV, and a custom GUI, it streamlines the process for teachers and students.

---

## Table of Contents
- [Features](#features)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Install Dependencies](#1-install-dependencies)
  - [How to Run](#2-how-to-run)
- [Usage](#usage)
- [Model Details](#model-details)
  - [Face Detection](#face-detection)
  - [Face Recognition](#face-recognition)
  - [Database Schema](#database-schema)
  - [Sample Augmentation](#sample-augmentation)
- [Key Scripts](#key-scripts)
- [Requirements](#requirements)
- [Acknowledgements](#acknowledgements)
- [License](#license)
- [Contact](#contact)

---

## Features

- **Automated Attendance:** Uses a deep learning face detection model (Caffe) and a Random Forest classifier for student recognition.
- **User Authentication:** Secure login and signup for teachers.
- **Class & Management:** Add, view, and manage classes and students.
- **Sample Collection & Augmentation:** Collects face samples and augments them for robust training.
- **Model Training:** Trains a classifier for each class using collected samples.
- **Attendance Marking:** Detects and recognizes students from images to mark attendance.
- **Reporting:** Generates CSV attendance reports per class.
- **Modern GUI:** Built with CustomTkinter for a sleek, user-friendly interface.

---

## Project Structure

```
SmartAttend/
├── src/
│   ├── main.py                   # Main application entry point
│   ├── model_testing.py          # Face detection/recognition testing
│   ├── initialize_db.py          # Database initialization
│   └── initialize_folders.py     # Folder structure setup
├── detection_model/
│   ├── architecture.prototxt     # Caffe model architecture
│   └── weights.caffemodel       # Pre-trained model weights
└── requirements.txt             # Python dependencies
```

---

## Getting Started

### 1. Install Dependencies

Install Python 3.8+ and run:

1. Clone the repository:
```bash
git clone https://github.com/yourusername/ICAT-2.git
cd ICAT-2
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Install and start MongoDB:
```bash
sudo systemctl start mongod
```

4. Initialize the system:
```bash
python src/initialize_db.py
python src/initialize_folders.py
```

---

### 2. How to Run

1. Start the application:
```bash
python src/main.py
```
2. Login or create a teacher account
3. Create classes and add students
4. Collect face samples using the webcam
5. Train the recognition model
6. Start taking attendance!
---

## Usage
- **Login/Signup:** Start the app and log in or sign up as a teacher.
- **Manage Classes:** Add new classes and view existing ones.
- **Add Students:** Add students to classes and collect face samples.
- **Train Model:** After collecting samples, train the classifier for the class.
- **Mark Attendance:** Use the GUI to upload an image and mark attendance automatically.
- **Generate Reports:** Export attendance records as CSV files.

---

## Model Details
### Face Detection
- Uses Caffe-based deep learning model
- Real-time detection through OpenCV
- Configurable confidence threshold

### Face Recognition
- Random Forest classifier per class
- Data augmentation using Albumentations
- Features:
  - Rotation and flips
  - Brightness/contrast adjustment
  - Noise injection
  - Elastic transformations

### Database Schema
- Teachers: {teacherID, username, password}
- Classes: {classID, className, teacherID, students[]}
- Students: {studentID, name, age, gender, batch, major}
- Attendance: {date, classID, present[]}
  
### Sample Augmentation:
- Uses Albumentations library for robust data augmentation:
  - Geometric Transforms:
    - Random rotation (±30 degrees)
    - Horizontal flips
    - Random scale (±20%)
    - Elastic deformations
  - Color Transforms:
    - Brightness and contrast adjustment
    - Random brightness shifts
    - Gamma correction
  - Noise Injection:
    - Gaussian noise
    - Motion blur
    - ISO noise simulation
  - Quality Transforms:
    - JPEG compression
    - Image downscaling
  - Environment Simulation:
    - Lighting changes
    - Shadow effects
    - Weather effects (fog, rain)

This comprehensive augmentation pipeline helps create a more robust face recognition model by:
- Improving model generalization
- Reducing overfitting
- Handling various lighting conditions
- Managing different face angles and poses

---

## Key Scripts
- **initialize_db_for_testing.py:** Resets and seeds the MongoDB database with test teachers, classes, and students.
- **initialize_folder_structure_for_testing.py:** Cleans up the class folders for a fresh start.
- **main.py:** Main application with GUI, database, and all core logic.
- **model_testing.py:** Standalone script for testing face detection and recognition models.

---

## Requirements
- **Python 3.8+**
- **MongoDB (local)**
- **Webcam (for sample collection and testing)**
- **See requirements.txt for Python dependencies.**

---

## Acknowledgements
- **OpenCV**
- **Albumentations**
- **CustomTkinter**
- **MongoDB**

---

## License
This project is for educational purposes.

---

## Contact
For questions or support:
- Open an issue
- Submit a pull request
- Email: sameerrizwanf23@nutech.edu.pk
