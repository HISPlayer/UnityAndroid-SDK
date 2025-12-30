# HISPlayer Unity Android SDK Release Notes

### Version 4.14.1
##### December 23, 2025
- [**Improvement**] Updated eventType of EventPlaybackSeekEnd to output HISPLAYER_EVENT_PLAYBACK_SEEK_END.

### Version 4.14.0
##### December 18, 2025
- [**Improvement**] Improved adding stream at runtime when initializing streams without predefined URLs.
- [**Improvement**] Improved volume change event handling to ensure HISPLAYER_EVENT_VOLUME_CHANGE is triggered consistently across all platforms.
- [**Improvement**] Updated GetProgramDateTimeEpoch to return the exact Epoch time of the current frame.
- [**Improvement**] Improved seek event handling to ensure HISPLAYER_EVENT_PLAYBACK_SEEK_END is consistently triggered across all platforms.

### Version 4.13.0
##### November 28, 2025
- [**Added**] New playback seek events: HISPLAYER_EVENT_PLAYBACK_SEEK_BEGIN and HISPLAYER_EVENT_PLAYBACK_SEEK_END with their respective overridable functions. HISPLAYER_EVENT_PLAYBACK_SEEK and the overridable function are deprecated.
- [**Added**] Customizable logging system allowing configuration of logLevel, showPlatform, showColorized, and showTimestamp.
- [**Added**] GetProgramDateTimeEpoch and GetProgramDateTimeString APIs to obtain the EXT-X-PROGRAM-DATE-TIME information from HLS streams.

### Version 4.12.0
##### October 29, 2025
- [**Improvement**] Optimized Unity lifecylce callbacks when releasing player.
- [**Improvement**] Optimized render texture cleaning when release player.
- [**Improvement**] Optimized playback repeat mode.
- [**Improvement**] Optimized stop function.
- [**Improvement**] Improved the UI appearance of HISPlayerManager in the inspector.

### Version 4.10.0
##### September 11, 2025
- [**Improvement**] Editor no longer clears console logs after stopping Play mode.
- [**Improvement**] Improved log when releasing player.
- [**Improvement**] Improved package architecture for multiple packages combination.

### Version 4.9.0
##### July 10, 2025
- [**Added**] Audio PCM data retrieval with the following APIs: UnityAudio, GetAudioData, FillAudioData.
- [**Added**] GetAudioSessionId API to get the audio session identifier.
- [**Added**] IsPlaying API to check whether the certain player is playing.
- [**Added**] 16KB memory pages support for Google Play Store.

### Version 4.8.0
##### July 7, 2025
- [**Improvement**] Enhancement to InspectorGUI to dynamically show/hide certain options.

### Version 4.7.0
##### March 3, 2025
- [**Improvement**] Optimized Android plugin

### Version 4.6.0
##### January 16, 2025
- [**Improvement**] Upgraded Android plugin

### Version 4.5.0
##### December 4, 2024
- [**Added**] Unity 6 support
- [**Added**] GameActivity support
- [**Improvement**] Optimized memory when releasing stream with Vulkan
- [**Improvement**] Optimized EventNetworkConnected and ErrorNetworkFailed callbacks
- [**Improvement**] Optimized GetTrackID, GetTrackBitrate, GetTrackWidth, and GetTrackHeight return values
- [**Improvement**] Optimized the event callbacks after removing streams

### Version 4.4.0
##### September 10, 2024
- [**Added**] Release API is called automatically when stopping the Editor, changing scenes or closing the app
- [**Added**] HISPLAYER_EVENT_TIMELINE_UPDATED and EventTimelineUpdated
    - This event occurs whenever the timeline of the current video has been updated. In the case of live content this may happen every certain time during the playback. This may change the current video position value from GetVideoPosition(...).
- [**Improvement**] Optimized error log messages

### Version 4.3.2
##### August 9, 2024
- [**Added**] New RenderMode External Surface to play Widevine L1 content with Meta Quest devices

### Version 4.3.0
##### August 8, 2024
- [**Added**] Vulkan support
- [**Added**] New HISPlayer Video Uploader feature. Turn local videos into streaming videos such as HLS or DASH. This videos are going to be stored in our server for you. Please, on the Editor refer to:
    - [HISPlayer Video Upload documentation](https://hisplayer.github.io/UnityVideoUpload/#/)
- [**Added**] Custom resources to support the stereoscopic rendering mode for Oculus
    - Packages > HISPlayer SDK > HISPlayer > Scripts > Shaders > **HISPlayerStereoscopicShader.shader**
    - Packages > HISPlayer SDK > HISPlayer > Resources > Materials > **HISPlayerStereoscopicMaterial.mat**
    - Packages > HISPlayer SDK > HISPlayer > Scripts > RenderTextures > **HISPlayerStereoscopicRenderTexture.rendertexture**
- [**Added**] Custom resources to play 180/360 videos
    - Packages > HISPlayer SDK > HISPlayer > Resources > Materials > **HISPlayer360Material.mat**
    - Packages > HISPlayer SDK > HISPlayer > Resources > Materials > **HISPlayer180Material.mat**
    - Packages > HISPlayer SDK > HISPlayer > Scripts > Shaders > **HISPlayer360Shader.shader**
    - Packages > HISPlayer SDK > HISPlayer > Scripts > RenderTextures > **HISPlayer360RenderTexture.rendertexture**
- [**Improvement**] Optimized HISPlayer Settings log messages
- [**Improvement**] Optimized Event and Error listeners
- [**Improvement**] Optimized license checking when date and time of the device are set to manual
- [**Improvement**] Optimized HISPlayer API function commentaries to be more clear
- [**Improvement**] Optimized runtime log messages
- [**Improvement**] Optimized initialization of the videos
- [**Improvement**] Optimized ABR and track selection without limitation from device's resolution

### Version 3.4.3
##### June 7, 2024
- [**Added**] Cache functionalites support
    - protected void InitCacheInstance(long maxCacheSize = 150 * 1024 * 1024L)
    - protected void AddURLToCache(string url)
    - protected void RemoveURLFromCache(string url)
    - protected bool IsURLCached(string url)
    - protected long GetRemainingCacheSpace()  

### Version 3.4.2
##### April 24, 2024
- [**Improvement**] Improvement of software robustness

### Version 3.4.1
##### April 23, 2024
- [**Improvement**] Improvement of software robustness

### Version 3.4.0
##### April 10, 2024
- [**Added**] HISPlayer360Shader.shader for the 360 Oculus mode
- [**Added**] Local Playback Persistent Datapath support 
- [**Added**] HISPLAYER_ERROR_PLATFORM_NOT_REGISTERED error event
- [**Added**] URL_EXTENSION, HLS and DASH MIME Types support. Please, refer to HISPlayerMimeTypes on [HISPlayer API](https://hisplayer.github.io/UnityAndroid-SDK/#/hisplayer-api)
    -  URL_EXTENSION (Default)
    -  HLS
    -  DASH
- [**Improvement**] Optimized URL video initialization
- [**Improvement**] Optimized HISPlayer Settings
    - A warning message will be displayed in case a field required by HISPlayer SDK is missing

### Version 3.3.0
##### January 25, 2024
- [**Added**] New API to change video content using the URL string as a parameter:
    - **ChangeVideoContent(int playerIndex, string url)**
    - **ChangeVideoContent(int playerIndex, string url, string keyServerURI, string tokenKey = "", string tokenValue = "")**
- [**Improvement**] Optimized error logs

### Version 3.2.0
##### December 7, 2023
- [**Added**] AutoTransition and LoopPlayback APIs to multiplatform SDK
- [**Added**] EnableABR and DisableABR APIs to multiplatform SDK
- [**Added**] Unity 2023 support to multiplatform SDK

### Version 3.1.1
##### November 23, 2023
- [**Improvement**] Improvement of software robustness

### Version 3.1.0
##### October 11, 2023
- [**Improvement**] Optimized Android IL2CPP build

### Version 3.0.0 (Multiplatform SDK)
##### September 5, 2023
The Android SDK is moved to multiplatform HISPlayerSDK (Android, iOS, macOS, WebGL, Windows)

Starting from version 3.0.0, the Android SDK is part of multiplatform SDK

### Version 2.13.0
##### December 5, 2023
- [**Added**] Local documentation
- [**Update**] HISPlayer Settings is now visible under 'Tools' Unity window
    - Refer to [Configure Unity for Android](https://hisplayer.github.io/UnityAndroid-SDK/#/setup-guide?id=_12-configure-unity-for-android) 
- [**Improvement**] Improvement of software robustness

### Version 2.12.0
##### October 24, 2023
- [**Added**] Unity 2023 support

### Version 2.11.0
##### October 18, 2023
- [**Added**] EnableABR and DisableABR API
- [**Added**] LoopPlayback API to loop the current playback. This will trigger HISPlayerEvent.HISPLAYER_EVENT_END_OF_CONTENT
    - Refer to [Stream Properties - LoopPlayback](https://hisplayer.github.io/UnityAndroid-SDK/#/hisplayer-api)
- [**Added**] AutoTransition API to change the playback to the next video in the playlist. This will trigger the HISPlayerEvent.HISPLAYER_EVENT_AUTO_TRANSITION
    - Refer to [Stream Properties - AutoTransition](https://hisplayer.github.io/UnityAndroid-SDK/#/hisplayer-api) 

### Version 2.10.0
##### September 21, 2023
- [**Added**] [Custom Shaders for Linear Color Space](/shaders.md)

### Version 2.9.0
##### September 7, 2023
- [**Improvement**] Optimized HISPlayer Settings

### Version 2.8.0
##### August 7, 2023
- [**Added**] Playback Speed Controller for Windows and MacOS editors

### Version 2.7.0
##### July 28, 2023
- [**Added**] Playback Speed Controller. Values must be greater than 0 and less than or equal to 8
    - void SetPlaybackSpeedRate(int playerIndex, float speed)
    - float GetPlaybackSpeedRate(int playerIndex)
- [**Improvement**] Optimized Release function for MacOS Editor
  
### Version 2.6.0
##### July 11, 2023
- [**Added**] Flip texture vertical API.
- [**Added**] Audio-Track-Selection support for MacOS Editor
    - HISPlayerAudioTrack[] GetAudioTrackList(int playerIndex)
    - int GetAudioCount(int playerIndex)
    - string GetAudioID(int playerIndex, int audioTrackIndex)
    - string GetAudioLanguage(int playerIndex, int audioTrackIndex)
    - void SelectAudioTrack(int playerIndex, int audioTrackIndex)

### Version 2.5.0
##### July 4, 2023

- [**Added**] Subtitles support for MacOS Editor
    - HISPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
    - int GetCaptionsCount(int playerIndex)
    - void EnableCaptions(int playerIndex, bool enabled)
    - string GetCaptionID(int playerIndex, int ccTrackIndex)
    - string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
    - void SelectCaptionTrack(int playerIndex, int ccTrackIndex)
- [**Improvement**] Optimized Android HISPlayer settings panel. There is a new field in the settings for putting target SDK as 33
- [**Improvement**] Optimized AddNewStream API on Windows Editor
- [**Improvement**] Optimized Release API on Windows Editor
- [**Improvement**] Optimized SDK for Unity 2022
- [**Improvement**] Optimized SetupPlayer API during runtime for Windows Editor

### Version 2.4.0
##### June 15, 2023
- [**Improvement**] Optimized gradle build for Unity version 2020

### Version 2.2.0
##### May 25, 2023
- [**Added**] Audio track selection functionalities: 
    - GetAudioTrackList(int playerIndex)
    - GetAudiosCount(int playerIndex)
    - GetAudioID(int playerIndex, int audioTrackIndex)
    - GetAudioLanguage(int playerIndex, int audioTrackIndex)
    - SelectAudioTrack(int playerIndex, int audioTrackIndex)

- [**Added**] MacOS Editor support
 
### Version 2.1.0
##### April 28, 2023
The Android package is combined with iOS package.

### Version 1.6.0
##### April 25, 2023
- [**Added**] New Error Listener System for handling different errors:
    - HISPLAYER_ERROR_TIMELOCK_EXPIRED = 0,
    - HISPLAYER_ERROR_NOT_VALID_APPID = 1,
    - HISPLAYER_ERROR_GENERAL_LICENSE_ERROR = 2,
    - HISPLAYER_ERROR_ANDROID_API_NOT_SUPPORTED = 3

- [**Added**] **HISPLAYER_EVENT_NETWORK_CONNECTED** and **EventNetworkConnected**: This event occurs whenever the network has been reconnected

### Version 1.5.0
##### April 10, 2023
- [**Added**] The tokens has been added. The tokens are a new layer for protecting the url content. There is a new field for adding tokens associated with the url
- DRM Tokens: List that contains DRM_Token elements. Each one has a string tokenKey and a string tokenValue

### Version 1.4.0
##### April 5, 2023
- [**Added**] New field for HISPlayerManager: 
      
    - License Key: A license key must be provided for being able to use the SDK

- [**Added**] New event: HISPLAYER_EVENT_PLAYBACK_BUFFERING - This event occurs whenever an internal playback is buffering
- [**Added**] Automation for HISPlayer Player Settings
- [**Added**] Support for Windows Editor (without multistream)
- [**Added**] Support for local videos using StreamingAssets or device's internal files
    
    - Supported formats: MP4, MP3, MOV, M4A, MKV, WAV, OGG and FLV

### Version 1.3.0
##### March 27, 2023
- [**Added**] New **HISPlayerRenderMode** option 'NONE' has been added. Choose this option if the stream is not going to be rendered on any surface
- [**Added**] **Decoded Frame Buffer Functionality** is now compatible with not rendering the stream on any surface

### Version 1.2.0
##### March 22, 2023
- [**Added**] **HISPLAYER_EVENT_AUTO_TRANSITION** and **EventAutoTransition** for detecting whenever the playlist has changed of playback automatically
- [**Changed**] **HISPLAYER_EVENT_END_OF_CONTENT** and **EventEndOfContent** changed to **HISPLAYER_EVENT_END_OF_PLAYLIST** and **EventEndOfPlaylist**
- [**Added**] Subtitles functionalities for WebVTT and CEA-608 added: The subtitles are being obtained from the url of the playback. Functionality for obtaining subtitles from a single uri has not been implemented yet
    
    - EnableCaptions(int playerIndex, bool enabled)
    - GetCaptionTrackList(int playerIndex)
    - GetCaptionsCount(int playerIndex)
    - GetCaptionID(int playerIndex, int ccTrackIndex)
    - GetCaptionLanguage(int playerIndex, int ccTrackIndex)
    - SelectCaptionTrack(int playerIndex, int ccTrackIndex)
- [**Added**] DRM video content available for adding content from code or editor:

    - **EnableDRM** variable to allow the DRM usage
    - **Key Server URI** list to add different license keys
    - **AddVideoContent** overloaded with one more field: **string keyServerUri**

### Version 1.1.0
##### March 16, 2023
- [**Added**] Decoded Frame Buffer functionalities included

    - GetDecodedFrameAtTimestamp(int msec, bool deletePreviousFrames = true)
    - GetDecodedFramesBufferRange()

### Version 1.0.1
##### March 9, 2023
- [**Added**] Added parameters for each Event. The meaning of each parameter depends on the triggered event. The information is both in the documentation and in the function's comments

### Version 1.0.0
##### March 7, 2023
- [**Added**] Initial release of HisPlayer Android SDK for Unity.
