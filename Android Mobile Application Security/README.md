# Android Mobile Security Lab

Mobile security is a rapidly growing field, but many of the available tools are still evolving. Compared to other cybersecurity domains, Android-focused tools often have limited documentation, reduced stability, and fewer real-world testing scenarios.  
This lab introduces key tools used in Android application analysis and mobile security research.

---

## 🎯 Lab Objectives

Set up, research, and evaluate the following tools on your PC:

- **JADX-GUI**
- **ADB (Android Debug Bridge)**
- **Android Emulator with Docker + ADB Bridge**

You will demonstrate these tools to your instructor and provide a brief description of how each one works.

---

## 🧰 Prerequisites

### System Requirements
- Windows 10/11 (64-bit)
- At least **8GB RAM**
- Minimum **20GB free disk space**

### Software Requirements
- Docker Desktop (installed and running)
- Administrator access  
  - *(For Cyber Lab PCs: use the **cyber staff** account)*

### macOS Users
If using a Mac, ensure **Homebrew** is installed before proceeding with the tool setup.

---

## 🛠️ Tools Overview

### 1. **JADX-GUI**
A reverse-engineering tool for Android apps. It converts `.apk` or `.dex` files into readable Java source code.  
Useful for:
- Inspecting application internals  
- Identifying security flaws  
- Reviewing resources and manifest files  

---

### 2. **ADB (Android Debug Bridge)**
A command-line tool used to communicate with Android devices or emulators.  
With ADB, you can:
- Install or extract apps  
- View logs using `logcat`  
- Access system paths  
- Forward ports for testing  

---

### 3. **Android Emulator (Docker + ADB Bridge)**
A containerized Android environment that runs via Docker.  
It provides:
- An isolated virtual Android device  
- Easy integration with ADB through port mapping  
- A reproducible setup ideal for mobile security labs  

---

## 📦 Installation & Setup

Follow your lab instructions to:

1. Install **JADX-GUI**  
2. Install and configure **ADB**  
3. Deploy the **Android Emulator** using Docker  
4. Set up the **ADB Bridge** to connect the emulator to your host machine  

---

## 📝 Evaluation

After the setup:

- Launch each tool  
- Perform basic tests (e.g., analyze an APK with JADX or connect ADB to the emulator)  
- Document any issues or observations  
- Prepare to present your findings to your instructor  

---

## 📚 Summary

This lab familiarizes you with essential Android mobile security tools and helps you build hands-on skills in analyzing and interacting with Android applications.  
The experience gained here forms a strong foundation for deeper research into mobile security testing.


