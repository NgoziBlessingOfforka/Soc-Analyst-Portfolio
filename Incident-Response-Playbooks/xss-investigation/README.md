Cross-Site Scripting (XSS) Investigation
Alert Information
SIEM: IBM QRadar
QRadar Event ID: 55230
Rule Triggered: ET WEB_SERVER Script tag in URI

Encoded Log
<168>suricata[8969]: {"timestamp":"2025-08-05T10:32:33.872706-0400"...}

Decoded Log
Source IP: 77.111.246.48
Destination IP: 38.242.128.144
URL: /search.php?searchdata=<script>alert('HACKED!')</script>

Indicators of Compromise
Source IP: 77.111.246.48
Payload: <script>alert('HACKED!')</script>

Investigation Summary
The alert indicates a possible reflected Cross-Site Scripting probing attempt targeting the web application. No successful exploitation was observed.

Recommendation
Monitor the IP and ensure input validation and WAF protections are enabled.
