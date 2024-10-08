# Update the SDK

Through this guide, you will be introduced how to update the SDK if you already have installed the SDK previously. Please, restart the Editor before continuing.

## Remove Old Package

Remove the previous HISPlayer SDK package from Unity Package Manager.

**Window > Package Manager > Packages - HISPlayer > HISPlayer SDK > Remove**

<p align="center">
  <img width="793" alt="Remove" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/00071022-a78b-4b36-bd1d-eaf64aad49fc">
</p>

<br>

## Import New package

Importing the new package is the same as importing other normal packages in Unity. 
Select the package of HISPlayer SDK and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK.unitypackage**

<p align="center">
<img width="450" src="./assets/import-package.png">
</p>

<br>

## Configure Unity for Android

Open the window **Tools > HISPlayer** located in the upper side of the screen > Click on Player Settings Configuration > Select **Build Target to Android** > Set all the required settings.

<p align="center">
<img width="550" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b3203548-b0c3-46c9-ae74-dded00c5915a">
</p>

<p align="center">
<img width="400" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/020bb6bb-fbc4-47b4-9503-347908f64254">
</p>

By selecting Android target 33, Unity is going to ask you to update (in the case you don't have the SDK 33 installed). Please, press "Update Android SDK" button.

<p align="center">
<img width="292" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d4cfb0b6-5d5f-4233-bd42-b454ae64925e">
</p>


## Update License Key
If you received a license key from HISPlayer, please input the license key in the License Key field.

<p align="center">
<img width=70% alt="image" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/50b10c75-c6e0-438d-ba1f-da6e66d51eed">
</p>

If the license key is not valid, the player won’t work and will throw an error message. License key is not required for Unity Editor usage.

## Check Material and Shader
After updating the SDK, check whether you have a shader error that is attached to the material. For example as image below:

<p align="center">
<img alt="image" src="https://github.com/user-attachments/assets/af33ab33-b2e0-4056-bb5f-58752250a766">
</p>

If you have this issue, please re-attach the correct shader to the material.

<p align="center">
<img width="50%" alt="image" src="https://github.com/user-attachments/assets/d1f6783f-831a-402c-b992-b991c0b2013f">
</p>


