PHISHING EMAIL ANALYSIS template
 **A phishing email analysis should include following information, supported by screenshots or
 relevant information needed to analyze.**
 Sender Information: b2b.erinbassettartistry.com
 Check for any anomalies or misspellings in the sender's name or domain.-Domain - No direct misspelling anomaly detected
 Check the domain. qarvdfbaonh@f2e4im377im.us
 Receiver Information: me@aol.com
 Are you the only recipient? Is there anything unusual?
 Subject Line: We've been trying to reache you please respond #2046608512
 Analyze the subject line for urgency or emotional triggers.
 Header Information:
 Authentication results. SPF, DKIM, DMARC - The domain b2b.erinbassettartistry.com lacks a DMARC record and shows no visible SPF or DKIM validation.
 Check the sender IP address.  The IP address associated with the analysis was checked using AbuseIPDB, WhatIsMyIP, and VirusTotal.
•  All tools indicate that the IP address is clean, with no reported malicious activity.
•  The IP address geolocates to the United States and does not show indicators of proxy, VPN, or suspicious hosting.

 Check if there is a reply-to address? qarvdfbaonh@f2e4im377im.us
 Check header for some other anomalies. This email failed all major authentication checks (SPF, DKIM, and DMARC). The sending infrastructure does not match the claimed domain, and the lack of DMARC enforcement allowed the message to be delivered despite authentication failures. Combined with an urgent subject line (“Final 24-Hour Notice”), these findings strongly suggest a phishing attempt.
 
 Content and Body: http://cansornatia[.]com/LEAVE=To
 Analyze the email content for grammar and spelling errors. The body of the email was analyzed to identify embedded links.

BrowserLink (browserlink.com) and a URL extractor tool were used to extract URLs from the email content.
 Check for generic greetings or an absence of personalized information.
 Assess the tone of the message (urgency, fear, excitement) to identify emotional
 manipulation.
 Look for requests for sensitive information or actions.
 Check for inconsistent or poor-quality graphics.
 Verify the legitimacy of company logos and branding elements.
 Links and URLs: (if any)
The extracted URL (hxxp://cansornatia[.]com/LEAVE=To>) was analyzed using VirusTotal, where 2 out of 98 security vendors flagged it as malicious, the majority classified it as clean or spam, and the URL returned an HTTP 404 status, which—when correlated with earlier email authentication failures and suspicious email content—still supports a phishing assessment.
The extracted URL (hxxp://cansornatia[.]com/LEAVE=To%3E) was analyzed using urlscan.io, which showed that the domain resolves to a U.S.-based IP address (205.185.120.105, PONYNET), uses a valid TLS certificate, returned a 404 Not Found page with a redirect from HTTP to HTTPS, and received no malicious classification, indicating no active payload at the time of scanning, though the infrastructure remains suspicious when correlated with the phishing email context.
 
 
Verify if the URL matches the purported destination.
Yes
 Analyze the use of shortened URLs.
N/a
 Attachments:(if any)
 
I ran the extracted URL through ANY.RUN and ThreatZone, and the analysis showed no active malware execution or exploit behavior, with the URL returning a 404 page and generating only normal browser activity, indicating no malicious payload was delivered at the time of analysis
 Be cautious with email attachments, especially from unknown sources. Do not
 download them directly to your computer. If you do it so, do not open.
 Verify the file type and extension.
 Use a VMto download document and use a sandbox to analyze.
 
 
After identifying the URL associated with the email, I analyzed it using VirusTotal, where related artifacts in the graph view revealed multiple malicious files, including Windows 32/64 malware variants, a Trojan downloader, HackTool.MSIL, and Win32.TrojanSpy detections, indicating that the URL is part of a broader malicious infrastructure despite the original link being inactive at the time of analysis.
Analysis of Findings
An investigation of the reported email determined it to be a confirmed phishing attempt with malicious intent, based on multiple converging indicators across header, content, and threat-intelligence analysis: the sender domain failed SPF, DKIM, and DMARC authentication, the Reply-To address did not match the sender domain, and the subject line used urgency to prompt user action; analysis of the embedded URL (hxxp://cansornatia[.]com/LEAVE=To) using VirusTotal, urlscan.io, ANY.RUN, and ThreatZone showed the link was inactive (HTTP 404) and delivered no payload at the time of testing, but VirusTotal graph analysis revealed associated malicious artifacts, including Trojan downloaders, HackTool.MSIL, and Win32.TrojanSpy variants, indicating linkage to a broader malicious infrastructure; although the hosting IP appeared clean and U.S.-based, this does not mitigate risk, as phishing campaigns commonly leverage legitimate infrastructure and rotate payloads to evade detection, leading to the conclusion that the email poses a high phishing risk despite the absence of active malware during dynamic analysis.


Recommendation
1.	Classify the email as phishing and malicious by intent and ensure it is blocked across the email security gateway.
2.	Blacklist and monitor the associated URL and domain (cansornatia[.]com) within network security controls, even though it is currently inactive.
3.	Educate users to avoid clicking links in emails that create urgency or request immediate action, especially when authentication checks fail.
4.	Implement and enforce DMARC (p=reject) for organizational domains to prevent spoofed emails from being delivered.
5.	Continue monitoring threat intelligence feeds for future activity related to the identified malicious infrastructure and associated malware families.
6.	Report the indicators of compromise (IOCs) to internal security teams or threat-sharing platforms to support proactive defense.

