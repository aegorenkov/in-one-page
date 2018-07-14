# System Design
Every choice is a trade-off so there is little room for opinionated thinking. Gauge every tool and technique in context and evaluate based on how well core system needs are fulfilled.

## Influences and constraints on design decisions
- **Personalization:** Cache is less effective when all content needs to be dynamic.
- **Uptime:** Technology eventually breaks forcing the need for redundancy and removing single points of failure.
- **Latency:** Users want responsive products forcing *acceptable* latency when servers are under load.
- **Throughput:** We need to have a rough idea of how many users we can support with acceptable latency.
- **Memory use:** Every part of the system has finite memory resources that we cannot overload.
- **CPU use:** Every part of the system has finite CPU resource that we cannot overload.

## Common tools to over come design constraints
- **DNS:** Allows regional routing of requests
- **Web Server:** Server that responds to client requests.
  - Optimize by: Gzip compression; CDN; Load Balancer; Take advantage of browser caching with HTTP headers.
- **Application Server:** Server resonsible for responding to dynamic requests that are difficult to fully cache.
  - Optimize by: Load balancer; Cache responses, fragments, or data; Optimize code by removing unnecesary operations; Queue write queries to manage server load.
- **Database:** Needed to persist data in between user sessions.
  - Optimize by: Upgrade versions for up-to-date algorithms; tune database settings; make sure OS and hardware are setup correctly; use database indexes to reduce read times but increase memory use and slow down write times; denormalization to reduce read and write times, but increase complexity and memory use, replication to scale reads, use federation partially scale reads and writes and allow further optimization, use sharding to scale reads and writes at the cost of complexity.
- **CDN:** Cache and serve static files. Many CDNs will also help optimize latency through regional routing.
- **Load Balancer:** Horizontal scaling of CPU and Memory by routing requests to multiple machines.
- **Cache:** Optimize how static or slowly changing content/data is read.
- **Write Queue:** Use asynchronous processing to optimize how data is written.
