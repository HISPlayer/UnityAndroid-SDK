# Playing Local Files

HISPlayer Android for Unity can playback local content, both from the device's storage and [**Unity Streaming Assets**](./local-files.md#Unity-Streaming-Assets).

<br>

In addition, Android’s devices need permission for using some features such as exploring or using the device’s folders and files. Asking for permissions can be configured following [**Configure Unity for Android**](./setup-guide.md#Configure-Unity-for-Android).

## Unity Streaming Assets
To use this format, it’s necessary to create a new folder into the **Assets** folder of Unity named **StreamingAssets**.

<p align="center">
<img src="./assets/streaming-assets.png" width="200" height="100">
</p>

The next step is to add a video content inside the folder and pass the name (**with the extension**) to the **Multi Stream Properties**.
&nbsp;

<p align="center">
<img src="./assets/content-strassets.png" width="500" height="150">
</p>

In case that subfolders are created inside StreamingAssets, the path of the file **must include the subfolder’s name** inside the field of Multi Stream Properties, e.g, with a subfolder named **“MyVideos”** the following path must be used: 

**MyVideos/localPlayback.mp4** 
&nbsp;

## Device’s local videos
In order to add videos from the device, keep in mind the SDK is taking the root path of the phone storage. The next step is to pass the name (**with the extension**) to the Multi Stream Properties.

<p align="center">
<img src="./assets/local-content.png" width="850" height="500">
</p>

In the case of exploring subfolders of the devices, it’s enough adding the subfolder at the beginning of the path, e.g., using a **WhatsApp video** it is possible to provide the following path: 

**WhatsApp/Media/WhatsApp Video/video.mp4**
&nbsp;
