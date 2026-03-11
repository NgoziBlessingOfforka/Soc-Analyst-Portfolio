# Incident Response Case Study: Fake Microsoft Tech Support Scam
## Overview
This case study documents a suspicious screen that appeared on a laptop claiming that Windows had been locked due to unusual activity. The screen instructed the user to contact a Microsoft technical support phone number. After investigation and response actions, the issue was identified as a browser-based tech support scam designed to trick users into calling a fake support number or entering credentials.

## Incident Screenshot

![Fake Lock Screen](Fake-Lock-Screen.jpg)
Incident Screenshot  Initial Indicators of Suspicious Activity
•	Alert displayed a phone number to call Microsoft support
•	System appeared locked with a login overlay
•	The message created urgency and fear
•	The alert prevented normal browser interaction
Immediate Response Actions
1. Isolate the Device
The first step was to disconnect the laptop from the network to prevent any potential malicious communication.
Actions taken:
- WiFi was disconnected
- Network access was isolated
2. Investigate the Screen Behavior
The screen appeared to behave like a browser overlay rather than a true system lock. Keyboard shortcuts were still working and the system remained responsive.
3. Terminate Suspicious Process
The Windows security shortcut Ctrl + Alt + Delete was used to open Task Manager. The browser process displaying the suspicious screen was ended, which removed the fake alert.
4. Restart the System
After closing the browser process, the system was restarted to clear any temporary processes. When the browser reopened, the previous session was not restored.
5. Clear Browser Data
The shortcut Ctrl + Shift + Delete was used to clear browsing history, cookies, and cached files to ensure the malicious page would not reload.
6. Perform Security Scan
A system check was conducted using Windows Security Defender:
1. Open Windows Security
2. Navigate to Virus & Threat Protection
3. Run Quick Scan
No threats were detected.
MITRE ATT&CK Mapping https://attack.mitre.org/
Technique	Description
T1566	Phishing / Social Engineering
T1204	User Execution
T1059	Browser Script Execution
Lessons Learned
•	Always verify suspicious security alerts
•	Avoid calling phone numbers displayed in pop-up warnings
•	Isolate affected systems quickly
•	Terminate suspicious processes using Task Manager
•	Perform post-incident security checks
Key Security Takeaways
•	Not all alarming security messages are legitimate
•	Immediate isolation reduces risk exposure
•	Understanding system behavior helps determine whether the threat is real
•	Basic incident response steps can resolve many browser-based attacks
Skills Demonstrated
•	Security awareness
•	Incident response fundamentals
•	Threat identification
•	System isolation
•	Endpoint investigation
