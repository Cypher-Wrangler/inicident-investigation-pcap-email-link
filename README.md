# inicident-investigation-pcap-email-link

This Github repo contains a timeline-based forensic investigation of suspicious activity captured in a PCAP file. A client reported strange behaviour on their endpoint after clicking a suspicous email link on December 15, 2023, shortly after 16:00 . The investigation was conducted entirely from the PCAP, with no access to a SIEM or endpoint telemery.

## Objective
- Identify what occurred after the client clicked the link
- Determine any C2 callbacks, malware downloads, or credential theft
- Document the packet-level timeline and notable traffic patterns.

##Structure
-timeline.md: Chronological breakdown of the packet analysis
-wireshark-analysis: Screenshots, findings, and protocol breakdowns
-pcap/: Sample PCAP
-tools.md : Tools used during the analysis

## Tools used
-Wireshark
-VirusTool
-AbuseIP
-CyberChef
