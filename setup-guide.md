# QuickStart Guide
Getting started with HISPlayer consists of implementing the following steps:

1. Import and configure package   

      1.1. Import package
 
      1.2. Configure Unity for Android
   
2. Create your own sample
   
    2.1 Setup HISPlayer Manager
   
    2.2 Attach Unity Resources
   
    2.3 Configure HISPlayer Properties

    2.4 Build and Run

It's also possible to import the [HISPlayer Sample](https://hisplayer.github.io/UnitySamples/#/hisplayer-sample) after completing step 1. The sample is a comprehensive example scene using the HISPlayerSDK to help demonstrate features like play, pause, seek, etc.

## 1.1 Import package

### HISPlayer SDK versions 3.4.0 and above

The _HISPlayer Sample_ is included in the _HISPlayer SDK Unity Package_.

Importing the package is the same as importing other normal packages in Unity. 
Select the package of _HISPlayer SDK_ and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK unity package**

Refer to [Import HISPlayer Sample](https://hisplayer.github.io/UnitySamples/#/hisplayer-sample) to know more about the HISPlayer Sample.

<p align="center">
<img width=70% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/c8ff9e55-524e-48f1-a323-95b00aa5c6c7">
</p>

In the case you don't want to include the HISPlayer Sample, please disable it from the _Import Unity Package_ window.

<p align="center">
<img width=60% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/e9cb3d17-8adf-490f-b910-46dff943c870">
</p>

###  HISPlayer SDK versions 3.3.0 and below

Importing the package is the same as importing other normal packages in Unity. 
Select the package of HISPlayer SDK and import it.

**Assets > Import Package > Custom Package > HISPlayerSDK unity package**

Only the SDK will be imported using HISPlayer SDK versions lower than 3.4.0. 
Refer to [Import HISPlayer Sample](https://hisplayer.github.io/UnitySamples/#/hisplayer-sample) to know more about the _HISPlayer Sample_.

<p align="center">
<img width=70% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/7c52ba95-4420-4db3-972d-77930ce5cb9f">
</p>

<br>

## 1.2 Configure Unity for Android

Open the window **Tools > HISPlayer** located in the upper side of the screen > Click on Player Settings Configuration > Select **Build Target to Android** > Set all the required settings.

<p align="center">
<img width="550" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/b3203548-b0c3-46c9-ae74-dded00c5915a">
</p>

<p align="center">
      <img width="50%" alt="image" src="https://github.com/user-attachments/assets/31964b54-f40b-4590-a081-e45dd865f73a">
</p>

Setting **"Plugins folder"** will create **mainTemplate.gradle** and **gradleTemplate.properties** in your ProjectRoot\Assets\Plugins\Android. Please make sure you use the correct **mainTemplate.gradle** that is generated from our SDK. If you need to modify it, please make sure the dependencies and configurations from HISPlayer SDK's mainTemplate.gradle exist in your modified gradle file.

#### Android Target API Level
It is recommended to set Target API Level to 33. By selecting Android target 33, Unity is going to ask you to update (in the case you don't have the SDK 33 installed). Please, press "Update Android SDK" button.

<p align="center">
<img width="292" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/d4cfb0b6-5d5f-4233-bd42-b454ae64925e">
</p>

If your project requires Target API Level higher than 33 such as 34, then you can select the higher Target API Level and ignore the error message in the HISPlayer settings window. 

#### Unity 2023, Unity 6 and Above
If you use Unity 2023, Unity 6 and above with HISPlayer SDK v4.4.0 and below, please set the **Application Entry Point** to **Activity** and **disable GameActivity**. Please go to Edit > Project Settings > Player > Select Android tab > Other Settings > Configuration > Application Entry Point > Select **Activity**.

<p align="center">
<img alt="image" src="https://github.com/user-attachments/assets/a217594b-48e6-48cc-8eeb-8e9d681c84f4">
</p>

 
## 2.1 Setup HISPlayer Manager

*You may skip this section if you are using [**HISPlayerSample**](./import-sample.md) or any other sample from HISPlayer. The code set-up is already included in the sample script (HISPlayerSample.cs).*

Create a new script which will inherit from **HISPlayerManager**, for example, AndroidStreamController. It is necessary to add the **'using HISPlayerAPI;'** dependancy. Then, add this component to a new game object (recommended to be empty).

Call the **SetUpPlayer()** function in order to initialize the stream environment internally. This function can be called whenever it’s needed.

For example, using the Awake function:

```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using HISPlayerAPI;

public class AndroidStreamController : HISPlayerManager
{
    protected override void Awake()
    {
        base.Awake();
        SetUpPlayer();
    }
}
```

It is strictly necessary to use SetUpPlayer before using anything else. This function initializes everything else that will be needed during the usage of HISPlayer APIs. 

Remember to call the Release function after closing the app or before changing scenes in Unity for freeing the internal resources. 

## 2.2 Attach Unity resources

Move to **Unity Editor** to attach all the resources. The rendering system is supporting **Material**, **RawImage** and **RenderTexture** Unity’s components.

### <ins>Material</ins>
Create a new Material from **Assets > Create > Material** and attach it to the GameObject that is going to be used as screen and to the stream controller component. 

You can also use the **Resources > Materials > HISPlayerDefaultMaterial.mat** we provide in our package. 

<p align="center">
<img width=40% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/eacab2a8-7cee-4218-add9-98672f250540">
<img width=40% alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/756b60e7-46f6-4efd-9ced-4221a2a782df">
</p>

### <ins>Raw Image</ins>
This action will be related to Unity’s Canvas. If there is not a Canvas created yet, creating a **Raw Image** will create one automatically.

For the creation, select **GameObject > UI > Raw Image**. Once it is created, attach it to the stream controller component

<p align="center">
<img width="600" alt="image" src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/af854bfb-215e-4ec5-bc6e-2c3ad4f0321b">
</p>

### <ins>RenderTexture</ins>
For this you can use the RenderTexture we provide or create a RenderTexture from zero. In the first case, go to the Resources folder of our package and attach the **Resources > Materials > HISPlayerDefaultMaterialRenderTexture.mat** to the GameObject that is going to be used as screen and the **Resources > RenderTextures > HISPlayerRenderTexture.renderTexture** to the stream controller component.

For creating it from zero, select **Assets > Create > Render Texutre** and then create a **Material** referencing the **Render Texture**. This last action can be done automatically by grabbing the **Render Texture** and dropping it at the end of a GameObject's Inspector with the component **Mesh Renderer** with **Material field empty**. This will create the new material inside a **Materials** folder. 

Once all this process it’s done, associate the **RenderTexture** to the script component.

<p align="center">
<img src="https://github.com/HISPlayer/UnityiOS-SDK/assets/47497948/a0f26bc1-c7b1-432e-ad87-1a2d203d32c8">
</p>

## 2.3 Configure HISPlayer properties

### <ins>License Key</ins>
If you received a license key from HISPlayer, please input the license key in the **License Key** field. 

<p align="center">
<img width="600" src="https://github.com/HISPlayer/UnityWebGL-SDK/assets/47497948/7e7ca754-8d92-4c1b-b4aa-8218b6108bbc">
</p>

If the license key is not valid, the player won't work and will throw an error message. License key is not required for Unity Editor usage.

### <ins>Multi Stream Properties</ins>
Use Multi Stream Properties to set all the configuration needed for multi stream. It starts with 0 elements. Each element added has its own configuration for multiple players and corresponds to 1 Render Surface. If you just need a single stream, then you just need to add 1 element with 1 URL.

* <span style="color:blue">**Render Mode**</span>: Select the render surface. It can be RenderTexture, Material, RawImage or NONE.
* <span style="color:blue">**Material**</span>: Attach the **Material** asset created to the **Material** section of the element.
* <span style="color:blue">**Raw Image**</span>: Attach the **RawImage** asset created to the **RawImage** section of the element.
* <span style="color:blue">**Render Texture**</span>: Attach the **RenderTexture** to the **RenderTexture** section of the element.
* <span style="color:blue">**URL**</span>: Add the URL associated to the stream. Each stream can have multiple URLs, therefore users can use the same render surface to play different URLs. It is also possible to add local files allocated in the device’s storage and the StreamingAssets special folder of Unity (see [Playing Local Files](/local-files.md) for more details).
* <span style="color:blue">**URL MIME Types**</span>: Set the MIME types of each URL. It can be using URL Extension, HLS or DASH. URL Extension is set by default.
* <span style="color:blue">**Autoplay**</span>: Property to determine whether the player will start automatically after set up.
* <span style="color:blue">**Loop Playback**</span>: Property to loop the current playback. It’s true by default.
* <span style="color:blue">**Auto Transition**</span>: Property to change the playback to the next video in the playlist. This action won’t have effect when loopPlayback is true. It’s false by default.
* <span style="color:blue">**Digital Rights Management (DRM)**</span>: The DRM will be disabled by default.  See [DRM](/drm.md) for more details.
<p align="center">
<img src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/a6cddeab-c0d2-4607-b14f-1cbaf97db56c">
</p>

## Build and Run
Once the configuration it’s done, open 'Build Settings' and press 'Build And Run'.
