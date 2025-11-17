Task 1: Installing JADX-GUI (Windows)

Step1: Install Java, JADX needs to run on Java Runtime Environment  (https://www.java.com/en/)
![Installation Page](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image1.png)
Step2: Download JADX-GUI from github view various releases and and download the .exe file: https://github.com/skylot/jadx/releases/tag/v1.2.0
![Dowload JADX installation file](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image2.png)

Task 2: Installing Android Platform Tools (ADB) on Windows
step1: Download Andriod SDK platform tools. click here to download: https://developer.android.com/studio/releases/platform-tools
![SDK platform tools](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image3.png)

step2: Extract the zip file and save the entire folder under C:\Windows.
![SDK platform tools](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image4.png)

step3: Check for access to adb tools using command `adb version` on the cmd.
![SDK platform tools](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image5.png)

NOTE: incase the `'adb' is not recognized as an internal or external command, operable programs or barch file` error is encountered, you can simply run this command on the cmd : `set PATH=%PATH%;C:\Windows\platform-tools`



