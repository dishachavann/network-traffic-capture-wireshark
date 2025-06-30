# Task 5: Capture and Analyze Network Traffic with Wireshark

## Objective
Capture live network traffic using Wireshark and identify at least **three different protocols** present in the captured data.

## Tools Used

- **Kali Linux**
- **Wireshark**
- **Firefox Browser**
- **Terminal commands** (e.g., `ping`)
- **Test websites**:
  - [http://neverssl.com](http://neverssl.com) – to trigger **HTTP**
  - [https://google.com](https://google.com) – to trigger **DNS**, **TLS**, **ICMP**

## Steps Performed

1. **Launched Wireshark** and selected the active interface: `eth0`
2. **Started packet capture**
3. Simulated diverse traffic types:
   - Executed `ping google.com` (to generate **ICMP** packets)
   - Accessed `http://neverssl.com` (to capture **HTTP** traffic)
   - Accessed `https://google.com` (to generate **DNS** requests and observe TLS handshakes)
4. Applied protocol filters in Wireshark:
   - `icmp`
   - `http`
   - `dns`
   - `tcp`
5. **Saved the captured packets** as `fixed.pcap`

## Protocols Captured and Identified

### 1.ICMP (Internet Control Message Protocol)
- **Function**: Used for diagnostics (e.g., `ping`)
- **Example Captured**: Echo requests and replies with `142.250.183.110`

### 2.HTTP (HyperText Transfer Protocol)
- **Function**: Unencrypted web communication over port 80
- **Example Captured**: `GET` request and `200 OK` response from `http://neverssl.com`

### 3.DNS (Domain Name System)
- **Function**: Translates domain names into IP addresses
- **Example Captured**: Query to `8.8.8.8` resolving `google.com`

### 4.TCP (Transmission Control Protocol)
- **Function**: Ensures reliable, ordered data transfer
- **Example Captured**: TCP three-way handshakes and data packets during HTTP/DNS sessions

## Files Included

- `fixed.pcap` – Wireshark capture file containing all traffic


## Interview Questions & Answers

### 1. What is the difference between TCP and UDP?
- **TCP (Transmission Control Protocol)** is a connection-oriented protocol that ensures reliable delivery of data through acknowledgments and retransmissions.
- **UDP (User Datagram Protocol)** is a connectionless protocol that sends data without guaranteeing delivery, order, or integrity. It is faster and used where speed is more critical than reliability (e.g., streaming, VoIP).

### 2. How does DNS resolution work in a typical web request?
- When a user enters a domain name (like `google.com`), the DNS resolver queries a **DNS server** (like `8.8.8.8`) to find the corresponding IP address.
- The response contains the IP address needed for the browser to connect to the web server.
- This resolution process can involve querying root, TLD, and authoritative DNS servers if the answer is not cached.

### 3. What is the role of ICMP in networking diagnostics?
- **ICMP** is used by network devices to send error messages and operational information.
- Commonly used in tools like `ping` and `traceroute` to test connectivity and measure round-trip times.
- It helps in identifying unreachable hosts, packet loss, and routing issues.

### 4. What is a packet, and what tools can inspect it?
- A **packet** is a small unit of data transmitted over a network.
- It includes headers (like source/destination IPs) and payload (the actual data).
- **Tools to inspect packets**: Wireshark, tcpdump, Tshark, Netcat, Nmap.

### 5. Why is `http://neverssl.com` particularly useful for HTTP traffic analysis?
- `neverssl.com` forces traffic over plain HTTP instead of HTTPS.
- This makes it ideal for observing unencrypted **HTTP requests and responses** in Wireshark, which are otherwise hidden when using secure sites.

  > ⚠️ Note: The `fixed.pcap` file is large and can't be previewed on GitHub. Please download and open it using Wireshark to view the contents.

