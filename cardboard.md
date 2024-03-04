# Google Cardboard
Google Cardboard is an inexpensive handheld device that powers a virtual reality (VR) experience using almost any smartphone running Cardboard-enabled apps and it is compatible 
with Unity and HISPlayer. 

Before continuing, please, complete the [HISPlayer QuickStart Guide](https://hisplayer.github.io/UnityAndroid-SDK/#/setup-guide).

Minimum Unity version:

- **Unity 2021.3.32f1**

## Install Google Cardboard in Unity
Please, follow these steps to install the Google Cardboard package in your Unity project:

1. Open **Window > Package Manager**
2. Click on **'+'** icon and select **Add package from git URL**
3. Paste **https://github.com/googlevr/cardboard-xr-plugin.git** in the input field
4. Wait until the package is imported
5. In the sample section you can import a simple sample for the Google Cardboard. The elements for the sample
will be downloaded in Assets/Samples/Google Cardboard/<version>/Hello Cardboard.

Please, refer to the official [Quickstart for Google Cardboard for Unity ](https://developers.google.com/cardboard/develop/unity/quickstart) for more information.

<p align="center">
  <img width=70% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/32ba2739-e392-4ccb-b2e7-600807497cc5">
</p>

<p align="center">
  <img width=70% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/a1048f03-9926-4e21-b31e-b9623fee872a">
</p>

## Set up Google Cardboard with HISPlayer
Once the [1.2 configured HISPlayer SDK for Android](https://hisplayer.github.io/UnityAndroid-SDK/#/setup-guide?id=_12-configure-unity-for-android) is done, 
the following 2 files will be generated:

- Assets\Plugins\Android\gradleTemplate.properties
- Assets\Plugins\Android\mainTemplate.gradle

You need to add these dependencies following the official google cardboard guide : [Quickstart for Google Cardboard for Unity](https://developers.google.com/cardboard/develop/unity/quickstart)

1. Add the following lines to the dependencies section of **Assets/Plugins/Android/mainTemplate.gradle**:

  - implementation 'androidx.appcompat:appcompat:1.4.2'
  - implementation 'com.google.android.gms:play-services-vision:20.1.3'
  - implementation 'com.google.android.material:material:1.6.1'
  - implementation 'com.google.protobuf:protobuf-javalite:3.19.4'

2. Add the following lines to **Assets/Plugins/Android/gradleTemplate.properties**:

  - android.enableJetifier=true
  - android.useAndroidX=true

 You can also download the updated files from below links. Please, copy these files to your **Assets\Plugins\Android** replacing the old files: 

- https://downloads.hisplayer.com/Unity/CardboardAndroidPlugin/gradleTemplate.properties
- https://downloads.hisplayer.com/Unity/CardboardAndroidPlugin/mainTemplate.gradle

After updating the files and rebuilding your project, if you have this error **unity java.nio.file.AccessDeniedException** you will need to clean the **.gradle cache**.
Or you can simply follow these steps:

- Close your Unity project
- Remove Library folder from your Unity root project : yourProject/Library 
- Re-open your Unity project. This will re-generate the Library folder.
- Build and Run

Please, ignore the error message that appears in the HISPlayer Settings window after the files **gradleTemplate.properties** and **mainTemplate.gradle** are modified.

<p align="center">
  <img width=50% src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/47497948/db261cc9-0268-4889-8a6f-a26a34041bb8">
</p>
