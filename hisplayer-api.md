# HISPlayer API

## Public API
The following public APIs are provided by **HISPlayerManager**:

* **public string licenseKey**: License key for making the SDK works. License key is not required for Unity Editor usage.

* **public List <StreamProperties> multiStreamProperties**: List of properties for multi stream. Please, don't modify this list directly, use the **AddStream** or **RemoveStream** functions instead.
  
* **public class StreamProperties**:
    * **public StreamProperties(bool isLoopPlaybackEnabled = true, bool isAutoTransitionEnabled = false)**: Constructor of the class. The received parameters will set the value of **LoopPlayback** and **AutoTransition** properties respectively. 
    * **public HISPlayerRenderMode renderMode**: Type of texture for rendering. **HISPlayerRenderMode.NONE** by default.
    * **public Material material**: Reference to the Unity Material.
    * **public RawImage rawImage**: Reference to the Unity Raw Image.
    * **public RenderTexture renderTexture**: Reference to the Unity Render Texture.
    * **public IntPtr externalSurface**: Reference to the external surface object. (Only in SDK v4.3.2 and v4.5.2)
    * **public List \<string\> url**: List of the URLs for the stream.
    * **public list \<string\> urlMimeTypes**: List of the HISPlayerMimeTypes attached to each URL from the url list.
    * **public bool autoPlay**: If true, the players will start playing automatically after set-up.
    * **public bool EnableRendering**: Determines if the stream will be rendered or not. The value can change in every moment for toggling between render or non-render mode. If true, the player will be rendered. It only can change in runtime.
    * **public bool FlipTextureVertically**: Flip the texture of the stream vertically. This value should be called before **SetUpPlayer**  or **AddStream** functions. Only supported on Android.
    * **public bool LoopPlayback (Read-only)**: Loop the current playback. It's true by default. To modify this value, please, use the Editor or the constructor **StreamProperties(loopPlayback, autoTransition)**.
    * **public bool AutoTransition (Read-only)**: Change the playback to the next video in the playlist. This action won't have effect when loopPlayback is true. It's false by default. To modify this value, please, use the Editor or the constructor **StreamProperties(loopPlayback, autoTransition)**.
    * **public List \<string\> keyServerURI**: List of the DRM license key for each URL.
    * **public List \<DRM_Token\> DRMTokens**: List of the DRM tokens for each URL.

* **public struct DRM_Token**: Information for the DRM token:
    * **public string tokenKey**: Key of the token associated with the URL.
    * **public string tokenValue**: Value of the token associated with the key.

* **public enum HISPlayerRenderMode**: Type of texture for rendering:
    * **RenderTexture**
    * **Material**
    * **RawImage**
    * **NONE**
    * **ExternalSurface**
 
* **public enum HISPlayerMimeTypes**: The list of the supported MIME Types:
   * **URL_EXTENSION**: The MIME type will be extracted from the URL extension
   * **HLS**: The "application/x-mpegURL" MIME type will be used
   * **DASH**: The "application/dash+xml" MIME type will be used. Not supported for iOS and macOS      

* **public enum HISPlayerEvent**: The list of events provided by HISPlayer SDK. The events can be used with the virtual functions in the next section:
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
    * **HISPLAYER_EVENT_TIMELINE_UPDATED**
    * **HISPLAYER_EVENT_END_OF_CONTENT**
    * **HISPLAYER_EVENT_CACHE_PROGRESS** (Only in SDK v3.4.3)
    * **HISPLAYER_EVENT_CACHE_URL_ADDED** (Only in SDK v3.4.3)
    * **HISPLAYER_EVENT_CACHE_URL_REMOVED** (Only in SDK v3.4.3)
    * **HISPLAYER_EVENT_CACHE_FLUSH_FINISHED** (Only in SDK v3.4.3)

* **public enum HISPlayerError**: The list of errors provided by HISPlayer SDK. The errors can be used with the virtual functions in the next section:
   * **HISPLAYER_ERROR_LICENSE_EXPIRED** (no function on this)
   * **HISPLAYER_ERROR_NOT_VALID_APPID** (no function on this)
   * **HISPLAYER_ERROR_GENERAL_LICENSE_ERROR** (no function on this)
   * **HISPLAYER_ERROR_ANDROID_API_NOT_SUPPORTED** (no function on this)
   * **HISPLAYER_ERROR_LICENSE_DISABLED** (no function on this)
   * **HISPLAYER_ERROR_IMPRESSIONS_LIMIT_REACHED** (no function on this)
   * **HISPLAYER_ERROR_PLAYBACK_DURATION_LIMIT_REACHED** (no function on this)
   * **HISPLAYER_ERROR_PLATFORM_NOT_REGISTERED** (no function on this)
   * **HISPLAYER_ERROR_NETWORK_FAILED**
   
* **public struct HISPlayerEventInfo**: The information of the triggered event.
   * **public HISPlayerEvent eventType**: The type of the event triggered.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public float param1**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param2**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param3**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public float param4**: This will have different meanings depending on the event. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the event.

* **public class HISPlayerEventCacheProgress**: The information of the CacheProgress event. (Only in SDK v3.4.3)
   * **public float requestLength**: The length of the content being cached in bytes.
   * **public float bytesCached**: The number of bytes that are cached.
   * **public float newBytesCached**: The number of bytes that have been newly cached since the last progress update.

* **public class HISPlayerEventCacheURL**: The information of the Cache URL that is added or removed. (Only in SDK v3.4.3)
   * **public HISPlayerEvent eventType**: The type of the event triggered.
   * **public string url**: The URL attached to the event.

* **public struct HISPlayerErrorInfo**: The information of the triggered error.
   * **public HISPlayerError errorType**: The type of the error triggered.
   * **public int playerIndex**: The index of the player where the error is triggered.
   * **public float param1**: This will have different meanings depending on the error. If there is no information about the parameter, it will have the default value -1.
   * **public string stringInfo**: Log information about the error.

* **public struct HISPlayerTrack**:
   * **public string id**: Id of the track
   * **public int bitrate**: Bitrate of the track in bits per second.
   * **public int width**: Width of the track.
   * **public int height**: Height of the track.
   * **public int framerate**: Framerate of the track in frames per second.

* **public struct HISPlayerCaptionTrack**:
   * **public string id**: ID of the caption
   * **public string language**: Language of the caption

* **public struct HisPlayerAudioTrack**:
   * **public string id**: ID of the caption
   * **public string language**: Language of the caption
 
* **public struct HISPlayerCaptionElement**: The information of the triggered event turns into caption’s format.
   * **public int playerIndex**: The index of the player where the event is triggered.
   * **public string caption**: The next generated caption text.

## Functions
The following functions are provided by **HISPlayerManager**. They are not public so it’s necessary to create a custom script which inherits from **HISPlayerManager**.

### Virtual functions - These functions can be overridden

#### protected virtual void Awake()
MonoBehaviour function which will be called from the beginning of the scene. It can be overridden but to make the system work it’s necessary to call **base.Awake()** into the overridden function.

#### protected virtual void EventPlaybackReady(HisPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_READY** is triggered.
This event occurs when the current playback of a stream is ready to be used.
Calling functions such as GetTracks before this event is triggered will provide null information.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Number of tracks of the playback.</td>
  </tr>
</table>

#### protected virtual void EventPlaylistChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYLIST_CHANGE** is triggered.
This event occurs whenever the current playlist has been modified. It could happen when an URL has been  added or deleted.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Playlist length.</td>
  </tr>
</table>

#### protected virtual void EventVideoSizeChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_VIDEO_SIZE_CHANGE** is triggered.
This event occurs whenever the internal video size of the current track changes.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Width of the video.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Heigth of the video.</td>
  </tr>
</table>

#### protected virtual void EventPlaybackPlay(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PLAY** is triggered.
This event occurs whenever an internal playback has been played.

#### protected virtual void EventPlaybackPause(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_PAUSE** is triggered.
This event occurs whenever an internal playback has been paused.

#### protected virtual void EventPlaybackStop(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_STOP** is triggered.
This event occurs whenever an internal playback has been stopped.

#### protected virtual void EventPlaybackSeek(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_SEEK** is triggered.
This event occurs whenever an internal playback has been sought to a new time position.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Value of the old track position in milliseconds.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Value of the new track position in milliseconds.</td>
  </tr>
</table>

#### protected virtual void EventVolumeChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_VOLUME_CHANGE** is triggered.
This event occurs whenever the volume has been modified.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>New value for the volume.</td>
  </tr>
</table>

#### protected virtual void EventEndOfPlaylist(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_END_OF_PLAYLIST** is triggered.
This event occurs whenever an internal playlist reaches the end of the list.

#### protected virtual void EventOnTrackChange(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_ON_TRACK_CHANGE** is triggered.
This event occurs whenever the tracks of the stream have changed. This event is not triggered by the ABR feature.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Number of video tracks available.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Number of subtitles tracks available.</td>
  </tr>
   <tr>
    <td>param2</td>
    <td>Number of audio tracks available.</td>
  </tr>
</table>

#### protected virtual void EventOnStreamRelease(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_ON_STREAM_RELEASE** is triggered.
This event occurs whenever a player/stream has been released.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>param1</td>
    <td>Number of players after releasing.</td>
  </tr>
</table>

#### protected virtual void EventTextRender(HISPlayerCaptionElement subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_TEXT_RENDER** is triggered.
This event occurs whenever a caption's text has been generated.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>caption</td>
    <td>The next generated caption text.</td>
  </tr>
</table>

#### protected virtual void EventAutoTransition(HISPlayerCaptionElement subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayerEvent.HISPLAYER_EVENT_AUTO_TRANSITION** is triggered.
This event occurs when the playback has changed to the next video in the playlist automatically.

#### protected virtual void EventPlaybackBuffering(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPLAYER_EVENT_PLAYBACK_BUFFERING** is triggered.
This event occurs whenever an internal playback is buffering.

#### protected virtual void EventEndOfContent(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayer_EVENT_END_OF_CONTENT** is triggered.
This event occurs whenever an internal playback reaches the end of the video content.

#### protected virtual void EventNetworkConnected(HISPlayerEventInfo subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayerEvent.HISPLAYER_EVENT_NETWORK_CONNECTED** is triggered.
This event occurs whenever the network has been reconnected.

#### protected virtual void EventTimelineUpdated(HISPlayerEventInfo subtitlesInfo)
Override this method to add custom logic when **HISPlayerEvent.HISPlayerEvent.HISPLAYER_EVENT_TIMELINE_UPDATED** is triggered.
This event occurs whenever the timeline of the current video has been updated. In the case of live content this may happen every certain time during the playback. This may change the current video position value from GetVideoPosition().

#### protected virtual void EventCacheProgress(HISPlayerEventCacheProgress cacheProgress)
Only in SDK v3.4.3. Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_PROGRESS** is triggered. 
This event occurs whenever there is a process of caching a certain URL. It shows the progress data of the current cache operation.

#### protected virtual void EventCacheURLAdded(HISPlayerEventCacheURL cacheURL)
Only in SDK v3.4.3. Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_URL_ADDED** is triggered.
This event occurs whenever the current cache operation has finished of adding the URL to the cache.

#### protected virtual void EventCacheURLRemoved(HISPlayerEventCacheURL cacheURL)
Only in SDK v3.4.3. Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_URL_REMOVED** is triggered.
This event occurs whenever the current cache operation has finished of removing the URL from cache.

#### protected virtual void EventCacheFlushed(HISPlayerEventInfo eventInfo)
Only in SDK v3.4.3. Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_FLUSH_FINISHED** is triggered.
This event occurs whenever the cache data has been flushed.

#### protected virtual void ErrorInfo(HISPlayerErrorInfo errorInfo)
Override this method to add custom logic when an error callback is triggered. Please, refer to the **HISPlayerError** list.

#### protected virtual void ErrorNetworkFailed(HISPlayerErrorInfo errorInfo)
Override this method to add custom logic when **HISPlayerError.HISPLAYER_ERROR_NETWORK_FAILED** is triggered.
This error occurs when the Internet connection fails.

### Non-virtual functions 
These functions can’t be overridden and they can be used only inside the inherited script. If it’s needed to use some of these functions into the Unity scene, for example with buttons, it is needed to create a public function which connects the button with the API.

#### protected void SetUpPlayer()
Initialize the player video stream system internally. It is necessary to use this function before anything else.

#### protected void Release()
Free all resources internally. In the SDK v4.3.0 and below, it's necessary to call this function before changing between Unity scenes or before quitting the application. In the SDK v4.4.0 and above, the release is called automatically when changing scenes or quitting the application and it's not required to call this function. 

#### protected void Play(int playerIndex)
Play a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Pause(int playerIndex)
Pause a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Stop(int playerIndex)
Stop a certain stream giving a **playerIndex**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void Seek(int playerIndex, long milliseconds)
Seek a certain stream to a certain time giving a **playerIndex** and the time of the track to be sought in **milliseconds**. The stream is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetVolume(int playerIndex, float volume)
Modify the volume of a certain stream giving a **playerIndex**. The **volume** of the track value ranges between 0.0f and 1.0f. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void AddStream(StreamProperties newStream)
Add a new stream to the list multiStreamProperties. The stream must be added using this function instead of changing the list manually.

#### protected void AddVideoContent(int playerIndex, string url, HISPlayerMimeTypes mimeType = HISPlayerMimeTypes.URL_EXTENSION (optional))
Add new content to a certain player. If the **enableDRM** variable is true, a video content with an empty license will be added. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The **url** is the link to the new video. Please, make sure the string is correct. This function supports local file paths. The parameter **mimeType** is optional and indicates which MIME type will be used for the new url.

#### protected void AddVideoContent(int playerIndex, string url, string keyServerUri,  string tokenKey = “” (optional), string tokenValue = “” (optional), HISPlayerMimeTypes mimeType = HISPlayerMimeTypes.URL_EXTENSION(optional))
Add new content to a certain player and its respective key server uri and tokens if needed (tokenKey and tokenValue are optional parameters). The **enableDRM** variable must be true for using this function. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The **url** is the link to the new video. The **keyServerUri** is the license key associated with the URL. Please, make sure the string is correct. This function supports local file paths. The **mimeType** parameter is optional and indicates which MIME type will be used for the new url.

#### protected void ChangeVideoContent(int playerIndex, int urlIndex)
Change the video’s URL  of a certain player. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The **urlIndex** is associated with the index of the element in the list of URLs.

#### protected void ChangeVideoContent(int playerIndex, string url)
Change the video’s URL of a certain player given a new URL. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The parameter **url** is the link to the new video. Please, make sure the new URL is correctly written. This function supports local file paths. This function will replace the Playlist with the new URL.

#### protected void ChangeVideoContent(int playerIndex, string url, HISPlayerMimeTypes mimeType)
Change the video’s URL of a certain player given a new URL. The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The parameter **url** is the link to the new video. Please, make sure the new URL is correctly written. This function supports local file paths. This function will replace the Playlist with the new URL. The **mimeType** indicates which MIME type will be used for the new url.

#### protected void ChangeVideoContent(int playerIndex, string url, string keyServerUri, string tokenKey = “” (optional), string tokenValue= “” (optional), HISPlayerMimeTypes, mimeType = HISPlayerMimeTypes.URL_EXTENSION(optional))
Change the video’s URL of a certain player given a new URL with DRM protection (tokenKey and tokenValue are optional parameters). The next playback will start paused if **autoPlay** is disabled. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list. The parameter **url** is the link to the new video. The **keyServerUri** is the license key associated with the URL. Please, make sure the parameters are correctly written. This function supports local file paths. This function will replace the Playlist with the new element. The **mimeType** parameter is optional and indicates which MIME type will be used for the new url.

#### protected void RemoveVideoContent(int playerIndex, int urlIndex)
Remove content from a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.  The **urlIndex** is associated with the index of the element in the list of URLs.

#### protected void RemoveStream(int playerIndex)
Remove a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetPlaybackSpeedRate(int playerIndex, float speed)
Modify the **speed rate** of a certain stream giving a **playerIndex**. The value of the player's speed must be greater (>) than 0.0f and less than or equal (<=) to 8.0f. The default value of player's speed is 1.0f. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected float GetPlaybackSpeedRate(int playerIndex)
Obtain the **speed rate** of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoPosition(int playerIndex)
Provides information about the timeline position in **milliseconds**, of the current video of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected long GetVideoDuration(int playerIndex)
Provides information about the total duration in **milliseconds**, of the current video of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected HISPlayerTrack[] GetTracks(int playerIndex)
Provides the list of the video tracks of the current video playing on a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackBitrate(int playerIndex, int trackIndex)
Get the bitrate of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackWidth(int playerIndex, int trackIndex)
Get the width of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackHeight(int playerIndex, int trackIndex)
Get the height of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 of the list.

#### protected int GetVideoWidth(int playerIndex)
Get the width of the current track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetVideoHeight(int playerIndex)
Get the height of the current track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackID(int playerIndex, int trackIndex)
Get the ID of a certain track of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected int GetTrackCount(int playerIndex)
Get the number of tracks of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public void EnableCaptions(int playerIndex, bool enabled)
Enables the captions of the stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public HISPlayerCaptionTrack[] GetCaptionTrackList(int playerIndex)
Provide information about all the captions of a certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public int GetCaptionsCount(int playerIndex)
Obtain the number of captions of a  certain stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionID(int playerIndex, int ccTrackIndex)
Obtain the ID of a certain caption of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public string GetCaptionLanguage(int playerIndex, int ccTrackIndex)
Obtain the language of a certain caption of a certain player. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### public void SelectCaptionTrack(int playerIndex, int ccTrackIndex)
Select a certain caption of a certain stream to be used. Before using this functions is recommended to use GetCaptionTrackList in order to know all the information about the captions. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetMaxBitrate(int playerIndex, int bitrate)
Set a new maximum bitrate (in bits per second) of a specific track. This doesn't disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetMinBitrate(int playerIndex, int bitrate)
Set a new minimum bitrate (in bits per second) of a specific track. This doesn't disable ABR. The possible tracks can be obtained from the tracks returned from the method GetTracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SelectTrack(int playerIndex, int trackIndex)
Select a certain track of a certain stream to be used as the main track. This action will disable ABR, to enable it again you can use **EnableABR** API. The possible tracks can be obtained from the tracks returned from the method **GetTracks**. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void SetDecodedFrameBufferEnabled(bool enable, int playerIndex = 0 (optional))
Enable the Decoded Frame Buffer Functionality. This function can be called independently of the SetUp function. This functionality can only be called for one single stream. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected async Task<Texture2D> GetDecodedFrameAtTimestamp(int msec, bool deletePreviousFrames = true (optional))
Retrieves the Texture2D of the requested frame or null if the frame is not available for the given timestamp (parameter msec in milliseconds).

#### protected Vector2Int GetDecodedFrameBufferRange()
Retrieves the range of the Decoded Frame Buffer in milliseconds. The X value of the Vector2Int corresponds to the timestamp in milliseconds of the oldest frame stored in the buffer, while the Y value corresponds to the newest.

#### protected int GetNetworkBandwidth()
Returns the current network bandwidth. This value is an estimation in kbps.
   
#### public HisPlayerAudioTrack[] GetAudioTrackList(int playerIndex)
Provide information about all the audio tracks of a certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### public int GetAudioCount(int playerIndex)
Obtain the number of audio of a  certain stream. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.
   
#### public string GetAudioID(int playerIndex, int audioTrackIndex)
Obtain the ID of a certain audio of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected string GetAudioLanguage(int playerIndex, int audioTrackIndex)
Obtain the language of a certain audio of a certain player. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void SelectAudioTrack(int playerIndex, int audioTrackIndex)
Select a certain audio-track of a certain stream to be used. Before using this functions is recommended to use GetAudioTrackList in order to know all the information about the audio-tracks. The playerIndex is associated with the index of the element of Multi Stream Properties, e.g. the index 0 is the element 0 in the list.

#### protected void EnableABR(int playerIndex)
Enables the ABR to change automatically between tracks. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void DisableABR(int playerIndex)
Disables the ABR to prevent the player from changing tracks regardless of bandwidth. The **playerIndex** is associated with the index of the element of **Multi Stream Properties**, e.g. the index 0 is the element 0 in the list.

#### protected void InitCacheInstance(long maxCacheSize = 150 * 1024 * 1024L)
Only in SDK v3.4.3. Initialize the Cache Instance in order to use all the cache API. It can be called before or after SetUpPlayer(). In the case of overriding the Awake() function, InitCacheInstance must be called after calling base.Awake(). The maxCacheSize indicates the maximum permitted size by the cache in bytes. 150 MB will be set by default (150 * 1024 * 1024L bytes).

#### protected void AddURLToCache(string url)
Only in SDK v3.4.3. The cache must be initialized before using this function. Given the URL, a miminum amount of data will be stored in cache in order to initialize the video faster when it's needed. Once the video is loaded and played, it will continue caching the remaining fragments of the video. Live and Local video contents are not supported. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy.

#### protected void RemoveURLFromCache(string url)
Only in SDK v3.4.3. The cache must be initialized before using this function. Removes the given URL from the cache if exists. Live and Local video contents are not supported. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy so it's possible the cached data from AddUrlToCache doesn't exist anymore.

#### protected bool IsURLCached(string url)
Only in SDK v3.4.3. The cache must be initialized before using this function. Determines if the given URL is cached. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy so it's possible the cached data from AddUrlToCache doesn't exist anymore.
  
#### protected long GetRemainingCacheSpace() 
Only in SDK v3.4.3. The cache must be initialized before using this function. Retrieves the remaining cache space in bytes.

#### protected void FlushCacheFolder()
Only in SDK v3.4.3. The cache must be initialized before using this function. Free the cache folder. If a video was loaded from using the cache data, it will continue downloading the new fragments into the cache folder after the flushing is completed.
