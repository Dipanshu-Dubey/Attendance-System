# AI GPS-Based Attendance System

An attendance management system that combines a PHP/MySQL web application with a
Flask service for webcam-based face recognition. The system supports employee
registration, face capture, attendance marking, location-aware administration,
and attendance reports.

## Features

- Employee signup, login, profile management, and administration
- Face-image capture and K-Nearest Neighbors face recognition
- Webcam-based attendance marking
- Daily attendance records stored as CSV files
- PHP/MySQL employee, attendance, location, and settings management
- Attendance dashboards and detailed reports

## Technology

- PHP and MySQL
- Python 3 with Flask
- OpenCV for webcam and face detection
- NumPy, pandas, scikit-learn, and joblib
- HTML, CSS, and JavaScript

## Project layout

The application source is currently distributed in:

```text
AI-GPS-based-Attendance-System-main (3).zip
```

After extracting it, the main files and directories are:

```text
app.py                         Flask face-recognition service
*.php                          PHP web pages and backend handlers
__dbconnection.php             MySQL connection configuration
Attendance/                    Daily attendance CSV files
static/faces/                  Registered employee face images
static/face_recognition_model.pkl
                               Trained face-recognition model
haarcascade_frontalface_default.xml
                               OpenCV face detector
```

## Requirements

- PHP 7.4+ with MySQLi
- MySQL or MariaDB
- Python 3.8+
- A working webcam
- XAMPP, WAMP, or another PHP-compatible web server

## Installation

1. Extract the archive into the web server document root, such as
   `htdocs/AI-GPS-based-Attendance-System-main`.
2. Create a MySQL database named `ai_attendance`.
3. Create the tables required by the PHP pages: `employees`, `attendance`,
   `locations`, and `settings`. The PHP source contains the fields used by each
   page; update the schema to match your deployment.
4. Update `__dbconnection.php` if your MySQL host, username, password, or
   database name differs from the defaults:

   ```php
   $host = "localhost";
   $user = "root";
   $password = "";
   $database = "ai_attendance";
   ```

5. Extract the Python service and install its dependencies:

   ```bash
   cd AI-GPS-based-Attendance-System-main
   python -m venv .venv
   source .venv/bin/activate       # Windows: .venv\Scripts\activate
   pip install flask opencv-python numpy pandas scikit-learn joblib
   ```

6. Start the Flask service:

   ```bash
   python app.py
   ```

   It listens on `http://127.0.0.1:1000`.

7. Start Apache and MySQL, then open the PHP application through Apache, for
   example `http://localhost/AI-GPS-based-Attendance-System-main/`.

## Usage

1. Create an employee account from the PHP application.
2. Capture face images for the employee using the face-registration flow.
3. Use the Flask attendance flow to recognize the employee from the webcam.
4. Press `a` when the recognized face should be recorded, or `q` to exit.
5. Review the generated daily CSV files in `Attendance/` and the PHP
   dashboards.

## Notes

- Camera access must be available to the machine running the Flask service.
- The Flask service uses relative paths, so run `app.py` from the extracted
  project directory.
- Do not commit real employee face images, model files, attendance records, or
  production database credentials to a public repository.
