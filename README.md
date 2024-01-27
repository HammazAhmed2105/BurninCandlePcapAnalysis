<h2>2022-03-21 - TRAFFIC ANALYSIS EXERCISE – BURNINCANDLE</h2>
<h2>Lab Summary</h2>
Summary: On March 21, 2022, at 20:58 UTC, a Windows host (DESKTOP-5QS3D5D, IP: 10.0.19.14) belonging to Patrick Zimmerman was infected with IcedID malware, leading to Cobalt Strike exploitation. The infection was traced using Kerberos traffic analysis, revealing details such as the host name, IP, and Windows username. Indicators of compromise include connections to malicious domains like oceriesfornot.top and antnosience.com, with associated IP addresses flagged for malware activity. Further investigation exposed the use of a cookie (_u) in the network stream, revealing the victim's username and password. Additional flagged domains and IP addresses associated with Iced bot and Cobalt Strike were identified.
<img src="https://i.imgur.com/qmP8ZMr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Summary</h2>
On Monday 2022-03-21 at approximately 20:58 UTC, a Windows host used by Patrick Zimmerman was infected with IcedID (Bokbot) malware that led to Cobalt Strike
<h2>Task</h2>
Write an incident report. (With Explanation)
<h2>Details</h2>
1.	Host Name – DESKTOP-5QS3D5D
2.	Host IP and Mac Address – 10.0.19.14 & 00:60:52:b7:33:0f
3.	Windows User name - patrick.zimmerman
4.	Time of infection – Monday 2022-03-21
<h2>Explanation</h2>
– Few steps that I like to follow in order to get the above details easily in by filtering Kerberos Traffic. Usually the host name and windows user are both present here. For this case, I used the below packets which says 303 AS-REQ Follow the stream for both and we get the information.
<img src="https://i.imgur.com/o9dyOq5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/l0q46eW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Once the packet is selected wireshark shows the Source IP and MAC in clear text. 
<img src="https://i.imgur.com/XZVbCTu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Indicator of Compromise</h2>
1.	188.166.154.118 – Victim machine made contact with oceriesfornot.top. Search for this host on virus total. It has been flagged as command and control malware by 14 vendors. There's a gzip file present as well.
<img src="https://i.imgur.com/mzqlHzH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Back to research , I found out that IcedID uses this technique as the first stage loading mechanism. The Binary Defense Threat Hunting team has a nice technical blog on the IcedID GZIPLOADER . I’d suggest having a look at it.
<img src="https://i.imgur.com/ob3SzqR.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
Upon more research I found out that the cookie present in the above stream means something. _u cookie value holds victims username and password hexlified. So go to cyberchef, and convert it to ascii. You will get DESKTOP 5QS3D5D:patrick.zimmerman:CD2F3B9F67E3C343
2.	157.245.142.66 – Host is antnosience.com. TCP Stream. Use above method.
<img src="https://i.imgur.com/dpsFjkE.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
3.	23.227.198.203 (bupdater.com) – This ip is beaconing with bupdater.com on port 757. And if we use it on virus total it is flagged as a malware. 
<img src="https://i.imgur.com/7G1NuTR.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Lr95sNf.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
Domains and IP Address for Iced bot
oceriesfornot[.]top	http://188.166.154.118/
antnosience[.]com	157.245.142.66
suncoastpinball[.]com	160.153.32.99
otectagain[.]top	157.245.142.66
seaskysafe[.]com		91.193.16.181
dilimoretast[.]com	160.153.32.99
