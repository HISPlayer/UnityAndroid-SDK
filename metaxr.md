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

First, please configure the Unity project for Oculus by following this [Tutorial](https://developer.oculus.com/documentation/unity/unity-tutorial-hello-vr/) and open `Window > Package Manager > Packages: In Project` to check Meta XR All-in-One SDK is installed properly.

<p align="center">
  <img width="605" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b4e362ba-f3d1-4d07-a46b-7a76e73d30fb">
</p>

In older versions of the Meta XR SDK, this step automatically installed Oculus XR Plugin. However, starting with Meta XR SDK v74 and later, the choice of plugin is up to you. Meta’s support has shifted to focus on OpenXR Plugin, but is recommended to use **Oculus XR Plugin** for best compatibility.

## Import Oculus XR Plugin

To install these plugin, open `Package Manage > Install Package by Name`, type *com.unity.xr.oculus* and select install.

<p align="center">
  <img width="469" height="99" alt="image" src="https://github.com/user-attachments/assets/fe2b17de-a500-476d-a7b7-cf93d8e6119e" />
</p>

Go to **Project Settings → XR Plug-in Management** and make sure that the provider Oculus is checked.
<p align="center">
  <img width="1250" height="565" alt="image" src="https://github.com/user-attachments/assets/5ec3a3c3-cd08-4e69-afba-efc4c706b68c" />
</p>

## Import HISPlayer SDK
If you have not imported HISPlayer SDK yet, please follow the [**Quickstart Guide**](./setup-guide.md).

## Import HISPlayer Meta XR Sample
Please, download the sample here: [**HISPlayer MetaXR Sample**](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_MetaXR_Sample.unitypackage) (no need to download it if you have received it in the email).

This updated sample includes multiple scenes designed for different video types:
  - **360° Scene:** for immersive 360-degree video playback.
  - **180° Stereoscopic Scene:** for 3D/VR180 stereoscopic video playback.
  - **Standard Video Scene:** for regular flat video playback.

It is recommended to use OpenGL for best compatibility. If you need to use Vulkan for playing high-resolution video on Meta Quest devices, please [contact HISPlayer team](https://hisplayer.com/demo-unity-player-sdk-for-meta-quest/). 

## Set-Up the Sample

Before using the sample, make sure you have completed all the required setup steps described above — including importing all necessary packages and dependencies for Oculus and the HISPlayer SDK.

Follow these steps to configure and run the sample properly:

**1. Enable the New Input System**

Unity versions starting with 6000 use the Input System Package (New) by default. To verify this, go to: `Edit > Project Settings > Player > Other Settings > Active Input Handling` If you are using Input Manager (Old) or Both, change it to **Input System Package (New).**

<p align="center">
  <img width="843" height="143" alt="image" src="https://github.com/user-attachments/assets/813cc63d-284e-4960-bbe9-de582617c89b" />
</p>

**2. Switch the Platform to Android**

Go to `File > Build Profiles > Android > Switch Platform`

**3. Run the Meta XR Project Setup Tool**

Navigate to `Meta XR Tools > Project Setup Tool`. Click **Fix All** Outstanding Issues and **Apply All** Recommended Items.

**Note:** You can safely ignore the message:
“Beginning with v74, it is recommended to use the OpenXR plugin instead of the OculusXR plugin.”

**4. Configure HISPlayer Settings**

Go to `Tools > HISPlayer > Player Settings Configuration`
Click **Fix All**, but do not enable “Set Multithreaded Rendering to Disable”.

**Note:** The Meta XR Project Setup Tool may show “Target API should be set to 32 to ensure the latest supported version.” This can be ignored or refer to the [Common Issues section](#common-issues).

**5. Configure Graphics API**

Go to `Player Settings > Other Settings > Auto Graphics API` and disable it. **Keep OpenGLES3** only and remove Vulkan.

**6. Open a Scene**

Open one of the three scenes located in `Assets/HISPlayerVRSample/Scenes/`. When opening a scene, a prompt may appear to **import TMP Essentials.**

<p align="center">
  <img width="1024" height="381" alt="image" src="https://github.com/user-attachments/assets/7c23779f-e457-427c-83a2-8b1e70763477" />
</p>

If it does not appear automatically, go to `Window > TextMeshPro > Import TMP Essential Resources`

**7. Enter License Key (if required)**

In the Inspector Window, select `StreamController GameObject → HISPlayerVRController component → License Key`. Enter your provided HISPlayer license key.

**8. Add the Scene to Build List**

Go to `File > Build Profiles > Scene List` and add the selected scene as the first in the list.

**9. Select the Target Device** 

Go to `Build Profiles > Android > Run Device` and select your connected device.

**10. Build the Project**

Choose Build or Build and Run. A warning may appear saying “Disable Multithreaded”. Click **Continue** and ignore it.

<p align="center">
  <img width="593" height="198" alt="image" src="https://github.com/user-attachments/assets/8f9ff15e-158a-49dc-a15e-10ca86731503" />
</p>

## HISPlayer Scenes Overview

This sample includes three different scenes, each demonstrating a different playback configuration: **Standard VR**, **180° Stereoscopic**, and **360°**.

### HISPlayer VR Scene

**Video Rendering:** The video is rendered to the `Screen` GameObject.

**Material Used:** `Assets/HISPlayerVRSample/Resources/Materials/HISPlayerVRMaterial.mat`

**Material Settings:**  
1. Click on `HISPlayerVRMaterial.mat` and check the **Inspector** window.  
2. Shader: `HISPlayer/HISPlayerDefaultShader`

<p align="center">
  <img width="917" height="375" alt="image" src="https://github.com/user-attachments/assets/fd991e75-f6e4-4c0d-81bc-499e670a2bd5" />
</p>

**Setting HISPlayer Stream Properties:**  
- In the **Hierarchy Window**, select `StreamController`  
- Then go to the **Inspector Window** → `HISPlayerVRController (Script)` → **MultiStream Properties**  
  - **Render Mode:** `Material`  
  - **Material:** `HISPlayerVRMaterial.mat`  
  - **URL:** A default URL is provided, but you can modify it to test your own stream.

<p align="center">
  <img width="823" height="589" alt="image" src="https://github.com/user-attachments/assets/723b7bb9-c8b1-4b19-b873-aaed47140d5d" />
</p>

### HISPlayer VR 180° Stereoscopic Scene

**Video Rendering:**  
The video is rendered to the **Unity Skybox**.

**Material Used:**  
`Assets/HISPlayerVRSample/Resources/Materials/HISPlayerVR180StereoscopicMaterial.mat`

**Material Settings:**  
1. Click on `HISPlayerVR180StereoscopicMaterial.mat` and check the **Inspector** window.  
2. Shader: `HISPlayer/HISPlayer360Shader`  
3. Image Type: `180 Degrees`  
4. 3D Layout: `Side by Side`  
5. Render Queue: `2501`

<p align="center">
  <img width="736" height="517" alt="image" src="https://github.com/user-attachments/assets/5116d627-4d3f-440c-a995-d5cb00a8c923" />
</p>

**Setting HISPlayer Stream Properties:**  
- In the **Hierarchy Window**, select:  
  `StreamController`  
- Then go to the **Inspector Window** → `HISPlayerVRController (Script)` → **MultiStream Properties**  
  - **Render Mode:** `Material`  
  - **Material:** `HISPlayerVR180StereoscopicMaterial.mat`  
  - **URL:** A default URL is provided, but you can modify it to test your own stream.

<p align="center">
  <img width="849" height="614" alt="image" src="https://github.com/user-attachments/assets/cddc2171-07ee-4d6e-bf5f-51440f3ab446" />
</p>

### HISPlayer VR 360° Scene

**Video Rendering:**  
The video is rendered to the **Unity Skybox**.

**Material Used:**  
`Assets/HISPlayerVRSample/Resources/Materials/HISPlayerVR360Material.mat`

**Material Settings:**  
1. Click on `HISPlayerVR360Material.mat` and check the **Inspector** window.  
2. Shader: `HISPlayer/HISPlayer360Shader`  
3. Image Type: `360 Degrees`  
4. 3D Layout: `None`  
5. Render Queue: `2501`

<p align="center">
  <img width="742" height="500" alt="image" src="https://github.com/user-attachments/assets/7ecc36ad-f624-40fc-be7c-bac108139fcd" />
</p>

**Setting HISPlayer Stream Properties:**  
- In the **Hierarchy Window**, select:  
  `StreamController`  
- Then go to the **Inspector Window** → `HISPlayerVRController (Script)` → **MultiStream Properties**  
  - **Render Mode:** `Material`  
  - **Material:** `HISPlayerVR360Material.mat`  
  - **URL:** A default URL is provided, but you can modify it to test your own stream.

<p align="center">
  <img width="778" height="566" alt="image" src="https://github.com/user-attachments/assets/cbff7849-99a4-4237-b79b-31816e1854e4" />
</p>

## HISPlayer Oculus Controllers
<p align="center">
  <img width="100%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d820d25f-a38b-4fa6-8bcc-8b7a8824125f">
</p>

## HISPlayer 360 Shader for Linear Color Space
If you are using **HISPlayer SDK version 3.4.0** and above, you will find **HISPlayer360Shader.shader** for 360 video playback in *Packages/com.hisplayer.hisplayersdk/HISPlayer/Scripts/Shaders/*.
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/e95a25a0-82ca-4c7b-b27b-e5ea3a84ae84">
</p>

HISPlayerVRSample uses the default Unity Skybox/Panoramic shader, as explained in the [HISPlayer 360 Material](./metaxr.md#HISPlayer-360-Material).

If you use Linear Color Space in the Unity Project Settings > Player Settings > Other Settings > Rendering > Color Space, please change the default shader to HISPlayer360Shader which will improve the video rendering quality by following these steps : 
* Open Assets/HISPlayerVRSample/Resources/RenderTextures/Materials/HISPlayer_360_Material.mat
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

There is a conflict between the recommended configuration of the HISPlayer SDK, which asks you to disable Multithreading, and the Meta XR SDK, which asks you to enable it. HISPlayer requires this to avoid certain issues with some Android devices, specifically mobile phones. Therefore, it is recommended to enable it as required for Meta Quest usage and ignore the HISPlayer warning.
<p align="center">
  <img width="597" height="122" alt="image" src="https://github.com/user-attachments/assets/9868dc07-209c-49ae-a44f-d3f32a176a4e" />
  <img width="590" height="192" alt="image" src="https://github.com/user-attachments/assets/2853424d-44ea-4b5d-b456-ac47b51391f3" />
</p>

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
