# HISPlayer Unity Android SDK Release Notes
### Version 2.5.0
##### July 4, 2023
- [**Added**] Android support for Unity 2022
- [**Added**] Subtitles support for MacOS Editor
    - HISPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
    - int GetCaptionsCount(int playerIndex)
    - void EnableCaptions(int playerIndex, bool enabled)
    - string GetCaptionID(int playerIndex, int ccTrackIndex)
    - string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
    - void SelectCaptionTrack(int playerIndex, int ccTrackIndex)
- [**Improvement**] Optimized Android HISPlayer settings panel. There is a new field in the settings for putting target SDK as 33.
- [**Improvement**] Optimized AddNewStream function on Windows Editor
- [**Improvement**] Optimized Release function on Windows Editor

### Version 2.4.0
##### June 15, 2023
- [**Improvement**] Optimized gradle build for Unity version 2020.

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

- [**Added**] **HISPLAYER_EVENT_NETWORK_CONNECTED** and **EventNetworkConnected**: This event occurs whenever the network has been reconnected.

### Version 1.5.0
##### April 10, 2023
- [**Added**] The tokens has been added. The tokens are a new layer for protecting the url content. There is a new field for adding tokens associated with the url
- DRM Tokens: List that contains DRM_Token elements. Each one has a string tokenKey and a string tokenValue.

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
- [**Added**] **Decoded Frame Buffer Functionality** is now compatible with not rendering the stream on any surface.

### Version 1.2.0
##### March 22, 2023
- [**Added**] **HISPLAYER_EVENT_AUTO_TRANSITION** and **EventAutoTransition** for detecting whenever the playlist has changed of playback automatically.
- [**Changed**] **HISPLAYER_EVENT_END_OF_CONTENT** and **EventEndOfContent** changed to **HISPLAYER_EVENT_END_OF_PLAYLIST** and **EventEndOfPlaylist**
- [**Added**] Subtitles functionalities for WebVTT and CEA-608 added: The subtitles are being obtained from the url of the playback. Functionality for obtaining subtitles from a single uri has not been implemented yet.
    
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
- [**Added**] Decoded Frame Buffer functionalities included.

    - GetDecodedFrameAtTimestamp(int msec, bool deletePreviousFrames = true)
    - GetDecodedFramesBufferRange()

### Version 1.0.1
##### March 9, 2023
- [**Added**] Added parameters for each Event. The meaning of each parameter depends on the triggered event. The information is both in the documentation and in the function's comments.

### Version 1.0.0
##### March 7, 2023
- [**Added**] Initial release of HisPlayer Android SDK for Unity.
