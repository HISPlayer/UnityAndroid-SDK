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
    * RenderTexture
    * Material
    * RawImage
    * NONE

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

