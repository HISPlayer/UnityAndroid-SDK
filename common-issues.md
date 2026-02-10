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

## Android PlayStore Target API Level 35
If your project requires Target API Level higher than 34 such as 35, then you can select the higher Target API Level and ignore the error message in the HISPlayer settings window. 

