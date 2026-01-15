# Common Issues

## Bright Video Output
If the video output is too bright when you are using **Linear** color space in the Unity Project Setting, please refer to this documentation: [Custom Shaders for Linear Color Space](https://hisplayer.github.io/UnityAndroid-SDK/#/shaders).

## Vertically Inverted / Flipped Video Output
### Normal Video (Non 180/360 Video)
Select the GameObject where you render the video. In the **Inspector** window, set the **Y Scale** with negative value of the original value.
<p align="center">
  <img width="50%" alt="image" src="https://github.com/user-attachments/assets/a65b409a-1af9-48be-a676-e2c8ed91aa96">
</p>

### 180/360 Video
Use **HISPlayer360Shader.shader** and attach it to the material. Make sure that the **Flip Vertically** option is enabled.

<p align="center">
  <img width="50%" alt="image" src="https://github.com/user-attachments/assets/3102cf49-0598-4914-8a54-ef00443853d5">
</p>

## Meta Quest Store Android Target API Level 32
HISPlayer SDK requires Android Target API Level 34, but Meta Quest Store requires Android Target API Level 32. To solve this, please download the updated custom Android gradle files from the following links depending on your Unity version:
- [Unity 6](https://downloads.hisplayer.com/Unity/Resources/Android34_Unity6.zip)
- [Unity 2022](https://downloads.hisplayer.com/Unity/Resources/Android34.zip)
- [Unity 2021 & 2020](https://downloads.hisplayer.com/Unity/Resources/Android34_Unity2020_2021.zip)

Please follow these steps after downloading the zip file:
- Extract the zip file. It contains **gradleTemplate.properties**, **launcherTemplate.gradle** and **mainTemplate.gradle**.
- Copy the 3 files above to your **UnityProject\Assets\Plugins\Android\...** This will replace the old files.
- Build and run your project again.

If you see the following errors and warning in HISPlayerSettings after copying the new files, you can ignore it.
<p align="center">
  <img width="40%" alt="image" src="https://github.com/user-attachments/assets/10591651-e27d-4d06-ba08-1280c10fd964">
</p>

## Android PlayStore Target API Level 35
If your project requires Target API Level higher than 34 such as 35, then you can select the higher Target API Level and ignore the error message in the HISPlayer settings window. 

