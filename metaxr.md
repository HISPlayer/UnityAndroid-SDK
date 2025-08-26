# HISPlayer MetaXR Integration

## Requirements

#### Meta XR All-in-One version
- Minimal Meta XR All-in-One version: 60.0

#### Unity version
- Minimal Unity version: 2021.3.26f1

#### HISPlayer SDK version
- Minimal HISPlayer SDK version: 3.3.0

#### Supported Android Version
- Minor version - Android 10.0 ‘Quince Tart’
- Minimum SDK: 29

#### Supported Unity Color Space
- Linear

#### Target Architecture
- IL2CPP - ARM64

**Note**: If you plan to use **Meta XR SDK v74 or newer**, we recommend working with **Unity 2022.3 LTS or Unity 6+**.  
Older Unity versions may still work but are limited to the Oculus XR Plugin and won’t support new Meta XR features.

## Integrate Meta XR All-in-One SDK

Integrate HISPlayer SDK with the **[Meta XR All-in-One SDK](https://developer.oculus.com/downloads/package/meta-xr-sdk-all-in-one-upm/)**.

First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/) and open **Window > Package Manager > Packages: In Project** to check Meta XR All-in-One SDK is installed properly.

<p align="center">
<img width="605" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b4e362ba-f3d1-4d07-a46b-7a76e73d30fb">
</p>

Open **Edit > Player Settings > MetaXR**, select the Android platform and clik "**Select All**" and "**Apply All**" in order to set up all the Oculus settings. It is possible that during the remaining processes new errors and warnings may arise that need to be fixed again.

<p align="center">
<img width="90%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/691d9de5-3874-4b6a-bb1e-3b2981020590">
</p>

In older versions of the Meta XR SDK, this step automatically installed Oculus XR. However, starting with Meta XR SDK v74 and later, the choice of plugin is up to you. Meta’s support has shifted to focus on OpenXR, so you should decide which plugin fits your project.

## Which plugin should you choose, Oculus XR or OpenXR?

When setting up the Meta XR All-in-One SDK in Unity, you’ll be asked to pick one of two XR providers: Oculus XR Plugin or Unity OpenXR Plugin.
- **Oculus XR Plugin**: Meta’s older, Oculus-specific integration. Only recommended if you are working with Unity < 6 or the Meta XR SDK prior to version v74. 
- **Unity OpenXR Plugin**: Industry-standard OpenXR integration. Fully compatible with all new features of the Meta XR SDK (v74+). It also allows your app to run on other OpenXR-compliant platforms, not just Quest.

To install these plugins, open **Package Manage > Install Package by Name**, type *com.unity.xr.oculus* or *com.unity.xr.openxr* depending on which one best suits your application, and select install.

Go to **Project Settings → XR Plug-in Management** and make sure that the provider you’ve chosen (Oculus XR or OpenXR) is checked.
<img width="1255" height="943" alt="image" src="https://github.com/user-attachments/assets/6c2237d4-092a-46aa-9a73-c8f5202a1725" />

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [**Quickstart Guide**](./setup-guide.md).

## Import HISPlayer Meta XR Sample
Please, download the sample here: [**HISPlayer MetaXR 360 Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_MetaXR_360_Sample.unitypackage) (no need to download it if you have received it in the email). The sample is intended for playing 360 video. It's recommended to use this sample with OpenGL. If you need to use Vulkan to play high resolution video with Meta Quest devices, please [contact HISPlayer team](https://hisplayer.com/demo-unity-player-sdk-for-meta-quest/). 

Before using the sample, please make sure you have followed the above requirements to set-up your Unity project for Oculus and HISPlayer SDK. To use the sample, please follow these steps :
  - Set up the Meta XR All-in-One environment
  - Import HISPlayer SDK
  - Import HISPlayer Meta XR Sample 
  - Open Assets/HISPlayerOculusSample/Scenes/HISPlayerOculusSample
  - Input the license key through the Inspector Unity window: **StreamController GameObject > HISPlayerSample component > License Key**
  - Open File > Build Settings > Add Open Scenes
  - Build and Run

To check how to set up the SDK and API usage, please refer to Assets/HISPlayerOculusSample/Scripts/Sample/HISPlayerSample.cs and StreamController GameObject in the Editor.

To check more about the project explanation, please refer to Assets/HISPlayerOculusSample/README.pdf

## HISPlayer Oculus Controllers
<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d820d25f-a38b-4fa6-8bcc-8b7a8824125f">
</p>

## HISPlayer 360 Material
Unity provides ways to configure how you will display your video content on the 360 environment. Please, refer to the following Unity documentation to check what kind of settings you will need: [Unity Video Panoramic Tutorial](https://docs.unity3d.com/Manual/VideoPanoramic.html).

We provide a material to configure the options of your video so please, refer to **Assets/HISPlayerOculusSample/Resources/RenderTextures/Materials/HISPlayer_360_Material.material** to check the 360 settings.

In our sample we're using the following options: 

* **Mapping**: Latitude Longitude Layout
* **Image Type**: 360 Degrees
* **3D Layout**: None

<p align="center">
<img width="600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/4a1f1958-ed35-4283-9f54-dae66d43d24d">
</p>

### 180 Degrees Video Playback
For 180 degrees playback usage, please change the **Image Type** of the material (HISPlayer_360_Material.mat) to **180 Degrees**.

<p align="center">
  <img width="60%" alt="image" src="https://github.com/user-attachments/assets/7834b9fc-8bb5-42de-a40e-ce04a4984ed4">
</p>

## HISPlayer 360 Shader for Linear Color Space
If you are using **HISPlayer SDK version 3.4.0** and above, you will find **HISPlayer360Shader.shader** for 360 video playback in *Packages/com.hisplayer.hisplayersdk/HISPlayer/Scripts/Shaders/*.
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/e95a25a0-82ca-4c7b-b27b-e5ea3a84ae84">
</p>

HISPlayerOculusSample uses the default Unity Skybox/Panoramic shader, as explained in the [HISPlayer 360 Material](./metaxr.md#HISPlayer-360-Material).

If you use Linear Color Space in the Unity Project Settings > Player Settings > Other Settings > Rendering > Color Space, please change the default shader to HISPlayer360Shader which will improve the video rendering quality by following these steps : 
* Open Assets/HISPlayerOculusSample/Resources/RenderTextures/Materials/HISPlayer_360_Material.mat
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/2e32d3c3-86b9-4bc2-829a-e1750a8524ba">
</p>

* In the Inspector window, change Shader to HISPlayer360Shader
<p align="center">
  <img width="60%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/a981eb80-d2e6-4c99-8ba6-201d4ca615a9">
</p>

* Make sure you have the following setting of the material:
<p align="center">
  <img width="60%" alt="image" src="https://github.com/user-attachments/assets/23317c69-6f45-4075-a89d-83b66faae48b">
</p>

## Common Issues

### Meta Quest Store Android Target API Level 32 Requirement
HISPlayer SDK requires Android Target API Level 33, but Meta Quest Store requires Android Target API Level 32. To solve this, please download the updated custom Android gradle files from the following links depending on your Unity version:
- [Unity 6](https://downloads.hisplayer.com/Unity/Resources/Android32_Unity6.zip)
- [Unity 2022](https://downloads.hisplayer.com/Unity/Resources/Android32.zip)
- [Unity 2021 & 2020](https://downloads.hisplayer.com/Unity/Resources/Android32_Unity2020_2021.zip)

Please follow these steps after downloading the zip file:
- Extract the zip file. It contains **gradleTemplate.properties**, **launcherTemplate.gradle** and **mainTemplate.gradle**.
- Copy the 3 files above to your **UnityProject\Assets\Plugins\Android\...** This will replace the old files.
- Build and run your project again.

If you see the following errors and warning in HISPlayerSettings after copying the new files, you can ignore it.
<p align="center">
  <img width="40%" alt="image" src="https://github.com/user-attachments/assets/10591651-e27d-4d06-ba08-1280c10fd964">
</p>

### Disable Multithreaded Rendering Requirement

<img width="594" height="197" alt="image" src="https://github.com/user-attachments/assets/33d65cfa-623f-4526-b014-6a19234229bb" />

### Vertically Inverted Video Issue

If you face an issue where the video is vertically inverted or rendered upside down, please follow 1 of these 2 approaches: 
* Approach 1 (Recommended): Use **HISPlayer360Shader.shader** and attach it to the material as explained in the previous section. Make sure that the **Flip Vertically** option is enabled.

<p align="center">
  <img width="60%" alt="image" src="https://github.com/user-attachments/assets/3102cf49-0598-4914-8a54-ef00443853d5">
</p>

* Approach 2: Set **FlipTextureVertically** of the StreamProperties to **true** before calling SetUpPlayer() in your project script. This API will flip the texture vertically. This API will work only for Android and Meta Quest devices, it will not have effect in the Unity editor. For example:
    ```
    // Flip texture vertically to render the texture correctly for Skybox material.
    multiStreamProperties[0].FlipTextureVertically = true;
    SetUpPlayer();
    ```
Please don't mix both approaches, otherwise the video will be veritcally inverted.
