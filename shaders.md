# Custom Shaders for Linear Color Space
Unity allows you to create [Custom Shaders](https://docs.unity3d.com/Manual/Shaders.html) to improve and generate your own materials 
and graphics. 

We provide examples that simulate the Gamma color space even if you are using Linear color space. The color space plays an important role when rendering the scene and there are differences between Gamma and Linear color spaces 
(refer to this [Unity Manual](https://docs.unity3d.com/Manual/LinearRendering-LinearOrGammaWorkflow.html))
 
If you follow the [Import Sample](https://hisplayer.github.io/UnityAndroid-SDK/#/import-sample) section, please, refer to the GameObject **ScreenRawImage** and check the **Raw Image** component. You
will see there is a material attach to the **material** attribute named **HISPlayerDefaultMaterialRawImage**.

<p align="center">
<img width = "600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/c778aed8-b818-47e2-8d60-8e688aab40c0">
</p>

This material is using the custom shader **HISPlayer/HISPlayerDefaultShaderRawImage**. 
For more details, you can check the following folders and files:

- **Packages/HISPlayerSDK/HisPlayer/Scripts/Shaders/** - Here you can find the custom shaders. These files contain the code to simulate the Gamma color space when using Linear color space.
  - **HISPlayerDefaultShader.shader**
  - **HISPlayerDefaultShaderRawImage.shader**

<p align="center">
<img width = "600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/2df21e45-cac0-4acc-8617-0ea460c29518">
</p>

- **Packages/HISPlayerSDK/HisPlayer/Resources/Materials/** - Here you can find 3 different Unity materials:
  - **HISPlayerDefaultMaterial.mat**: It uses the **HISPlayerDefaultShader.shader** and can be used for the HISPlayer RenderMode “Material”.
  - **HISPlayerDefaultMaterialRawImage.mat**: It uses the **HISPlayerDefaultShaderRawImage.shader** and can be used attaching the material to the material attribute of the RawImage component.
  - **HISPlayerDefaultMaterialRenderTexture.mat**: It uses the HISPlayerDefaultShader.shader and the HISPlayerDefaultRenderTexture.renderTexture.

<p align="center">
<img width = "600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/962fd08d-c31e-4b74-9d14-23d11bf5b458">
</p>

- **Packages/HISPlayerSDK/HisPlayer/Resources/RenderTextures/**
  - **HISPlayerDefaultRenderTexture.renderTexture** - This file is a custom RenderTexture to be used with the **HISPlayerDefaultMaterialRenderTexture.mat**.

## HISPlayer 360 Shader for 360 Video Playback
If you are using **HISPlayer SDK version 3.4.0** and above, you will find **HISPlayer360Shader.shader** in *Packages/com.hisplayer.hisplayersdk/HISPlayer/Scripts/Shaders/*.
<p align="center">
  <img width="70%" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/e95a25a0-82ca-4c7b-b27b-e5ea3a84ae84">
</p>

When building 360 application, you might use different shaders such as the Unity Skybox/Panoramic shader.

If you use Linear Color Space, please change the default shader to HISPlayer360Shader which will improve the video rendering quality by following these steps : 
* Open your 360 material, for example: Assets/HISPlayerOculusSample/Resources/RenderTextures/Materials/HISPlayer_360_Material.mat
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


## Vertically Inverted Video Issue

If you face an issue where the video is vertically inverted or rendered upside down, please follow below approach: 
* Use **HISPlayer360Shader.shader** and attach it to the material as explained in the previous section. Make sure that the **Flip Vertically** option is enabled.

<p align="center">
  <img width="60%" alt="image" src="https://github.com/user-attachments/assets/3102cf49-0598-4914-8a54-ef00443853d5">
</p>
