# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Challenge Tasks

### Task 1: DNS – How Names Become IPs

1. Explain in 3–4 lines: what happens when you type `google.com` in a browser?
Ans. When you enter google.com, the browser asks the OS to resolve the domain name into an IP address via DNS.

A DNS resolver queries DNS servers to find the correct IP.

Once the IP is returned, the browser establishes a TCP/TLS connection to that server.

Then it sends an HTTP(S) request and loads the webpage.

2. What are these record types? Write one line each:
Ans.
- A → Maps a domain name to an IPv4 address

- AAAA → Maps a domain name to an IPv6 address

- CNAME → Alias that points one domain to another domain

- MX → Specifies mail servers responsible for receiving emails

- NS → Indicates authoritative name servers for the domain

3. Run: `dig google.com` — identify the A record and TTL from the output
Ans. Screenshot of the output :

<img width="809" height="456" alt="image" src="https://github.com/user-attachments/assets/a0cd02a5-b984-4138-8027-024281024ee6" />

Here, 
- A Record -> 142.250.205.14
- TTL      -> 142

---

### Task 2: IP Addressing
1. What is an IPv4 address? How is it structured? (e.g., `192.168.1.10`)
Ans. An IPv4 address is a 32-bit numerical identifier assigned to devices on an IP network.

It is written in dotted-decimal format as four octets separated by dots (e.g., 192.168.1.10).

Each octet ranges from 0 to 255 (8 bits each).

Example structure:
192 .168 .1 .10

2. Difference between **public** and **private** IPs — give one example of each
Ans. Public IP → Globally unique, routable on the internet, assigned by ISP
✅ Example: 8.8.8.8

Private IP → Used inside local networks, not directly routable on the internet
✅ Example: 192.168.1.10

3. What are the private IP ranges?
Ans.
- 10.0.0.0 to 10.255.255.255 → (10/8)

- 172.16.0.0 to 172.31.255.255 → (172.16/12)

- 192.168.0.0 to 192.168.255.255 → (192.168/16)

4. Run: `ip addr show` — identify which of your IPs are private.
Ans.
<img width="694" height="275" alt="image" src="https://github.com/user-attachments/assets/d1c57265-3a44-4c0d-bbe4-ac2fe1158842" />

---

### Task 3: CIDR & Subnetting
1. What does `/24` mean in `192.168.1.0/24`?
Ans. /24 is the CIDR prefix length, meaning 24 bits are used for the network portion of the address.

Since IPv4 has 32 bits total → 32 − 24 = 8 bits for hosts.

Equivalent subnet mask: 255.255.255.0

2. How many usable hosts in a `/24`? A `/16`? A `/28`?
Ans. Formula: Hosts = 2^(host bits) − 2
(we subtract network address + broadcast address)

- /24 → host bits = 8 → 2^8 − 2 = 256 − 2 = 254

- /16 → host bits = 16 → 2^16 − 2 = 65,536 − 2 = 65,534

- /28 → host bits = 4 → 2^4 − 2 = 16 − 2 = 14

3. Explain in your own words: why do we subnet?
Ans. We subnet to divide a large network into smaller, manageable networks.

This helps improve performance, security, IP utilization, and broadcast control.

It also allows logical segmentation (e.g., departments, environments).

5. Quick exercise — fill in:
```
| CIDR |   Subnet Mask   | Total IPs | Usable Hosts |
|------|-----------------|-----------|--------------|
| /24  | 255.255.255.0   | 256       | 254          |
| /16  | 255.255.0.0     | 65,536    | 65,536       |
| /28  | 255.255.255.240 | 16        | 14           |
```

---

### Task 4: Ports – The Doors to Services
1. What is a port? Why do we need them?
Ans. A port is a logical communication endpoint used by TCP/UDP to identify a specific service or application on a device.

While an IP address identifies the machine, a port identifies the process/service running on it.

We need ports for :
1️⃣ Multiple services on one IP
A single server can run many services: web, SSH, database. Ports keep them separate.

2️⃣ Traffic direction
Ports tell the OS which application should receive the data.

3️⃣ Standardization
Well-known ports map to common services.

2. Document these common ports:
```
| Port | Service |
|------|---------|
| 22   | SSH     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 53   | DNS     |
| 3306 | MySQL   |
| 6379 | Redis   |
| 27017| MongoDB |
```

3. Run `ss -tulpn` — match at least 2 listening ports to their services
Ans.
<img width="876" height="179" alt="image" src="https://github.com/user-attachments/assets/1418f8e6-817b-41bb-b89b-70460d68469d" />

---

### Task 5: Putting It Together
1. You run `curl http://myapp.com:8080` — what networking concepts from today are involved?
Ans. Several networking pieces work together:

- DNS resolution → myapp.com → IP address (via port 53)
- IP addressing → Connecting to the resolved server IP
- Port 8080 → Specifies the target application/servic
- TCP connection → Handshake (SYN/SYN-ACK/ACK)
- HTTP protocol → curl sends an HTTP request
- Routing / NAT / Firewall → Determines if packets can reach destination

2. Your app can't reach a database at `10.0.1.50:3306` — what would you check first?
Ans.
i) ping 10.0.1.50

ii) nc -zv 10.0.1.50 3306

iii) 
```
ss -tulpn | grep 3306
systemctl status mysql
```
iv) 
```
bind-address = 127.0.0.1  ❌ blocks remote access
bind-address = 0.0.0.0    ✅ allows remote
```

---
