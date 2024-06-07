# DRM

In the video streaming industry, the DRM (Digital Rights Management) makes possible a secure distribution of contents over the network.
Encrypted content is prepared using an encryption server and stored in a content library. The encrypted content is streamed or downloaded from the content library to client devices via content servers. Licenses to view the content are obtained from the License Server.

The HISPlayer Unity Video Player SDK for Android supports [Widevine DRM](https://www.widevine.com/solutions/widevine-drm) and provides an API to the users for usage of the MediaDRM module. Only Widevine with security L3 is supported.

Use **Multi Stream Properties** to set the DRM fields. It is possible to add license keys both in the editor and from code (see AddStream and AddVideoContent in [HISPlayer API](/hisplayer-api.md) for more details):

* <span style="color:blue">**Enable DRM**</span>: Check to enable DRM usage. When enabled, there should be one license key URI per content URL even though the content is clear (empty license key URI). This field will have effect during the AddVideoContent functionality.
* <span style="color:blue">**Key Server URI**</span>: Add license URLs for DRM-protected contents. There must be one license key URL per content URL when the “Enable DRM” is checked.
* <span style="color:blue">**DRM Tokens**</span>: If your key server needs more information, add drm tokens for DRM-protected contents alongside the respective Key Server URI. There must be one token per key server uri when the “Enable DRM” is checked. The tokens are composed of a Key and a Value. This field will have effect during the AddVideoContent functionality.

You may find the Widevine DRM video content URL and the key server URL sample here: [Widevine DRM Sample](https://integration.widevine.com/player). Then you can input the URLs in the **Multi Stream Properties** like image below:
<p align="center">
<img src="https://github.com/HISPlayer/UnityAndroid-SDK/assets/32887298/82aaba44-ee4e-4004-9fdd-8a733fe025b2">
</p>

Belos is an example of the usage of the DRM fields in the editor with different properties of each video stream:
* There are 3 URLs:
  * VIDEO CONTENT 1 CLEAR
  * VIDEO CONTENT 2 DRM
  * VIDEO CONTENT 3 DRM + TOKEN
* The 'enableDRM' field is checked.
* There are 3 elements in Key Server URI list:
  * The first one is empty, because the first content is clear
  * The second and the third elements have their respective license key
* There are 3 elements in DRM Tokens list:
  * The first and the second elements are empty because URLs don't require DRM tokens.
  * The third element is protected both with a license key and token.

<p align="center">
<img src="./assets/drm.png">
</p>

