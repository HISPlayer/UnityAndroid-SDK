# HISPlayer MetaXR 360 Sample

## Integrate Meta XR All-in-One SDK

Integrate HISPlayer SDK with the **[Meta XR All-in-One SDK](https://developer.oculus.com/downloads/package/meta-xr-sdk-all-in-one-upm/)**.

First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/) and open **Window > Package Manager > Packages: In Project** to check Meta XR All-in-One SDK is installed properly.

<p align="center">
<img width="605" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b4e362ba-f3d1-4d07-a46b-7a76e73d30fb">
</p>

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

#### Oculus platform
Open **Edit > Player Settings > Oculus**, select the Android platform and clik "**Select All**" and "**Apply All**" in order to set up all the Oculus settings. 

<p align="center">
<img width="600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/4a907bcb-4689-4ad3-b4c1-7c53478a07fb">
</p>

In XR Plug-in Management, please make sure that you have the **Oculus** option checked. Otherwise, when you run the application, it will show a 2D window without XR environment.
  
  - **Edit > Project Settings > XR Plug-in Management**

<img width="1040" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/beb2689c-d884-495c-9fa4-07b70014dfed">

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](./setup-guide.md).

## Import HISPlayer Meta XR Sample
Please, download the sample here: [**HISPlayer MetaXR 360 Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_MetaXR_360_Sample.unitypackage) (no need to download it if you have received it in the email).

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
