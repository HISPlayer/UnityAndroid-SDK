# HISPlayer API

## Public API
The following public APIs are provided by **HISPlayerManager**:
* **public List < StreamProperties > multiStreamProperties**: List of properties for multi stream.
* **public class StreamProperties**:
    * **public HisPlayerRenderMode renderMode**: Type of texture for rendering.
    * **public Material material**: Reference to the Unity Material.
    * **public RawImage rawImage**: Reference to the Unity Raw Image.
    * **public RenderTexture renderTexture**: Reference to the Unity Render Texture.
    * **public List < string > url**: List of the URLs for the stream.
    * **public bool autoPlay**: If true, the players will start playing automatically after set-up.
    * **public bool enableRendering**: Determines if the stream will be rendered or not. The value can change in every moment for toggling between render or non-render mode. If true, the player will be rendered. It can change in runtime.
    * **public List < string > keyServerURI**: List of the license key for each URL.
    * **public List < DRM_Token > DRMTokens**: List of the tokens for each URL.

* **public struct DRM_Token**: Information for the DRM token:
    * **public string tokenKey**: Key of the token associated with the url.
    * **public string tokenValue**: Value of the token associated with the key.

* **public enum HisPlayerRenderMode**: Type of texture for rendering:
    * **RenderTexture**
    * **Material**
    * **RawImage**
    * **NONE**

* **public enum HisPlayerEvent**: The list of events provided by HisPlayer SDK. The events can be used with the virtual functions in the next section:
    * **HISPLAYER_EVENT_PLAYBACK_READY**
    * **HISPLAYER_EVENT_PLAYLIST_CHANGE**
    * **HISPLAYER_EVENT_VIDEO_SIZE_CHANGE**
    * **HISPLAYER_EVENT_PLAYBACK_PLAY**
    * **HISPLAYER_EVENT_PLAYBACK_PAUSE**
    * **HISPLAYER_EVENT_PLAYBACK_STOP**
    * **HISPLAYER_EVENT_PLAYBACK_SEEK**
    * **HISPLAYER_EVENT_VOLUME_CHANGE**
    * **HISPLAYER_EVENT_END_OF_PLAYLIST**
    * **HISPLATER_EVENT_ON_TRACK_CHANGE**
    * **HISPLAYER_EVENT_ON_STREAM_RELEASE**
    * **HISPLAYER_EVENT_TEXT_RENDER**
    * **HISPLAYER_EVENT_AUTO_TRANSITION**
    * **HISPLAYER_EVENT_PLAYBACK_BUFFERING**
    * **HISPLAYER_EVENT_NETWORK_CONNECTED**

* **public enum HisPlayerError**: The list of errors provided by HisPlayer SDK. The errors can be used with the virtual functions in the next section:
   * **HISPLAYER_ERROR_TIMELOCK_EXPIRED** (no function on this)
   * **HISPLAYER_ERROR_NOT_VALID_APPID** (no function on this)
   * **HISPLAYER_ERROR_GENERAL_LICENSE_ERROR** (no function on this)
   * **HISPLAYER_ERROR_ANDROID_API_NOT_SUPPORTED** (no function on this)
   * **HISPLAYER_ERROR_NETWORK_FAILED**
   
* **public struct HisPlayerEventInfo**: The information of the triggered event.
   * **public HisPlayerEvent eventType**: The type of the event triggered.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public float param1**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param2**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param3**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param4**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the event.

* **public struct HisPlayerErrorInfo**: The information of the triggered error.
   * **public HisPlayerError errorType**: The type of the error triggered.
   * **public int playerIndex**: The index of the player where the error is triggered.
   * **public float param1**: This will have different meanings depending on the error. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the error.

* **public struct HisPlayerCaptionElement**: The information of the triggered event turns into caption’s format.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public string caption**: The next generated caption text.

* **public struct HisPlayerTrack**:
   * **public string id**: Id of the track
   * **public int bitrate**: Bitrate of the track in bits per second.
   * **public int width**: Width of the track.
   * **public int height**: Height of the track.
   * **public int framerate**: Framerate of the track in frames per second.

* **public struct HisPlayerCaptionTrack**:
   * **public string id**: ID of the caption
   * **public string language**: Language of the caption


## Functions
The following functions are provided by HisPlayerManager. They are not public so it’s necessary to create a custom script which inherits from HisPlayerManager.

### Virtual functions - This functions can be overridden

#### protected virtual void Awake()
MonoBehaviour function which will be called from the beginning of the scene. It can be overridden but to make the system work it’s necessary to call base.Awake() into the overridden function.

#### protected virtual void EventPlaybackReady(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_READY is triggered.
This event occurs when the current playback of a stream is ready to be used.
Calling functions such as GetTracks before this event is triggered will provide null information.
| Name  | Description  | 
|---|---|
|param1| Number of tracks of the playback.|

#### protected virtual void EventPlaylistChange(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYLIST_CHANGE is triggered.
This event occurs whenever the current playlist has been modified. It could happen when an URL has been  added or deleted.
| Name  | Description  | 
|---|---|
|param1| Playlist length.|


#### protected virtual void EventVideoSizeChange(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_VIDEO_SIZE_CHANGE is triggered.
This event occurs whenever the internal video size of the current track changes.
This event is triggered by the ABR feature.
| Name  | Description  | 
|---|---|
|param1| Width of the video.|
|param2| Heigth of the video.|

#### protected virtual void EventPlaybackPlay(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PLAY is triggered.
This event occurs whenever an internal playback has been played.
| Name  | Description  | 
|---|---|
|param1| PLAY = 1, PAUSE = 0|

#### protected virtual void EventPlaybackPause(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PAUSE is triggered.
This event occurs whenever an internal playback has been paused.

#### protected virtual void EventPlaybackStop(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_STOP is triggered.
This event occurs whenever an internal playback has been stopped.

#### protected virtual void EventPlaybackSeek(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_SEEK is triggered.
This event occurs whenever an internal playback has been sought to a new time position.
| Name  | Description  | 
|---|---|
|param1| Value of the old track position in milliseconds.|
|param2| Value of the new track position in milliseconds.|


#### protected virtual void EventVolumeChange(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_VOLUME_CHANGE is triggered.
This event occurs whenever the volume has been modified.
| Name  | Description  | 
|---|---|
|param1| New value for the volume.|

#### protected virtual void EventEndOfPlaylist(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_BUFFERING is triggered.
This event occurs whenever an internal playlist reaches the end of the list.

#### protected virtual void EventOnTrackChange(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_ON_TRACK_CHANGE is triggered.
This event occurs whenever the tracks of the stream have changed. This event is not triggered by the ABR feature.
| Name  | Description  | 
|---|---|
|param1| Number of video tracks available.|
|param2| Number of subtitles tracks available.|
|param3| Number of audio tracks available.|

#### protected virtual void EventOnStreamRelease(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_ON_STREAM_RELEASE is triggered.
This event occurs whenever a player/stream has been released.
| Name  | Description  | 
|---|---|
|param1| Number of players after releasing.|

#### protected virtual void EventTextRender(HisPlayerCaptionElement subtitlesInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_TEXT_RENDER is triggered.
This event occurs whenever a caption's text has been generated.
| Name  | Description  | 
|---|---|
|caption| The next generated caption text.|

#### protected virtual void EventAutoTransition(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_AUTO_TRANSITION is triggered.
This event occurs whenever the playlist has changed of playback automatically. The change is due to the end of the current playback, so the next playback in the list is released.

#### protected virtual void EventPlaybackBuffering(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_PLAYBACK_BUFFERING is triggered.
This event occurs whenever an internal playback is buffering.

#### protected virtual void EventPlaybackBuffering(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when HisPlayerEvent.HISPLAYER_EVENT_NETWORK_CONNECTED is triggered.
This event occurs whenever the network has been reconnected.

#### protected virtual void ErrorNetworkFailed(HisPlayerErrorInfo errorInfo)
Override this method to add custom logic when HisPlayerError.HISPLAYER_ERROR_NETWORK_FAILED is triggered.
This error occurs whenever the network on a stream playback has failed.
| Name  | Description  | 
|---|---|
|param1| Number of tracks of the playback.|

### Non-virtual functions 
These functions can’t be overridden and they can be used only inside the inherited script. If it’s needed to use some of these functions into the Unity scene, for example with buttons, it is needed to create a public function which connects the button with the API.

#### protected void SetUpPlayer()
Initialize the player video stream system internally. It is necessary to use this function before anything else.

#### protected void Release()
Free all resources internally.

#### protected void Play(int playerIndex)
Play a certain stream giving a playerIndex. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void Pause(int playerIndex)
Pause a certain stream giving a playerIndex. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void Stop(int playerIndex)
Stop a certain stream giving a playerIndex. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void Seek(int playerIndex, long milliseconds)
Seek a certain stream to a certain time giving a playerIndex and the time of the track to be sought in milliseconds. The stream is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SetVolume(int playerIndex, float volume)
Modify the volume of a certain stream giving a playerIndex. The volume of the track value ranges between 0.0f and 1.0f. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void AddStream(StreamProperties newStream)
Add a new stream to the list multiStreamProperties. The stream must be added using this function instead of changing the list manually.

#### protected void ChangeVideoContent(int playerIndex, int urlIndex)
Change the video’s url  of a certain player. The next playback will start paused. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list. The urlIndex is associated with the index of the element in the list of urls.

#### protected void AddVideoContent(int playerIndex, string url)
Add new content to a certain player. If the enableDRM variable is true, a video content with an empty license will be added. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list. The url is the link to the new video. Please, make sure the string is correct. This function supports local file paths.

#### protected void AddVideoContent(int playerIndex, string url, string keyServerUri,  string token key = “empty”opt, string token value= “empty”opt)
Add new content to a certain player and its respective key server uri and tokens if needed. The enableDRM variable must be true for using this function. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list. The url is the link to the new video. The keyServerUri is the license key associated with the url. Please, make sure the string is correct. This function supports local file paths.

#### protected void RemoveVideoContent(int playerIndex, int urlIndex)
Remove content from a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.  The urlIndex is associated with the index of the element in the list of urls.

#### protected void RemoveStream(int playerIndex)
Remove a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected string GetPlayerLog(int playerIndex)
Provides a log message obtained from a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoPosition(int playerIndex)
Provides information about the timeline position in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoDuration(int playerIndex)
Provides information about the total duration in milliseconds, of the current video of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected HisPlayerTrack[] GetTracks(int playerIndex)
Provides information about a track of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackBitrate(int playerIndex, int trackIndex)
Get the bitrate of a certain track of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackWidth(int playerIndex, int trackIndex)
Get the width of a certain track of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackHeight(int playerIndex, int trackIndex)
Get the height of a certain track of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 of the list.

#### protected int GetTrackID(int playerIndex, int trackIndex)
Get the ID of a certain track of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackCount(int playerIndex)
Get the number of tracks of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### public HisPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
Provide information about all the captions of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### public int GetCaptionsCount(int playerIndex)
Obtain the number of captions of a  certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionID(int playerIndex, int ccTrackIndex)
Obtain the ID of a certain caption of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
Obtain the language of a certain caption of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SetMaxBitrate(int playerIndex, int bitrate)
Set a new maximum bitrate (in bits per second) of a specific track. This doesn't disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SetMinBitrate(int playerIndex, int bitrate)
Set a new minimum bitrate (in bits per second) of a specific track. This doesn't disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SelectTrack(int playerIndex, int bitrate)
Select a certain track of a certain stream to be used as the main track. This action will disable ABR. It is possible to activate ABR using SetMaxBitrate and SetMinBitrate with different values for each one. The possible tracks can be obtained from the tracks returned from the method GetTracks. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SetDecodedFrameBufferEnabled(bool enable, int playerIndex = 0opt, int bufferSize = 60opt)
Enable the Decoded Frame Buffer Functionality. This function can be called independently of the SetUp function.  This functionality can only be called for one single stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list. The bufferSize will take 60 as the default value.

#### protected Texture2D GetDecodedFrameAtTimestamp(long msec)
Retrieves the Texture2D of the requested frame or null if the frame is not available for the given timestamp (parameter msec in milliseconds).

#### protected Vector2 GetDecodedFrameBufferRange()
Retrieves the range of the Decoded Frame Buffer in milliseconds. The X value of the Vector2 corresponds to the timestamp in milliseconds of the oldest frame stored in the buffer, while the Y value corresponds to the newest.

#### protected int GetNetworkBandwidth()
Returns the current network bandwidth. This value is an estimation in kbps.
