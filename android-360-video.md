# 360 Video on Android devices
It is possible to integrate HISPlayer SDK with 360 videos in mobile devices. In the case of using Oculus devices, please refer to this section
[**Oculus Set Up Guide**](https://hisplayer.github.io/UnityAndroid-SDK/#/oculus) before continuing with this guide.

Please, download the sample here -> [**HISPlayer Android 360 Sample**](TODO:ADD_THE_URL_HERE) (no need to download it if you have received it in the email).

## Import HISPlayer Sample
Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Android_360_Sample.unitypackage**

<p align="center">
<img src="./assets/import-package.png">
</p>

- Complete the configuration for Android ->  [**Configure Unity for Android**](./setup-guide.md#12-configure-unity-for-android)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayer360Sample.unity**

<p align="center">
<img width="470" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/beeebd0e-7b88-4f8d-acc5-e8ea4c37c25e">
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector Window. **StreamController** game object -> **HISPlayerSample** component -> **License Key**

<p align="center">
<img src="./assets/license-key.PNG">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
<img width="700" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e56658fc-4483-4cb3-9f19-563dc91b770b">
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerSample.cs** and **StreamController GameObject** in the Editor.

## UI Demo
The UI components in the sample scene are fully modifiable. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features
such as play, pause, seek, etc.

<p align="center">
<img src="./assets/android-ios-uicomponent.PNG">
</p>

### How to display a 360 video
To display a 360 environment, set the Main Camera **Clear Flag** field to **Skybox**.

<p align="center">
  <img width="424" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/6d60c24c-ce80-453f-bc18-3a05e7173224">
</p>

Use a **Render Texture** attach to a **Unity Material** with the shader **Skybox/Panoramic**. You can check: 

- **Assets/HISPlayerSample/Resources/HISPlayer_360_Material.mat**
- **Assets/HISPlayerSample/Resources/HISPlayer_360_RenderTexture.renderTexture**

<p align="center">
  <img width="504" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/c57d15b8-9468-4cb1-be12-a054ee169f12">
  <img width="425" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/2dd0131f-4bcd-4e21-b353-4da7d156f710">
</p>

Open **Window** > **Rendering** > **Lighting** > **Environment** and attach the **Material** to the **Skybox Material** in the Lighting configuration. 

<p align="center">
  <img width="611" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d6c8edcd-041f-47f4-aaa1-be5356ff061b">
</p>

Select **Render Mode** > **Render Texture** and attach the previous **Render Texture** to the **StreamController Render Texture** field

<p align="center">
  <img width="413" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/fd033f25-8c58-4d84-a56c-88357e5684da">
</p>

### How to use the Android Gyroscope
The Gyroscope is a typical Android sensor used for different cases. We're using the gyroscope to control the camera of the demo. If you are using Oculus devices, 
this step can be skip, since Oculus is controlling the camera by itself.

To check how to use the Gyroscope, please refer to **Assets/HISPlayerSample/Scripts/GyroscopeController.cs** and **Main Camera GameObject** in the Editor. 

