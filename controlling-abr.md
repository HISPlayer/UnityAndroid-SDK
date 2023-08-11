# Controlling ABR

There are 3 ways to work with ABR (Adaptive Bitrate) : 
1. Automatic ABR
2. ABR with maximum and minimum resolution
3. No ABR, one track selected only

## Automatic ABR
The player automatically takes the highest video quality from the available resolutions based on the network condition. Automatic ABR is enabled by default.

## ABR with Maximum and Minimum Resolution
Given the *maximum* and *minimum* bitrate values, the player automatically adjusts the video quality from the available resolutions within the range of *minimum* and *maximum* bitrates.

To set the maximum bitrate to be used, please refer to the following API : 

[**protected void SetMaxBitrate(int playerIndex, int bitrate)**](./hisplayer-api.md#protected-void-setmaxbitrateint-playerindex-int-bitrate)

To set the minimum bitrate to be used, please refer to the following API : 

[**protected void SetMinBitrate(int playerIndex, int bitrate)**](./hisplayer-api.md#protected-void-setminbitrateint-playerindex-int-bitrate)

## No ABR
ABR is disabled and the player selects single resolution. To disable ABR and select specific resolution, please refer to the following API : 

[**protected void SelectTrack(int playerIndex, int bitrate)**](./hisplayer-api.md#protected-void-selecttrackint-playerindex-int-bitrate)

If you need to re-enable ABR after disabling it, you need to set the minimum and maximum bitrate values by calling [SetMinBitrate(int playerIndex, int bitrate)](./hisplayer-api.md#protected-void-setminbitrateint-playerindex-int-bitrate) and [SetMaxBitrate(int playerIndex, int bitrate)](./hisplayer-api.md#protected-void-setmaxbitrateint-playerindex-int-bitrate) . 
Please refer to the previous section :  [ABR with Maximum and Minimum Resolution](#abr-with-maximum-and-minimum-resolution)
