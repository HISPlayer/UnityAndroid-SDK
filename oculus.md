# Oculus / Meta Quest Set Up Guide
It is possible to integrate HISPlayer SDK with the Oculus environment.
First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/). 

## Requirements

It's necessary to install the [Oculus XRPlugin](https://developer.oculus.com/documentation/unity/unity-xr-plugin/) and 
import the [OculusIntegration.unitypackage](https://developer.oculus.com/downloads/package/unity-integration/). 

- **Assets > Import Package > Custom Package > OculusIntegration.unitypackage**

#### Supported Android Version
- Minor version - Android 10.0 ‘Quince Tart’
- Minimum SDK: 29

#### Supported Unity Color Space
- Linear

#### Target Architecture
- IL2CPP - ARM64

#### Oculus platform
In XR Plug-in Management, please make sure that you have the **Oculus** option checked. Otherwise, when you run the application, it will show a 2D window without XR environment.
  
  - **Edit > Project Settings > XR Plug-in Management**

<img width="1040" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/beb2689c-d884-495c-9fa4-07b70014dfed">

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [Quickstart Guide](./setup-guide.md).

## Import HISPlayer Oculus Sample
Please, download the sample here -> [**HISPlayer Oculus 360 Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Oculus_360_Sample.unitypackage) (no need to download it if you have received it in the email).

Before using the sample, please make sure you have followed the above requirements to set-up your Unity project for Oculus, and HISPlayer SDK has been imported. To use the sample, please follow these steps :
  - Import HISPlayer Oculus Sample package
  - Open Assets/HISPlayerOculusSample/Scenes/HISPlayerOculusSample
  - Input the license key through the Inspector Window. StreamController game object > HISPlayerSample component > License Key
  - Open File > Build Settings > Add Open Scenes
  - Build and Run

To check how to set up the SDK and API usage, please refer to Assets/HISPlayerOculusSample/Scripts/Sample/HISPlayerSample.cs and StreamController game object in the Editor.

To check more about the project explanation, please refer to Assets/HISPlayerOculusSample/README.pdf
