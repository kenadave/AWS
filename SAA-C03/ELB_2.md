Perfect 👍 let’s map the protocols (L4 vs L7) to AWS Load Balancer types.


---

🔹 1. Application Load Balancer (ALB) → Layer 7

Works with application protocols:

HTTP

HTTPS (TLS termination supported)

WebSockets (because they start as HTTP and then upgrade)


Features: Path-based routing (/app1 vs /app2), host-based routing (api.example.com vs shop.example.com), sticky sessions, header-based rules.

Can inspect request content before routing.


💡 Example: GET /orders → ALB inspects path → routes to Orders microservice.


---

🔹 2. Network Load Balancer (NLB) → Layer 4

Works with transport protocols:

TCP

UDP

TLS (pass-through, no inspection)


Features: Very high performance (millions of requests per second), preserves source IP, supports static IPs, suitable for low latency use cases.

Does not look at HTTP paths/headers—just forwards based on IP + port.


💡 Example: Gaming app using UDP → NLB forwards traffic without touching payload.


---

🔹 3. Gateway Load Balancer (GWLB) → Layer 3

Works at network layer (Layer 3/4).

Routes all traffic (IP packets) to security appliances (firewalls, IDS/IPS).

Primarily used for inspection and inline security services.


💡 Example: All VPC traffic → GWLB → Third-party firewall → destination.


---

🗂 Quick mapping table:

Protocol	OSI Layer	AWS LB Support

HTTP	L7	ALB
HTTPS	L7	ALB
WebSocket	L7	ALB
TCP	L4	NLB
UDP	L4	NLB
TLS (pass-through)	L4	NLB
All IP traffic	L3/4	GWLB



---

👉 A rule of thumb:

If you need content-based routing (paths, hosts, headers) → ALB.

If you need raw performance / low latency / TCP or UDP → NLB.

If you need traffic inspection / security appliances → GWLB.



---

Do you want me to also explain why WebSocket, even though it looks like TCP, is handled by ALB (L7) and not NLB? That’s a common confusion.

