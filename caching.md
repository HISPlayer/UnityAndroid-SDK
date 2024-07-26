# Caching

HISPlayer Android for Unity supports caching for HLS, DASH and Progressive Download(mp4) URLs to load the video faster from the cache. Caching is supported in **SDK v3.4.3**. 

## Related APIs

#### protected void InitCacheInstance(long maxCacheSize = 150 * 1024 * 1024L)
Initialize the Cache Instance in order to use all the cache API. It can be called before or after SetUpPlayer(). In the case of overriding the Awake() function, InitCacheInstance must be called after calling base.Awake(). The maxCacheSize indicates the maximum permitted size by the cache in bytes. 150 MB will be set by default (150 * 1024 * 1024L bytes).

#### protected void AddURLToCache(string url)
The cache must be initialized before using this function. Given the URL, a miminum amount of data will be stored in cache in order to initialize the video faster when it's needed. Once the video is loaded and played, it will continue caching the remaining fragments of the video. Live and Local video contents are not supported. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy.

#### protected void RemoveURLFromCache(string url)
The cache must be initialized before using this function. Removes the given URL from the cache if exists. Live and Local video contents are not supported. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy so it's possible the cached data from AddUrlToCache doesn't exist anymore.

#### protected bool IsURLCached(string url)
The cache must be initialized before using this function. Determines if the given URL is cached. In the case the cache folder is full, the least recently used old files will be removed when new data is downloaded following the Least Recently Used (LRU) cache policy so it's possible the cached data from AddUrlToCache doesn't exist anymore.
  
#### protected long GetRemainingCacheSpace() 
The cache must be initialized before using this function. Retrieves the remaining cache space in bytes.

#### protected void FlushCacheFolder()
The cache must be initialized before using this function. Free the cache folder. If a video was loaded from using the cache data, it will continue downloading the new fragments into the cache folder after the flushing is completed.

### Properties

* **public class HISPlayerEventCacheProgress**: The information of the CacheProgress event.
   * **public float requestLength**: The length of the content being cached in bytes.
   * **public float bytesCached**: The number of bytes that are cached.
   * **public float newBytesCached**: The number of bytes that have been newly cached since the last progress update.

* **public class HISPlayerEventCacheURL**: The information of the Cache URL that is added or removed.
   * **public HISPlayerEvent eventType**: The type of the event triggered.
   * **public string url**: The URL attached to the event.

### Events and Virtual Functions

* **public enum HISPlayerEvent**: The list of events provided by HISPlayer SDK. The events can be used with the virtual functions:
    * **HISPLAYER_EVENT_CACHE_PROGRESS**
    * **HISPLAYER_EVENT_CACHE_URL_ADDED**
    * **HISPLAYER_EVENT_CACHE_URL_REMOVED**
    * **HISPLAYER_EVENT_CACHE_FLUSH_FINISHED**

#### protected virtual void EventCacheProgress(HISPlayerEventCacheProgress cacheProgress)
Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_PROGRESS** is triggered. 
This event occurs whenever there is a process of caching a certain URL. It shows the progress data of the current cache operation.

#### protected virtual void EventCacheURLAdded(HISPlayerEventCacheURL cacheURL)
Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_URL_ADDED** is triggered.
This event occurs whenever the current cache operation has finished of adding the URL to the cache.

#### protected virtual void EventCacheURLRemoved(HISPlayerEventCacheURL cacheURL)
Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_URL_REMOVED** is triggered.
This event occurs whenever the current cache operation has finished of removing the URL from cache.

#### protected virtual void EventCacheFlushed(HISPlayerEventInfo eventInfo)
Override this method to add custom logic when **HISPLAYER_EVENT_CACHE_FLUSH_FINISHED** is triggered.
This event occurs whenever the cache data has been flushed.

## Cache Sample

Please go to [Cache Sample](https://hisplayer.github.io/UnitySamples/#/hisplayer-cache-sample). The sample is intended to show a comprehensive scene using the HISPlayer SDK to help demonstrate the cache features.
