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



NOTE: incase the **`'adb' is not recognized as an internal or external command, operable programs or barch file`** error is encountered, you can simply run this command on the cmd : **`set PATH=%PATH%;C:\Windows\platform-tools`**
alternatively:
Change the directory to the directory of the platform tools:

![Error_message_correction](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image6.png)


Task 3: Setting Up Docker Android Simulator:
step1: pull the image docker from https://github.com/budtmo/docker-android
![pull_repo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image9.png)

step2: use the `docker images` command on the cmd to verify the image:
![Error_message_correction](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image10.png)

Task 4: Running the Android Emulator Container
step1: create and start the container by using this command on the command prompt:
`docker run -d -p 6080:6080 -p 5555:5555 -e EMULATOR_DEVICE="Samsung Galaxy S10" -e WEB_VNC=true --device /dev/kvm --name android-container budtmo/docker-android:emulator_11.0`

![run a container](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image11.png)
also you can check docker desktop to check if the container is running (docker desktop should be open throughout this Lab)
![docker info](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image12.png)

step2: check if the container is running using the command: `docker ps`

![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image13.png)

Task 5: Accessing the wen interface of the Andriod Emulator:
step 1: open this link with a browser: http://localhost:6080/
step 2: CClick on Connect to connect the docker
step3: the Android Emulator interface runs:

![android emulator](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image14.png)

Interact with the android emulator and explore the apps:
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image15_interact.png)

step 4: Use the `docker logs android-container` command to check emulator logs
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image16_logs.png)

Task 6: Bridging ADB from windows host to docker container:
step 1: connect to ADB the containerised emulator with this command: 
`adb connect localhost:5555`
![image17](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image17_IH5555.png)
setp2: verify the connection using the command `adb devices`
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image18_adb_devices.png)
step3: Test ADB Connection using the command `adb shell getprop ro.build.version.release`
step 4: list installed packages using command `adb shell pm list package`

Task 7 : Installing android apps in the emulator
step 1: Using APK pure. Navigate using the emulator on the browser
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image20_injured andriod.png)
Alternatively: 
Step 1: search for injured android app and click on the first legitimate gitnhub account:
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image21_B3nac.png)

step2: Click on the latest release of the android apk on the bottom right of the page: 
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image22_b3nac.png)

step3: Scroll to the buttom of the page and click on the apk file to downlead:
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image23.png)

step4: installing injuredAndroid apk. Check adb devices using the command `adb devices`
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image24_adb_install.png)

step 5: use this command incase of possible error: `adb -s emulator-5554 install InjuredAndroid-1.0.12-release.apk` else use `adb install InjuredAndroid-1.0.12-release.apk`

![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image25_commands.png)

the Injured Andriod app is successfully installed:
![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image25_injuredapp.png)

Task 8 Openeing JADX-GUI and ensuring access the MANIFEST.XML

![docker_ifo](https://raw.githubusercontent.com/D-rank-developer/Computer-and-Operating-Systems-Security/2da1ac53f384c2bab09b273a742c5003b51287fd/Android%20Mobile%20Application%20Security/Lab_images/image26_jadx.png)

step2: Having access to MANIFEST.XML file.
![dockerf](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/47651f0b4fb985e88bff4fd8f8589c2c82874d46/Android%20Mobile%20Application%20Security/Lab_images/Screenshot%20(23).png)
