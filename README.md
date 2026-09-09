<div align="center">
  <img width="260" height="260" src="Eduflex.jpg" alt="Eduflex-icon"/>
  <h1 align="center">Eduflex</h1>
  <p align="center"> 
    A professional desktop application (offline) for managing teachers, students, attendance, exams, subscriptions, and reports.
  </p>
</div>

<div align="center">

<div align="center">
  <img src="https://img.shields.io/static/v1?label=Platform&message=x86__64&color=4C0099" alt="platform"/>
  <img src="https://img.shields.io/static/v1?label=Python&message=3.14&color=4C0099" alt="language"/>
  <img src="https://img.shields.io/static/v1?label=GUI&message=App&color=4C0099" alt="assembly"/>
  <br>
  <img src="https://img.shields.io/static/v1?label=Desk&message=Top&color=4C0099" alt="bootloader"/>
  <img src="https://img.shields.io/static/v1?label=Status&message=Active&color=4C0099" alt="status"/>
  <br>
   <img src="https://img.shields.io/static/v1?label=License&message=MIT&color=4C0099" alt="license"/>
</div>
<br>

<div align="center">
  
  [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white)](https://instagram.com/@bassemmohamed_0)
  [![Reddit](https://img.shields.io/badge/Reddit-%23FF4500.svg?style=for-the-badge&logo=Reddit&logoColor=white)](https://reddit.com/user/00xBassem)
  [![X](https://img.shields.io/badge/X-black.svg?style=for-the-badge&logo=X&logoColor=white)](https://x.com/@Basem2Mohamed)
  
</div>
<p align="center">Made possible by <a href="https://bassemmohamed.pages.dev/"><strong>BassemMohamed</strong></a></p>

## Technologies

<div style="display: flex; flex-direction: row; align-items: center; gap: 10px; flex-wrap: wrap;">
  <img src="https://img.shields.io/static/v1?label=Python&message=3.14.5&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=PySide6.5&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=SQLAlchemy&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=SQLite&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=Argon2id&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=ReportLab&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=openpyxl&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=pytest&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=PyInstaller&color=4C0099"/>
  <img src="https://img.shields.io/static/v1?label=&message=qrcode/OpenCV/pyzbar&color=4C0099"/>
</div>

## 🚧 Project Status

**Current Status:** 🟡 In Development

| Phase | Description | Status |
|:---:|---|:---:|
| 01 | Project Structure + Database + Models | ✅ |
| 02 | Authentication + Teacher Profile | ✅ |
| 03 | Student Management | ✅ |
| 04 | Classes + Subscriptions | ✅ |
| 05 | QR Generation + Scanner | ✅ |
| 06 | Attendance System | ✅ |
| 07 | Exams + Results | ✅ |
| 08 | Reports + Export | ✅ |
| 09 | Dashboard + Login + Main Window | ✅ |
| 10 | Backup / Restore | ✅ |
| 11 | Testing | ✅ |
| 12 | Security Review + Bug Fixing | ✅ |
| 13 | Packaging with PyInstaller | 🟡 |

##  Running the Project — Development Environment

Install the required dependencies, run the test suite, and start the application:

```bash
pip install -r requirements.txt

pytest

python -m app.main
```

### First Run

On the first launch, the application will display a **Teacher Account Setup** screen where you can enter:

* Name
* Subject
* Password

After creating the account, you will be **automatically logged in** and redirected to the **Main Window (Dashboard)**.

The Dashboard displays **real data retrieved directly from the database**.

---

## UI Status

**9 / 9 screens completed** ✅

| Screen             | Status |
| :----------------- | :----: |
| Dashboard          |    ✅   |
| Student Management |    ✅   |
| Attendance         |    ✅   |
| Classes            |    ✅   |
| Subscriptions      |    ✅   |
| Backup & Restore   |    ✅   |
| Exams              |    ✅   |
| Reports            |    ✅   |
| Settings           |    ✅   |

### ⚠️ Known Limitation

There is currently **one exception**:

**Live camera QR scanning** is not yet connected directly to the Attendance screen UI.

The QR scanning backend is already fully implemented and available at:

```text
app/qr/scanner.py
```

All other core screens and functionality are implemented and operational.

## Building the Windows `.exe`

Run the following script:

```bat
build_windows.bat
```

> ⚠️ **Important:** This script must be executed on a **real Windows machine**, not in the current development environment.

Make sure you are running it inside a **virtual environment** with all dependencies from `requirements.txt` installed.

The script will:

1. Run the test suite first.
2. Build the Windows application using `eduflex.spec`.
3. Generate the final executable at:

```text
dist\Eduflex\Eduflex.exe
```

### Build Requirements

* Windows
* Python
* Virtual environment (`venv`)
* Dependencies installed from `requirements.txt`
* PyInstaller
* All tests passing successfully


## Security Review Summary — Phase 12

The following security checks and fixes were completed during **Phase 12**:

* **No `print()` statements are used for error handling** anywhere in the codebase. This was verified through an actual codebase-wide search.

* **Passwords and password hashes never appear in log files.** This was verified by inspecting the actual log contents after login and password-change operations.

* **QR tokens and their associated payloads are never logged.**

* **SQL Injection attempts** in user-provided input, such as a student name, are safely stored as plain text through **SQLAlchemy ORM** and are never executed as SQL commands. This was verified through actual testing.

* **End-to-End testing** covers the complete application flow, from authentication through backup and restore.

* **Critical bug discovered and fixed:** Backup filenames could collide when generated within the same second, potentially causing data loss during restoration. See **Phase 10** for details.

* **Logging bug discovered and fixed:** The logging system did not correctly track changes to data paths. This issue affected the test environment only and had **no impact on the actual production environment**.

## Project Structure

```text
Eduflex/
├── app/
│   ├── main.py
│   ├── config/        # Data paths and application settings
│   ├── database/      # SQLAlchemy connection and migrations
│   ├── models/        # Database tables (ORM models)
│   ├── repositories/  # Data access layer
│   ├── services/      # Business logic
│   ├── security/      # Password hashing and security
│   ├── qr/            # QR code generation and scanning
│   ├── reports/       # PDF/Excel report generation
│   ├── ui/            # PySide6 user interfaces
│   └── utils/         # Utilities (logging, exceptions)
├── tests/             # Automated tests
├── assets/            # Application assets
├── requirements.txt   # Python dependencies
└── pyproject.toml     # Project configuration
```


## Security Notes

* **Passwords** are stored exclusively as **Argon2id hashes** and are never stored in plain text.

* **QR codes** contain only a randomly generated token and do **not** contain any personal information.

* The **database** is stored in the user's application data directory (`AppData`) rather than inside the installation directory.

  This keeps user data separate from the application files and helps prevent data loss during application updates or reinstallation.


## Thanks for Checking Out Eduflex!

Thank you for taking the time to read through the README and explore the project.

If you found **Eduflex** interesting, feel free to check out more of my work and projects:

### My Portfolio

**[Visit My Portfolio](https://bassemmohamed.pages.dev/)**

---

*Built with Python, PySide6, and a focus on security, reliability, and clean architecture.*
