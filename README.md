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
