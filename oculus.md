# Oculus Set Up Guide
It is possible to integrate HISPlayer SDK with the Oculus environment.
Please, follow this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/) for adding the Oculus SDK to your Oculus project.

## Requirements

It's necessary to install the [Oculus XRPlugin](https://developer.oculus.com/documentation/unity/unity-xr-plugin/) and 
import the [OculusIntegration.unitypackage](https://developer.oculus.com/downloads/package/unity-integration/). 

- **Assets > Import Package > Cusstom Package > OculusIntegration.unitypackage**

#### Supported Android Version
|Minor version - Android 10.0 ‘Quince Tart’ | Minimum SDK: 29|
|-|-|

#### Supported Unity Color Space
- Linear

#### Target Architecture
- IL2CPP - ARM64

#### Oculus platform
  For making the project works on the Oculus device, please, make sure you have the **Oculus** option checked. 
  Otherwise, when you run the application, it will show a 2D window with no VR.
  
  - **Edit > Project Settings > XR Plug-in Management**

<img width="1040" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/beb2689c-d884-495c-9fa4-07b70014dfed">

## HISPlayer SDK
In the case you didn't have imported HISPlayer SDK yet, please, follow the [Set UP Guide](./setup-guide.md) so you will be able to use our SDK.
