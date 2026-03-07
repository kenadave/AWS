1) Q. What can I do with Amazon CloudFront?
Amazon CloudFront provides a simple way to:

Deliver fast, secure websites: Reach viewers across the globe in milliseconds with built-in data compression, edge compute capabilities, and field-level encryption.

Accelerate dynamic content delivery and APIs: Optimize dynamic web content delivery with the purpose-built and feature-rich Amazon Web Services network infrastructure supporting edge termination and WebSockets.

Stream live and on-demand video: Start streams quickly, play them with consistency, and deliver high-quality video to any device with Amazon Web Services Media Service and AWS Elemental integration.

Distribute patches and updates: Scale automatically to deliver software, game patches, and IoT over-the-air (OTA) updates at scale with high transfer rates.

2) For every origin that you add to a CloudFront distribution, you can  assign a backup origin  that can be used to automatically serve your traffic if the primary origin is unavailable. You can choose a combination of HTTP 4xx/5xx status codes that, when returned from the primary origin, trigger the failover to the backup origin. The two origins can be any combination of Amazon Web Services and non- Amazon Web Services origins.

3) Amazon CloudFront establishes WebSocket connections only when the client includes the 'Upgrade: websocket' header and the server responds with the HTTP status code 101 confirming that it can switch to the WebSocket protocol.

4) Field-Level Encryption is a feature of CloudFront that allows you to securely upload user-submitted data such as credit card numbers to your origin servers.

5) Amazon CloudFront supports delivery of dynamic content that is customized or personalized using HTTP cookies. To use this feature, you specify whether you want Amazon CloudFront to forward some or all of your cookies to your custom origin server. Amazon CloudFront then considers the forwarded cookie values when identifying a unique object in its cache. This way, your end users get both the benefit of content that is personalized just for them with a cookie and the performance benefits of Amazon CloudFront. You can also optionally choose to log the cookie values in Amazon CloudFront access logs.

6) Yes, the query string whitelisting feature allows you to easily configure Amazon CloudFront to only use certain parameters in the cache key, while still forwarding all of the parameters to the origin.

7) Yes, you can configure Amazon CloudFront to white list up to 10 query parameters.

8) 
