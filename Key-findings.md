
## Perform OSINT on IP and Domains
IP Address:68.66.226.89
 - AbuseIPDB: Reported 16 times as of investigation
   <img width="950" height="1169" alt="Screenshot 2025-08-11 091124" src="https://github.com/user-attachments/assets/cf3c3464-e3f3-4d66-b4c9-07a44723f615" />

Domain:jinjadiocese.com
 -DomainTools Whois: created 2025-01-19 | updated 2025-01-19
 <img width="691" height="712" alt="Screenshot 2025-08-11 092748" src="https://github.com/user-attachments/assets/7311f6f5-d935-4692-9a0a-c743abd0fbb6" />
 -VirusTotal: 3 security vendors flagged this domain as malicious, phishing and suspicious.
<img width="1061" height="807" alt="Screenshot 2025-08-11 093346" src="https://github.com/user-attachments/assets/5b193091-f96a-41b4-89f9-455524c90ee5" />
AlienVault OTX: Analyze this domain is related to Pikabot
<img width="1073" height="1166" alt="Screenshot 2025-08-11 094047" src="https://github.com/user-attachments/assets/0400a060-ec39-43dd-8bbb-4c1b3f459de6" />
A quick investigation of Pikabot, MITRE ATT&CK list Pikabot as a backdoor used for initial access and tool deployment
<img width="1059" height="636" alt="Screenshot 2025-08-11 094537" src="https://github.com/user-attachments/assets/f0e0cc99-1ef9-446c-a4b6-d42b4a651018" />

Based on quick OSINT, this activity does not look legitimate and requires further investigation.

## Perform further investigation
On wireshark we can see another GET request for another odd URI in packet 17. 
<img width="1404" height="40" alt="Screenshot 2025-08-11 100504" src="https://github.com/user-attachments/assets/36b7f3b9-d6d7-4132-9f1c-6c89ee84e984" />

Following the HTTP stream:
 - Theres an interesting filename: GURVU.zip being downloaded from the server as result of this GET request. This file has a content type of application/octet-stream which is generu=ic binary data according to IANA media types.
<img width="1098" height="676" alt="Screenshot 2025-08-11 100849" src="https://github.com/user-attachments/assets/7cb423fb-1ad6-4259-af2e-1b361145bc91" /0
The media header "PK.." indicate this is a zip file.

On packet 117 we see DNS queries being requested and response all the way to packet 13o
<img width="1563" height="227" alt="Screenshot 2025-08-11 101626" src="https://github.com/user-attachments/assets/27d83a15-5e7d-4f3b-b053-d5e629fab87d" />
Responsees lsited under the info column indicate that there were no records found for the .dat requests. This could possibly be that this .dat requests are instructions for the malware to communicate with other domains, this is just a theory😊.

## Perform OSINT on the additional domains that were requested and successfully responded
 Domain: Keebling[.]com
  -VirusTotal: 15 security vendors flagged this domain as malicous. Google result and comments mentioned pikabot
  -AlienVault OTX: created 2023-12-12
Domain: Baumbachers[.]com
  -VirusTotal: 13 security vendors flag this domain malicious.Google result and comments mentioned pikabot
  AlienVault OTX:created 2023-12-12. Related tag showed pikabot
Domain: Ionister[.]com
  -VirusTotal: 13 security vendors flag this domain malicious.Google result and comments mentioned pikabot
  -AlienVault OTX:created 2023-12-12. Related tag showed pikabot

With OSINT, we know this domains are malicious are likely related to Pikabot. 

Further undestanding Pikabot - downloads additional malware.
<img width="952" height="355" alt="Screenshot 2025-08-11 123812" src="https://github.com/user-attachments/assets/b0932297-3014-4d42-9518-4e9da7a6e360" />

Extract the zip file in an isolated VM.
<img width="872" height="911" alt="image" src="https://github.com/user-attachments/assets/0451b133-eab9-4589-aa84-b89dc0dc8fef" />
Then generate its SHA256 hash:
<img width="629" height="68" alt="Screenshot 2025-08-11 124251" src="https://github.com/user-attachments/assets/2e73a5a8-474b-487f-af23-6101027aecb8" />

Searching the hash on VirusTotal, 28 security vendors flagged this file as malicious. Category its trojan with family label pikabot. File type is zip and contain Javascript.
<img width="1070" height="1119" alt="Screenshot 2025-08-11 124847" src="https://github.com/user-attachments/assets/83123b54-393e-4bac-9cce-042aa364472b" />

Looking at the comment section, filename is GURVU.zip as we had seen earlier on
<img width="975" height="755" alt="Screenshot 2025-08-11 125026" src="https://github.com/user-attachments/assets/fbcf974d-70d4-41c1-920d-289435afa309" />



