# Caching:


Caching, in the context of system design, is a technique used to store copies of frequently accessed data in a location that can be retrieved quickly. The purpose of caching is to improve the performance and efficiency of a system by reducing the time it takes to fetch the data from its primary storage location.

Here are a few key aspects of caching in system design:

`Temporal Locality`: Caching utilizes the concept of temporal locality, which is the idea that if a particular piece of data is accessed at one point in time, it's likely to be accessed again in the near future. By storing this data in a cache, future requests for the same data can be served faster.

`Spatial Locality`: Another related concept is spatial locality, where if one piece of data is accessed, the data located near it is likely to be accessed soon. This concept is often used in caching algorithms to predict what data to cache.

`Cache Invalidation`: One of the challenges in caching is knowing when to remove data from the cache, particularly when the original data changes. This is known as cache invalidation. Common strategies include time-based expiration, where data is removed after a certain amount of time, and write-through, where changes to data are written to both the cache and the primary storage.

`Cache Types`: There are many types of caches in system design, including memory cache, disk cache, and database cache. Each serves a different purpose and can be utilized in different layers of a system. For instance, a web application might use memory cache to store session information, disk cache to store static files, and database cache to store query results.

`Cache Eviction Policies`: These are strategies that determine which items to remove from the cache when it becomes full. Common policies include Least Recently Used (LRU), where the items that haven't been accessed for the longest time are removed first, and Least Frequently Used (LFU), where the items that are used least frequently are removed first.

`Distributed Caching`: In a distributed system, caching can be complex because the same piece of data can be cached in multiple locations. Techniques like distributed cache (e.g., Memcached, Redis) can help coordinate caches across multiple machines, ensuring consistency and improving performance.

`Caching at Different Layers`: In a typical web application, caching could be implemented at various layers. There might be caching at the browser level, CDN caching for static content delivery, reverse proxy caches (like Varnish), and server-side application caches. Each layer can contribute to reducing server load and improving response times, but each comes with its complexities and must be managed appropriately.

Remember, while caching can significantly improve system performance, it should be implemented with care. Over-reliance on caching can lead to complexities like stale data and increased difficulty in managing state. Also, cache misses (when requested data isn't found in the cache) can cause performance issues if not handled correctly.

## How caches and why caches:

- Can have separate horizonatally scaled served dedicated to for caching
- Client Hash requests to a given server
- In memory(fast)
- Important for machines that have more reads than writes, because in case of writing it invalidate caches
- Expiration policy would determine how long the data should be cached
- Hotspots can be problem, how to deal with the scenario when only one sort of data is being used a lot, for example if something is trending then everyone might try to access that... This problem is also known as celebrities problem.
- Cold start problem: when cache server has been just created then there would be no cache at that time. But until that server gets warmup all of your queries will directly hit database, which might crash your database

## Eviction Policies:

Eviction policies are basically used to decide which cache would be kept on server and which one will be discarded in case if memory gets full.

- LRU: Least Recently Used, kind of the data that was used least in the cache memory will be discarded first.

[Just check if item exists in cache, if yes then put that at head point, rest of the items will
be automatically repositioned, and if its new then remove the tail item and last one].

- LFU: In lfu, least frequently used item will be removed from cache... To do so you have to keep count
of frequency how quickly they were accessed.

[There would be one problem with newly added items that they will not be upto the count of old items,
and will start from 0, to deal with such problems, we have different options e.g.]

`Decaying LFU`: Instead of simply counting the total number of accesses, this variant of LFU reduces the value of the counts over time, making recent accesses more valuable than older ones. For example, every time an access is made, all counts could be multiplied by a factor less than 1, then the count for the accessed item is incremented by 1. This allows items that are accessed frequently in recent times to have a higher count than items that were accessed frequently in the past but not recently.

`Segmented LFU (SLFU)`: This is a more advanced cache algorithm that combines the LFU and LRU ideas. The cache is divided into two segments: a probationary segment for new entries (handled by LRU) and a protected segment for entries that have been accessed more than once. This way, new entries have a chance to prove their "worth" before being evicted, and the problem of new entries being quickly evicted is solved.

`Count-Min Sketch technique with LFU`: This is a probabilistic data structure that serves as a frequency table of events in a stream of data. It uses hash functions to map events to frequencies. Although there can be collisions where different events are mapped to the same frequency, it tends to be rare if the table size and number of hash functions are chosen appropriately. When used with LFU, it provides a space-efficient way to estimate the frequencies of different events.

`Aging`: This technique periodically decrements the counters of all pages in the cache, thus lowering the impact of historical page references. This can also be thought of as a way of "forgetting" about older accesses over time.
