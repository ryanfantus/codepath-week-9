# codepath-week-9
These are my honeypot findings for the Codepath Cybersecurity Course - week 9

I deployed an MHN honeypot admin vm and the following actual honeypots, C2'd by the admin VM, for approximately four days:

 1. cowrie
 2. snort
 3. dionaea

I initially tried installing all of these honeypots under Ubuntu 14.04 but realized the cowrie VM wasn't returning anything. Further inspection revealed that there are currently some deployment errors on Ubuntu 14.04 so I killed the VM and tried again on a 16.04 stack, which resulted in success.

The honeypot results for *total attempted attacks* are as follows:

 1. cowrie - 3822
 2. snort - 4346
 3. dionaea - 43483

Most attacks were from TOR exit nodes. Interestingly, the rest of the top attacking IPs all appeared to originate in France or Canada. It's possible that these are VPN exit node locations.

The top attacked port was 22, ssh, intercepted by cowrie, though the most often attacked honeypot was dionaea. This is likely due to a wider attack surface.

The top five attack signatures were
1.  **ET COMPROMISED Known Compromised or Hostile Host Traffic TCP group 39 (281 times)**
2.  **ET DROP Dshield Block Listed Source group 1 (269 times)**
3.  **ET SCAN Potential SSH Scan (157 times)**
4.  **ET COMPROMISED Known Compromised or Hostile Host Traffic TCP group 30 (96 times)**
5.  **ET SCAN Suspicious inbound to MSSQL port 1433 (74 times)**

Cowrie attacks predominantly expected to login with some sort of "admin" credential, which is common with IOT devices.

The raw exported data can be found attached [here](session.json) as well.
