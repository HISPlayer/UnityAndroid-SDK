# Oculus Integration

It is possible to integrate HISPlayer SDK with the Oculus environment. 

The **Meta XR All-in-One SDK** is available since November 13th, 2023, but in this tutorial we will explain how to use the old [OculusIntegration.unitypackage](https://developer.oculus.com/downloads/package/unity-integration/). 

First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/). In the **Step 4. Import Meta XR All-in-One SDK from the Unity Asset Store**, please, import the Oculus Integration package instead and accept all the pop-ups in order to config properly the SDK.

- **Assets > Import Package > Custom Package > OculusIntegration.unitypackage**

<p align="center">
<img width="800" alt="Step 1" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e20e9b45-9ec5-44b8-8d73-78d22f58275f">
</p>

## Requirements

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

## Import HISPlayer Oculus Sample
Please, download the sample here -> [**HISPlayer Oculus 360 Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Oculus_360_Sample.unitypackage) (no need to download it if you have received it in the email).

Before using the sample, please make sure you have followed the above requirements to set-up your Unity project for Oculus and HISPlayer SDK. To use the sample, please follow these steps :
  - Import Oculus Integration SDK
  - Set up the Oculus environment
  - Import HISPlayer SDK
  - Import HISPlayer Oculus 360 Sample
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
