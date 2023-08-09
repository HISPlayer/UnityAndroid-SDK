# Import HISPlayer Sample
Please, download the sample here -> [**HISPlayer Android & iOS Sample**](https://downloads.hisplayer.com/Unity/Android_iOS/HISPlayer_Android_iOS_Sample.unitypackage)

Importing the package is the same as importing other normal packages in Unity. Select the downloaded package and import it.

- **Assets > Import Package > Custom Package > HISPlayer_Android_iOS_Sample.unitypackage**

<p align="center">
<img src="./assets/import-package.png">
</p>

- Complete the configuration for Android ->  [**Configure Unity for Android**](./setup-guide.md#12-configure-unity-for-android)

- Open the scene **Assets/HISPlayerSample/Scenes/HISPlayerSample.unity**

<p align="center">
<img src="./assets/android-ios-scene.PNG" width=50%>
</p>

- Import TextMesh Pro Essential

- Input the license key through the Inspector Window. **StreamController** game object -> **HISPlayerSample** component -> **License Key**

<p align="center">
<img src="./assets/license-key.PNG">
</p>

- Open **File** > **Build Settings** > **Add Open Scenes**

<p align="center">
<img src="./assets/android-buildsetting.PNG" width=80%>
</p>

- Build and Run

To check how to set up the SDK and API usage, please refer to **Assets/HISPlayerSample/Scripts/HISPlayerSample.cs** and **StreamController GameObject** in the Editor.

## UI Demo
The UI components in the sample scene are fully modifiable. The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate features such as play, pause, seek, etc.

<p align="center">
<img src="./assets/android-ios-uicomponent.PNG">
</p>

<p align="center">
<img src="./assets/android-ios-sampleui.PNG" width=70%>
</p>