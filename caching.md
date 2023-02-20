<!-- caching -->
# Caching

The cache is a smaller and faster memory that stores copies of the frequently used data. Content like HTML pages, images, files, web objects, etc is stored in the cache to improve the efficiency and overall performance of the application.

A cache is typically stored in memory or on a disk. A memory cache is normally faster to read from than a disk cache. But, does not survive when system restarts.(1)

**The process of storing and accessing data from a cache is known as caching.**(2)

Caches are widely used in most of the high volume applications to:
* Reduce Latency
* Increase Capacity
* Improve App Availability

## Types of Caching
There are four types of caching:

* In-memory Caching
* Database Caching
* Web Caching
* CDN Caching

### In-memory Caching:

In this caching approach, cached data is stored directly in RAM, which is faster than the typical storing system where the original data is located. The most common implementation of this type of caching is based on key-value (dictionary) databases. They can be seen as sets of key-value pairs. The key is represented by a unique value, while the value by the cached data. This means that each piece of data is identified by a unique value. By specifying this value, the key-value database will return the associated value. Such a solution is fast, efficient, and easy to understand.(3)

### Database Caching:

Each database have some level of caching. Specifically, an internal cache is generally used to avoid querying a database excessively. By caching the result of the last queries executed, the database can provide the data previously cached immediately. This way, for the period of time the database can avoid executing queries.

### Web Caching :

Caching web content helps improve upon the responsiveness of your websites by reducing the load on backend resources and network congestion. Web caching is performed by retaining HTTP responses and web resources in the cache for the purpose of fulfilling future requests from cache rather than from the origin servers.(4)

### CDN (Content Delivery Network) Caching :

* A CDN is a distributed server network that delivers temporarily stored, or cached, copies of website content to users based on the user’s geographic location.
* A CDN stores this content in distributed locations and serves it to users as a way to reduce the distance between your website visitors and your website server. Having cached content closer to your end users allows you to serve content faster and helps websites better reach a global audience.
* CDNs protect against traffic surges, reduce latency, decrease bandwidth consumption, accelerate load times, and lessen the impact of hacks and attacks by introducing a layer between the end user and your website infrastructure.(5)

![](https://awesome-tech.readthedocs.io/images/incapsula_cdn_caching.png)(6)

## What are the top caching strategies?

A caching strategy is to determine the relationship between data source and your caching system, and how your data can be accessed. There are various strategies to implement cache but each will have different impacts on your system design and the resulted performance.(7)

* ### Cache Aside
    In this strategy, the cache is sitting aside the database. The application will first request the data from the cache. If the data exists (this is called as ‘cache hit’), the app will retrieve the data directly. If not (this is called as ‘cache miss’), the app will request data from the database and write it to the cache so that the data can be retrieved from the cache again next time.

* ### Read Through
    The application only request data from the cache. If a ‘cache miss’ occurs, the cache is responsible to retrieve data from the database, update itself and return data to the application. This is called read throug.

* ### Write Through
    Similar to read through, Every writes from the application must go through the cache to the database.

* ### Write Back
    It has a similar setup with write through. The application still writes data to the cache. However, there is a delay in writing from the cache to the database. The cache only flushes all updated data to the database once in a while (e.g. every 5 minutes).

* ### Write Around
    Write around usually combines with either cache aside or read through strategy. Here data is directly written/updated to the database without disturbing the cache. It is better to use this when the data is not immediately used again.

![](https://miro.medium.com/max/1400/1*U3DIa03Stqf-28CS41BUgg.png)(8)



## References

1. [https://bootcamp.uxdesign.cc/caching-techniques-one-should-know-603e09d2b298](https://bootcamp.uxdesign.cc/caching-techniques-one-should-know-603e09d2b298)

1. [https://www.tutorialspoint.com/What-is-caching#:~:text=Cache%20is%20a%20type%20of,cache%20is%20known%20as%20caching](https://www.tutorialspoint.com/What-is-caching#:~:text=Cache%20is%20a%20type%20of,cache%20is%20known%20as%20caching)

1. [https://auth0.com/blog/what-is-caching-and-how-it-works/](https://auth0.com/blog/what-is-caching-and-how-it-works/)

1. [https://aws.amazon.com/caching/database-caching/](https://aws.amazon.com/caching/database-caching/)

1. [https://www.ibm.com/cloud/learn/networking-a-complete-guide?cm_mmc=OSocial_Youtube-_-Hybrid+Cloud_Cloud+Platform+Digital-_-WW_WW-_-CDNYTDescription&cm_mmca1=000016GC&cm_mmca2=10007981](https://www.ibm.com/cloud/learn/networking-a-complete-guide?cm_mmc=OSocial_Youtube-_-Hybrid+Cloud_Cloud+Platform+Digital-_-WW_WW-_-CDNYTDescription&cm_mmca1=000016GC&cm_mmca2=10007981)

1. [https://awesome-tech.readthedocs.io/images/incapsula_cdn_caching.png](https://awesome-tech.readthedocs.io/images/incapsula_cdn_caching.png)

1. [https://blog.bluzelle.com/things-you-should-know-about-database-caching-2e8451656c2d](https://blog.bluzelle.com/things-you-should-know-about-database-caching-2e8451656c2d)

1. [https://miro.medium.com/max/1400/1*U3DIa03Stqf-28CS41BUgg.png](https://miro.medium.com/max/1400/1*U3DIa03Stqf-28CS41BUgg.png)

1. [https://youtu.be/6FyXURRVmR0](https://youtu.be/6FyXURRVmR0)

1. [https://youtu.be/U3RkDLtS7uY](https://youtu.be/U3RkDLtS7uY)