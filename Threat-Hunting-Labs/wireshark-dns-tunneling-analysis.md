#  Wireshark Network Traffic Analysis – DNS over TCP & TLS Session

**Author:** Ngozi Blessing Offorka  
**Date:** 28 October 2025  
**Category:** Network Traffic / Threat Hunting  
## 🎯 Objective
Analyze a Wireshark capture to identify potential anomalies or malicious behaviors within DNS and encrypted traffic.
## 📊 Summary of Findings
The packet capture revealed both IPv6 TLSv1.2 (HTTPS) traffic and IPv4 DNS communications. While TLS sessions are expected, multiple **DNS queries over TCP (port 53)** were observed, which is **unusual** unless the payload exceeds 512 bytes or the server forces TCP fallback.
| Observation | Evidence | Analyst Interpretation |
|--------------|-----------|------------------------|
| Encrypted TLSv1.2 session with external IPv6 address | Packets 1–3 (to 2a06:98c1:3107::6812:2715) | Normal HTTPS communication |
| Repeated TCP SYNs to port 53 | Packets 4–6 from 192.168.1.79 → 192.168.1.254 | Potential DNS tunneling or resolver misconfiguration |
| SYN-ACK and ACK responses | Packets 6–9 | TCP handshake completed, meaning DNS server accepted TCP |
| No UDP DNS traffic in this capture | Entire capture slice | Worth validating if UDP is blocked or intentionally disabled |
##  Analysis Narrative
The local host (192.168.1.79) repeatedly initiates DNS requests over TCP to its gateway (192.168.1.254). DNS over TCP is rarely used unless:
1. UDP is blocked or filtered.
2. The DNS response exceeds UDP’s 512-byte limit.
3. DNS tunneling is being leveraged to exfiltrate data.
Given these repeated TCP connections within a short interval, this pattern could indicate **DNS tunneling or beaconing behavior.**
##  Recommended Actions
-  Confirm that 192.168.1.254 is a legitimate DNS resolver.
-  Apply Wireshark filters:  
  `dns && tcp.port==53`  
  to isolate DNS traffic.
-  Examine payloads for long or base64-encoded strings.
-  Run IP reputation checks on external IPv6 addresses.
-  Monitor DNS query volume in SIEM for similar behaviors.
##  SOC Takeaway
> DNS over TCP is not inherently malicious, but when seen frequently from a host, it can suggest exfiltration attempts. SOC analysts should always investigate such anomalies further by correlating with endpoint and DNS logs.
##  Tools Used
- Wireshark v4.2  
 
