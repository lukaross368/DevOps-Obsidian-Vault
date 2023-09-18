#devops #systemDesign #caching

### What is Caching? 

A cache stores previously used or computed data in a high-speed data store to make it more rapidly available than in the main storage layer. Generally we would use hardware such as RAM.

Here are some benefits of caching:

- **Reduce database costs**: If your DB implementation charges per IOPS (input/output per second) then a cache can help reduce this.
- **Reduce backend load**: If the same query is bombarding the backend then by implementing a cache we reduce this load. (This works in conjunction with the above point since it allows our main datastore to be smaller) 
- **Improve application performance**: cached results are much quicker to retrieve
- **Predictable performance**: High traffic events on traditional datastores can cause locking and other performance bottlenecks. By having a high throughput cache this can be reduced.
- **Eliminate database hotspots**: Some data in our DB may be more frequently accessed than others. It doesn't make sense to scale our whole database purely based on this.

Here are some Common Use cases:

#### CDN Caching

A CDN (content delivery network) is a number of servers spread over the globe in order to provide fast delivery of content on the internet. It allows for effective loading of internet content assets such as HTML, CSS, JavaScript, Videos and Images.

For example if our server is hosted in London, this means load times when accessing content on our server will be slow if its being accessed from Philadelphia. By having a Point of Presence (POP) or edge server in New York that our Site assets replicated on, we can deliver content to Philadelphia more quickly. 

[[AWS]] offer a CDN called [[CloudFront]]. CloudFront servers act as a cache by sitting at edge locations and serving up cached versions of assets. 
#### DNS Caching

[[DNS]]

#### Web Caching

#### Session Cache

#### Database Cache

In memory caching can help alleviate some of the pressures on your DB. If you have a frequently accessed, read only data then it makes sense to store this in a cache instead of on your persistent storage. This can be done on the database itself, locally on your application servers, or like sessions it can use a dedicated caching layer. 

By caching on the database we can have write-through (how updated data affects our cached values) handled automatically. However, the cache will sit on the same server as our database, meaning it will need to be scaled with the whole database engine.

By caching on our application servers we alleviate some of these issues, however we now only have access to cache on one node, which we will lose if it goes down.

A dedicated caching layer combats this, but introduces latency as requests must be made. For this and the previous solution we also face the problem of updating cache values when data is updated. A tricky logic!

![[Caching.png]]

A great in-memory database (see [[Databases]]) for DB caching is [[Redis]].

#### General Cache

### Quick Note on Getting Data out of Cache
