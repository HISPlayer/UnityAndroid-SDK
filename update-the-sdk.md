# Update the SDK

Through this guide, you will be introduced how to update the SDK if you already have installed the SDK previously.

## Remove Old Package

Remove the previous HISPlayer Android / iOS SDK package from Unity Package Manager

**Window > Package Manager > Packages - HISPlayer > HISPlayer Android IOS SDK > Remove**

<p align="center">
<img width="700" src="./assets/remove-package.PNG">
</p>

<br>

## Import New package

Importing the new package is the same as importing other normal packages in Unity. 
Select the package of HISPlayer SDK and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK_Android_iOS unity package**


<p align="center">
<img width="450" src="./assets/import-package.png">
</p>

<br>

## Configure Unity for Android

Open the window HISPlayer located in the upper side of the screen.

<p align="center">
<img width="550" src="./assets/configure-unity.png">
</p>

<p align="center">
<img width="400" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/add6d0c9-19c0-4a6c-8b81-a0c935ab8e1c">
</p>

By selecting Android target 33, Unity is going to ask you to update (in the case you don't have the SDK 33 installed). Please, press "Update Android SDK" button.

<p align="center">
<img width="292" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d4cfb0b6-5d5f-4233-bd42-b454ae64925e">
</p>


## Update License Key
Input the license key that is associated with the SDK through HISPlayer properties. If the license key is not valid, the player won't work and will throw an error message.

<p align="center">
<img width="400" src="./assets/license-key.PNG">
</p>
