| Layer | Name         | Purpose                     | Example                      |
| ----- | ------------ | --------------------------- | ---------------------------- |
| L7    | Application  | User-facing services        | HTTP, FTP, SMTP              |
| L6    | Presentation | Data formatting, encryption | SSL/TLS, JPEG                |
| L5    | Session      | Session management          | NetBIOS, RPC                 |
| L4    | Transport    | End-to-end communication    | TCP, UDP                     |
| L3    | Network      | Routing between networks    | IP, ICMP                     |
| L2    | Data Link    | MAC addressing, switching   | Ethernet, ARP                |
| L1    | Physical     | Transmitting bits           | Cables, Fiber, Wi-Fi signals |

| TCP/IP Layer          | Purpose                        | Protocols             |
| --------------------- | ------------------------------ | --------------------- |
| Application           | User services                  | HTTP, HTTPS, DNS, SSH |
| Transport             | End-to-end delivery            | TCP, UDP              |
| Internet              | Routing                        | IP, ICMP              |
| Link (Network Access) | Physical network communication | Ethernet, Wi-Fi       |

| OSI Layer         | TCP/IP Layer |
| ----------------- | ------------ |
| Application (L7)  | Application  |
| Presentation (L6) | Application  |
| Session (L5)      | Application  |
| Transport (L4)    | Transport    |
| Network (L3)      | Internet     |
| Data Link (L2)    | Link         |
| Physical (L1)     | Link         |

## When you visit https://google.com:
DNS resolves google.com → IP address.
TCP establishes a connection (3-way handshake).
TLS (part of HTTPS) encrypts communication.
HTTP/HTTPS sends the web request.
IP routes packets across networks.
Ethernet/Wi-Fi carries frames over the local network.

```
Q: Does HTTP run on IP directly?
Answer: No.
HTTP
 ↓
TCP
 ↓
IP
 ↓
Ethernet/Wi-Fi
```
## Real Example: `curl https://example.com`
```
curl https://example.com
```

The request travels through multiple layers:
```
Application Layer  → HTTPS (HTTP + TLS)
        ↓
Transport Layer    → TCP
        ↓
Internet Layer     → IP
        ↓
Link Layer         → Ethernet / Wi-Fi
```

### Step-by-Step

**1. DNS Lookup (Application Layer)**
* `example.com` is resolved to an IP address.
* DNS query is sent (usually using UDP port 53).

```
example.com → 93.184.216.34
```

**2. TCP Connection (Transport Layer)**
* Your machine establishes a TCP connection to the server on port 443.
```
Client → SYN
Server → SYN-ACK
Client → ACK
```

**3. TLS Handshake (Application Layer)**
* HTTPS requires encryption.
* Client and server exchange certificates and negotiate encryption keys.

**4. HTTP Request (Application Layer)**
```
GET / HTTP/1.1
Host: example.com
```

**5. Encapsulation**
The HTTP request is wrapped at each layer:

```
HTTP Request
    ↓
TCP Segment
    ↓
IP Packet
    ↓
Ethernet Frame
    ↓
Network
```

**6. Server Response**
* Server sends back an HTTP response.
* The layers are unpacked in reverse order on your machine.
---
```
netstat - an	View active connections
```

nc -zv localhost 22
| Part        | Meaning                                                 |
| ----------- | ------------------------------------------------------- |
| `nc`        | Run Netcat                                              |
| `-z`        | Scan mode (don't send data, just check if port is open) |
| `-v`        | Verbose output                                          |
| `localhost` | Target machine (your own computer)                      |
| `22`        | Port number (SSH)                                       |


- ss -tulpn shows which ports are listening on the system.
- nc -zv actively attempts a connection to verify that the port is reachable.

You can add this to your markdown report:

### Reflection

#### 1. Which command gives you the fastest signal when something is broken?
**`ping`** gives the fastest basic connectivity check because it immediately tells me whether the target is reachable and provides latency and packet loss information.
For web applications specifically, **`curl -I <url>`** is often the fastest way to verify whether the service itself is responding.

---

#### 2. What layer would you inspect next if DNS fails?
DNS operates at the **Application Layer (OSI Layer 7)** and the **Application Layer of the TCP/IP model**.
If DNS resolution fails, I would check:
* DNS server configuration (`/etc/resolv.conf`)
* DNS reachability (`ping` or `nc` to DNS server)
* Firewall rules
* Network connectivity at the Internet/Network layer

---

#### 3. What layer would you inspect if HTTP 500 appears?
An **HTTP 500 Internal Server Error** usually indicates a problem at the **Application Layer (OSI Layer 7)**

* Web server logs (Nginx/Apache)
* Application logs
* Backend service health
* Database connectivity
* Recent deployments or configuration changes

---

#### 4. Two follow-up checks in a real incident
**Check 1: Service Status**
```
systemctl status <service>
```

Purpose:
* Verify whether the application or service is running properly.

**Check 2: Logs**
```
journalctl -u <service> -n 50
```

```
tail -f /var/log/nginx/error.log
```

Purpose:
* Identify errors, crashes, connection failures, or configuration issues.

---
### Key Takeaway

When troubleshooting, I start from the bottom and move upward:

```
Physical/Link
    ↓
Network (IP)
    ↓
Transport (TCP/UDP)
    ↓
Application (DNS, HTTP, SSH)
```

- Curl - Used to send HTTP/HTTPS requests and interact with APIs.
- wget - to download
- traceroute/ tracepath - Shows the path packets take from your machine to a destination.

```
DNS Issue?
    ↓
dig google.com

Network Issue?
    ↓
ping google.com

Path Issue?
    ↓
traceroute google.com

Port Issue?
    ↓
nc -zv host port

Web/App Issue?
    ↓
curl -I https://site.com

Need File?
    ↓
wget URL
```
