# Content Delivery Network(CDNs)


A Content Delivery Network, or CDN, is a network of servers strategically placed around the world to provide efficient and fast delivery of internet content. It's a system designed to solve the inherent issues of latency in the loading of web pages, particularly for users geographically distant from the source server.

The main purpose of a CDN is to increase speed and reliability for end users by distributing and delivering content more directly and quickly to them based on their geographic location. This is achieved by caching the content at various points in the network, known as edge servers. When a user requests content that has been cached on an edge server, it is delivered directly from the closest server rather than the origin server.

This has several benefits:

Speed: By serving content closer to the user's location, CDNs can significantly reduce page load times.

Reduced Bandwidth Costs: CDNs can help minimize data transfer costs for website owners by caching and optimizing content.

Scalability: CDNs are designed to handle traffic spikes and heavy loads, reducing the risk of website downtime.

Security: CDNs can provide additional security measures such as DDoS protection and other optimization features that can help protect the integrity and performance of websites.

Popular examples of CDNs include Cloudflare, Amazon CloudFront, Akamai, and Fastly. CDNs are commonly used by high-traffic websites, e-commerce platforms, media and entertainment companies, and any organization that has a substantial online presence or caters to a global audience.

- Geographically distributed fleet of servers that serves mostly static data from your website
- local hosting of HTML/CSS/JS/Images (Static things), it will available in different region for
different people accessing it, so that you can avoid latency problem...

For Example: if person from india is accessing html or static content there then it should be
fetching that data from the CDN server located there... this can make your website faster 
- Some limited computation may be available as well.
- But mainly important for static content

**Disadvantages**:

- CDN can be expensive some times

## CDN Providers

- AWS CloudFront
- Google Cloud CDN
- Microsoft Azure CDN
- CloudFlare