# Android Mobile Application Security Lab Setup

This guide walks through installing **JADX-GUI**, **ADB (Android Platform Tools)**, **Docker Android Emulator**, and installing the **InjuredAndroid APK**.  
All steps include screenshots, commands, and helpful notes.

---

## Task 1: Installing JADX-GUI (Windows)

### **Step 1 — Install Java**
JADX requires Java Runtime Environment (JRE).  
Download Java here:  
https://www.java.com/en/

![Installation Page](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image1.png)

---

### **Step 2 — Download JADX GUI**
Download the `.exe` installer from GitHub releases:  
https://github.com/skylot/jadx/releases/tag/v1.2.0

![Download JADX installation file](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image2.png)

---

## Task 2: Installing Android Platform Tools (ADB)

### **Step 1 — Download Android SDK Platform Tools**
Official download link:  
https://developer.android.com/studio/releases/platform-tools

![SDK platform tools](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image3.png)

---

### **Step 2 — Extract ZIP File**
Extract the folder and move it to:

```
C:\Windows\
```

![Extract folder](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image4.png)

---

### **Step 3 — Verify ADB Installation**

Run this in CMD:

```
adb version
```

![adb version check](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image5.png)

---

### ⚠️ **Fix ADB Not Recognized Error**

If you see:
```
'adb' is not recognized as an internal or external command...
```

Run:

```
set PATH=%PATH%;C:\Windows\platform-tools
```

Or manually navigate:

```
cd C:\Windows\platform-tools
```

![Error fix](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image6.png)

---

## Task 3: Setting Up Docker Android Simulator

### **Step 1 — Pull the Docker Image**
Repository link:  
https://github.com/budtmo/docker-android

![Pull repo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image9.png)

---

### **Step 2 — Verify Downloaded Images**

Run:

```
docker images
```

![docker images](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image10.png)

---

## Task 4: Running the Android Emulator Container

### **Step 1 — Start the Emulator Container**

Run this command:

```
docker run -d -p 6080:6080 -p 5555:5555 -e EMULATOR_DEVICE="Samsung Galaxy S10" -e WEB_VNC=true --device /dev/kvm --name android-container budtmo/docker-android:emulator_11.0
```

![run container](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image11.png)

You can also monitor Docker Desktop:

![docker desktop](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image12.png)

---

### **Step 2 — Check Running Containers**

```
docker ps
```

![docker ps](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image13.png)

---

## Task 5: Accessing the Web Interface

### **Step 1 — Open in Browser**

Go to:  
http://localhost:6080/

### **Step 2 — Click "Connect"**

![Emulator UI](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image14.png)

Interact with the emulator:

![Interact](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image15_interact.png)

---

### **Step 3 — View Emulator Logs**

```
docker logs android-container
```

![logs](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image16_logs.png)

---

## Task 6: Connecting ADB to Docker Emulator

### **Step 1 — Connect ADB**

```
adb connect localhost:5555
```

![adb connect](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image17_IH5555.png)

---

### **Step 2 — List ADB Devices**

```
adb devices
```

![adb devices](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image18_adb_devices.png)

---

### **Step 3 — Test ADB Connection**

```
adb shell getprop ro.build.version.release
```

### **Step 4 — List Installed Packages**

```
adb shell pm list package
```

---

## Task 7: Installing Android Apps in Emulator

### **Option 1 — Using APKPure via Emulator Browser**

![APKPpure InjuredAndroid](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image20_injured%20andriod.png)


---

### **Option 2 — Install Directly from GitHub**

#### **Step 1 — Visit Official Repo**
![injured android github](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image21_B3nac.png)

#### **Step 2 — Go to Latest Release**
![release page](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image22_b3nac.png)

#### **Step 3 — Download APK**
![download apk](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image23.png)

---

### **Step 4 — Install APK**

Check device:

```
adb devices
```

Install:

```
adb install InjuredAndroid-1.0.12-release.apk
```

If errors occur:

```
adb -s emulator-5554 install InjuredAndroid-1.0.12-release.apk
```

![install apk](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image25_commands.png)

Successful installation:

![installed](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image25_injuredapp.png)

---

## Task 8: Opening JADX-GUI & Accessing MANIFEST.XML

Open JADX-GUI:

![jadx gui](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image26_jadx.png)

Access the `AndroidManifest.xml` file:

![manifest xml](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/47651f0b4fb985e88bff4fd8f8589c2c82874d46/Android%20Mobile%20Application%20Security/Lab_images/Screenshot%20(23).png)

---

### ✔️ **End of Lab Setup Guide**
