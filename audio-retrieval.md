# Audio PCM Data Retrieval and Connection to Unity Audio

It is possible to retrieve the raw Audio PCM data and connect it to Unity Audio Source component through [OnAudioFilterRead()](https://docs.unity3d.com/6000.1/Documentation/ScriptReference/MonoBehaviour.OnAudioFilterRead.html). 

## Requirements
#### Unity version
- Supported Unity versions: 2022, 2023, Unity 6

#### HISPlayer SDK version
- HISPlayer SDK version: 4.9.0 and above

<br>

It’s required to set **UnityAudio** property in MultistreamProperties to True through Unity editor or script.

<p align="center">
<img width=40% src="https://github.com/user-attachments/assets/e80ceca8-5e05-4ee9-be04-6269a795be51">
</p>

To get the audio data, you can choose either using **GetAudioData()** or **FillAudioData()** API. 
Please refer to below APIs section and HISPlayer Android Spatial Audio Sample section.

## Related APIs

**public bool UnityAudio (Read-only)**: Retrieves the audio data that can be connected to Unity AudioSource through OnAudioFilterRead() instead of direct device speaker output. Calling SetVolume API to control the audio volume will not work, please control the corresponding Unity Audio Source volume instead. It's false by default. To modify this value, please, use the Editor or the constructor **StreamProperties(loopPlayback, autoTransition, unityAudio)**.

#### public float[][] GetAudioData(int playerIndex, int sampleSizePerChannel)
Get the audio PCM data of each channel in float array. The order of the channel is the same as the order of the stream's audio channel layout, e.g. C L R Ls Rs. The **playerIndex** is the index of the player in multistream properties, the **sampleSizePerChannel** is the requested data size of each audio channel. Please use this API when **UnityAudio** is set to true.

#### public void FillAudioData(int playerIndex, float[] audioData, int channelIndex)
Fill the audio buffer with new audio PCM data. The **playerIndex** is the index of the player in multistream properties. The **audioData** is the audio buffer that will be filled with new audio data. The **channelIndex** is the index of the audio channel. The order of the channel index must be the same as the order of the stream's audio channel layout, e.g. C=0, L=1, R=2, Ls=3, Rs=4. Please use this API when **UnityAudio** is set to true.

## HISPlayer Android Spatial Audio Sample

Please download the sample here: [HISPlayer_Android_SpatialAudio_Sample.unitypackage](https://downloads.hisplayer.com/Unity/AllPlatforms/HISPlayer_Android_SpatialAudio_Sample_v2.unitypackage) and import it to your Unity project.

Before using the sample, make sure that you have imported HISPlayer SDK. If not, please follow the [**Quickstart Guide**](./setup-guide.md).

The sample plays local video with 5 audio channels that are connected to 5 AudioSources. You may modify the sample depending on your audio channel count. 
Please refer to the sample package which consists of the following Unity scenes in **HISPlayerSpatialAudioSample\Scenes**:
- **HISPlayerFillAudioSample**: Sample utilizing **FillAudioData()** API by passing the float[] data from each Unity Audio Source **OnAudioFilterRead()** which the data buffer will be filled automatically. To check the APIs usage, please refer to all scripts in **HISPlayerSpatialAudioSample\Scripts\Sample\Audio\FillAudioSample**.
- **HISPlayerGetAudioSample**: Sample utilizing **GetAudioData()** API in Unity Audio Source **OnAudioFilterRead()** for center channel, and the new audio data is shared to other channel classes. The new audio data will be copied to the float[] data of **OnAudioFilterRead()** for each channel. To check the APIs usage, please refer to all scripts in **HISPlayerSpatialAudioSample\Scripts\Sample\Audio\GetAudioSample**.
