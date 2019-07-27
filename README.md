# Quasar-Cordova-Apk
Simple guide to create a signed apk from a Quasar app with Cordova.

## Technologies
- Quasar v1
- Cordova
- JDK

### Run the following commands in the root folder of your app

Install cordova dependencies
```batch
quasar mode add cordova
```
Change to cordova folder
```batch
cd src-cordova
```
Install Android platform
```batch
cordova platform add android
```
Go back to the root folder
```batch
cd..
```
Build your app
```batch
quasar build -m cordova -T android
```
Change to cordova folder again
```batch
cd src-cordova
```
Build the apk
```batch
cordova build android
```

### Run the following commands with a CMD for better compatibility

Change to the apk release folder.
```batch
cd "<ROOT-FOLDER>\src-cordova\platforms\android\app\build\outputs\apk\release\"
```
To create a keystore, you have to inform the password and answer all the questions.

I've called mine MY_KEYSTORE. 

JDK 1.8.0_171 is the version installed in my PC.
```batch
"C:\Program Files\Java\jdk1.8.0_171\bin\keytool.exe" -genkey -v -keystore MY_KEYSTORE.keystore -alias MY_KEYSTORE -keyalg RSA -keysize 2048 -validity 20000
```
- Finally, run this command, inform the keystore password and the apk will be signed.
```batch
"C:\Program Files\Java\jdk1.8.0_171\bin\jarsigner.exe" -tsa http://timestamp.digicert.com -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore MY_KEYSTORE.keystore app-release-unsigned.apk MY_KEYSTORE
```
### Good Job
Your apk is ready to be installed in your device.
Enjoy!



