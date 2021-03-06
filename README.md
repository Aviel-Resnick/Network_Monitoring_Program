# Network_Monitoring_Program
My 2015-2016 PJAS Project

##Definitions:
* A network (WI-FI) automatically indexes connected users based on there connection order. For example the IP of the router (first index) is 192.168.1.1, the next person who connects will have 192.168.1.2, etc. 
* MAC address never change, and can be used to identify devices. 
* A substring is a part of a string. For example, "the best of" is a substring of "It was the best of times". 
* An Address Resoulution Protocol scan takes an IP Address as input, and returns an ARP Table including things like IP, MAC, and connection type.

In order to detect unregistered network intrusions, you need raw network data. At first I used a network mapper, but the sc  an took too long, and I switched to ARP.
The first step is a Batchfile, which scans the first 20 indexes (with ARP) and returns an output similar to the one below -

<br />

#####Interface: 192.168.1.3 --- 0x8 

Internet Address | Physical Address | Type
---------------- | -----------------|----- 
192.168.1.1 | 00-7f-28-45-33-8e | dynamic   

No ARP Entries Found.
No ARP Entries Found.
No ARP Entries Found.

Interface: 192.168.1.3 --- 0x8
  Internet Address      Physical Address      Type
  192.168.1.5           00-24-d7-9d-aa-8c     dynamic   

Interface: 192.168.1.3 --- 0x8
  Internet Address      Physical Address      Type
  192.168.1.6           cc-07-ab-cd-47-e9     dynamic   
No ARP Entries Found.

Next a C# Program uses substrings to detect the lines with MAC Addresses, and pull out the MACS.
It produces an output like the one below -

00-7f-28-45-33-8e
00-24-d7-9d-aa-8c
cc-07-ab-cd-47-e9

The same C# program the cross refrences the MAC address of each connected device every 2 seconds with a user created list of 
"regestered users", and in a scenerio where someone is connecting in any way to the router, my system detects it, and alerts the 
user in 2 seconds.

I also created a user interface in Visual Studio, and intergrated my system into it. The software is basic enough so that anyone
could use it, but powerful enough to detect outside intrusions of any kind in up to 2 seconds.
