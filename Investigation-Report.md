#Findings
- Time: 2023-12-15 16:01:57 UTC
- Host: 10.12.15.101
- IOC Domains: jinjadiocese.com, keebling.com, baumbachers.com, ionister.com
- IOC IPs: 68.66.226, 66.42.96.18, 45.77.85.150, 207.246.75.243
- Possible Malware Family: Pikabot
- Zip Filename:GURVU.zip
- Zip File SHA256:F24888DA47BAE0149AB5C0D887D32FC155CB42AC8138D22699AE12CE1DCA6BD1
  
#Investigation

On 2023-12-15 16:01:57 UTC, the host 10.12.15.101 was seen accessing the domain jinjadiocese.com, which led to the download of an archived file at 16:02:02 named GURVU.zip. The contents within this file were likely executed as suspicous DNS queries were requested at 16:10:12, approximetly 8 minutes after downloading the file. Based on the investigation, these DNS requests have been reported in the wild as malicious and related to Pikabot. Pikabot is a downloader/installer, meaning its purpose is to install additional malware on the host.
With the evidence of these DNS requests, I believe with high confidence that the host 10.12.15.101is infected with Pikabot malware. Based on the PCAP provided , we cannot say with confidende is the activity is still ongoing.  

WHO: Host: 10.12.15.101

WHAT: Downloaded ZIP file: GURVU.zip

WHEN: Started 2023-12-15 16:01:57 - Based the PCAP, we cannot determine if the activity still ongoing

WHERE:Computer with IP Address 10.12.15.101

WHY: The intent is not provided

HOW: As result of the user on the host machine clicking on email link resulting on the download of GURVU.zip. This could have either been knowingly or unknowingly.The contents were likely executed based on the DNS request.

#Recommendations

1. Immediately isolate this host and consider a forensic investigation to determine the impact of the incident. Otherwise reimage to ensure complete removal of artifacts left behind.

2. Execute a query to search for the IOCs to check if any additional host in the network has them. If you find any host with this IOCs isolate them immediately.
3. Although the IPs and domains are easily changed by attackers, consider placing them in a blocklist to prevent future compromise.
