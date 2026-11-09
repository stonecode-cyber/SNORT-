 This is my hands-on lab project using snort rule in iIntrusion detection system and the Intrusion Prevention system

SNORT is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS). 

**### Intrusion Detection system IDS :**
Passive traffic monitoring that only sent alert when suspiscious traffic is detected  we have two types which are :

- Network-Based IDS- monitors the traffic flow from various areas of the network. The aim is to investigate the traffic on the entire subnet. If a signature is identified, an alert is created.
- Host-Based IDS; monitors the traffic flow from a single endpoint device. Its aim is to investigate the traffic on that device. If a signature is identified, an alert is created.

**### INTRUSION PREVENTION SYSTEM** 
IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for stopping/preventing/terminating the suspicious event as soon as it is detected.
There are 4 amjor type IPS:

- Host-based IPS :PS actively protects the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device. If a signature is identified, the connection is terminated.
- Network-Based IPS: NIPS monitors the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If a signature is identified, the connection is terminated.
- Behavioural Based IPS:Behaviour-based systems monitor the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If an anomaly is identified, the connection is terminated.(Network behavior analysis)
- Wireless IPS:monitors the traffic flow from a wireless network. Its aim is to protect wireless traffic and stop possible attacks launched from there. If a signature is identified, the connection is terminated.

In this project i start by cehcking if snort is install on my system using the command **_snort -V_** i also check if the configuration is correct by using the commnd  **_sudo snort -c /etc/snort/snort.conf -T_** 

I proceed to explore snort by checking the Build number of my snort version using the command  _**sudo snort -c /etc/snort/snort.conf -T**_ 

<img width="476" height="362" alt="Image" src="https://github.com/user-attachments/assets/4cd868e0-7a58-42c6-abcc-3bd19464b501" />

I also check the total number of rules in the current version  which indicated total of 1451 rules 

<img width="487" height="351" alt="Image" src="https://github.com/user-attachments/assets/fcafb58f-0d07-45ce-9293-e9308da76137" />

### **SNORT AS A SNIFFER MODE:**
where
-v= verbose mode
-d = packet loader(payload)mode
-e = Display the link-layer (TCP/IP/UDP/ICMP) headers. 
-X=Display the full packet details in HEX.
-i =s define a specific network interface to listen to or sniff.

**### SNORT AS A LOGGER MODE**
-l= use snort as a logger mode
-K ASCII= log packet in ASCII Mode
-r =Reading option: Review the logged events in Snort.
-n =specify the number of packets to be processed or read

**### SNORT AS A IDS/IPS MODE**
-c =Defining the configuration file.
-T =Testing the configuration file.
-N=Disable logging.
-D=Background mode.
-A= Alert mode( full alert about an event)


I started by lunching snort in a verbose mode, using the commnd **_sudo snort -v_** snort start showing the  packets in verbosity mode as shown below; WHILE to check for configuration status we may use the command _**sudo snort -c /etc/snort/snort.conf -T**_

<img width="425" height="346" alt="Image" src="https://github.com/user-attachments/assets/27ff5dc9-a2c9-43c3-a5f4-e590246a406d" />
Lunching snort is packet dumping mode using command **_sudo snort -d_**

TASK 1: sudo snort -dev -K ASCII -l .

Execute the traffic generator script and choose "TASK-6 Exercise". Wait until the traffic ends, then stop the Snort instance. Now analyse the output summary and answer the question.
sudo ./traffic-generator.sh
Now, you should have the logs in the current directory. Navigate to folder "145.254.160.237". What is the source port used to connect port 53?

In this task, navigate to the directory where an executable fole was located name _traffic-generator.sh_ i execute the file using the _**sudo ./traffic-generator.sh command**_ , and  file _**snort.log.1640048004**_ from which i can read the detail of th captured Packet  by using the command _**sudo snort -r snort.log.1640048004**_.
From there navigated to the packet with IP address 145.254.160.237 at port 53. This reveale the port number to be **3009 a**s shown in the screenshot below

<img width="460" height="354" alt="Image" src="https://github.com/user-attachments/assets/d58cdd71-d8e3-4769-99fb-051942f1811e" />

TASK 2: Read the snort.log file with Snort; what is the IP ID of the 10th packet?
In thsi task i read the pack number 10 of the file using the command **_sudo snort -r snort.log.1640048004 -n10_**  this revel the ID of packet number 10 to be **49313** as shown in the screenshot below:

<img width="456" height="347" alt="Image" src="https://github.com/user-attachments/assets/9c23bd8f-7374-4c78-bfaa-b50ff8480ef2" />

TASK 3: Read the "snort.log.1640048004" file with Snort; what is the referer of the 4th packet?

In this project, i made use of the command that filter 4th packet  and display the result in HEX format as follows: _**sudo snort -Xr snort.log.1640048004 -n4**_

This display the result as _**http://www.ethereal.com/development.html**_ as shown in th screenshot below:

<img width="468" height="364" alt="Image" src="https://github.com/user-attachments/assets/1fce967c-7b0a-4912-ad37-59b18a4e7a19" />

TASK 4: Read the "snort.log.1640048004" file with Snort; what is the Ack number of the 8th packet?

In this project, i made use of the command that filter 4th packet  and display the result in HEX format as follows: _**sudo snort -Xr snort.log.1640048004 -n8**
This reveal the Ack  number to be **_0x38AFFFF3_** as shown in the screenshot below 

<img width="481" height="360" alt="Image" src="https://github.com/user-attachments/assets/1288f85c-0909-4aaa-8c53-a82bf7322298" />

TASK 5: Read the "snort.log.1640048004" file with Snort; what is the number of the "TCP port 80" packets?
In this task i use the command to look for all packet with tcp port 80 as **_sudo snort -r snort.log.1640048004 'tcp port 80 '_**
which reveal the total packet to be 41 as shown in the screenshot below:

<img width="485" height="385" alt="Image" src="https://github.com/user-attachments/assets/16cf4b03-9c46-4b2d-8cb8-21f90ce47e46" />

**Snort as IDS/IPS Mode**
I explore the snort further by disablin logging mode using the command  _**sudo snort -c /etc/snort/snort.conf -N**_
I enable http /ICMP taffic using the command  _**sudo snort -c /etc/snort/snort.conf -D**_

<img width="376" height="82" alt="Image" src="https://github.com/user-attachments/assets/84974faa-014a-4060-a9cd-b7a1c73b737b" /
DS/IPS mode with parameter "-A console"
 I started  the Snort instance in console alert mode (-A console ) with the following command: _**sudo snort -c /etc/snort/snort.conf -A console**_

**### Pcap Investigation with SNORT**
Parameters:
-r /--pcap-single ==Read a single pcap
--pcap-list=""  == read pcap provide withing the apostrophy
--pcap-show == show pca[ name during the process

**TASK: Investigate the mx-1.pcap file with the default configuration file. What is the number of the generated alerts?**

In this task, i made use of the command _**sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap**_  to count the number of alert capture in the scan. This reveal the total number of alert recievd in the scan to be 170 as shown below:
<img width="467" height="359" alt="Image" src="https://github.com/user-attachments/assets/294f86d8-1838-49c4-8806-adc601df1b37" />

**TASK 2: Keep reading the output. How many TCP Segments are Queued?**
In this task, i investigate the section for stream statistics  which display the number of queued segment to be 18 s shown in the screenshot below:
<img width="481" height="223" alt="Image" src="https://github.com/user-attachments/assets/153e6338-6c19-43bf-aa1a-bed7152a9efe" />

**TASK 3:Keep reading the output.How many "HTTP response headers" were extracted?**
<img width="482" height="191" alt="Image" src="https://github.com/user-attachments/assets/2493f1c1-5941-4400-b789-78365e2e7ba8" />

**TASK 4: Investigate the mx-1.pcap file with the second configuration file. What is the number of the generated alerts?**
In this task, i made use of the command **_sudo snort -c /etc/snort/snortv2.conf -A full -l . -r mx-1.pcap_**  whuch reveal the number of alert to be 68 as shown in the screenshot below:

<img width="486" height="220" alt="Image" src="https://github.com/user-attachments/assets/98a4d6e9-c700-4e79-9af3-75c33195a524" />

**TASK 5: Investigate the mx-2.pcap file with the default configuration file. What is the number of the generated alerts?**
In this task we made use of the command sudo **_snort -c /etc/snort/snort.conf -A full -l . -r mx-2.pcap_** 

<img width="452" height="174" alt="Image" src="https://github.com/user-attachments/assets/a343a7ea-426f-4613-8fd6-e373d9f6dcb2" />

This reveal the number of alert to be 340 as shown above

**TASK 6: Keep reading the output. What is the number of the detected TCP packets?**

<img width="485" height="257" alt="Image" src="https://github.com/user-attachments/assets/94ad6436-65d1-43ae-8761-8c9ecdf4b055" />

**TASK 7: Investigate the mx-2.pcap and mx-3.pcap files with the default configuration file. What is the number of the generated alerts?**

<img width="475" height="255" alt="Image" src="https://github.com/user-attachments/assets/58bdf2aa-ae68-4ce4-b231-8e8319c0e492" />

**### SNORT RULES** 
Snort rules follow a specified pattern as stipulated below: 

<img width="410" height="111" alt="Image" src="https://github.com/user-attachments/assets/85f5bd51-00a1-4bff-8c63-6218bf43a29e" />

In this project, i will be considering the 3types of rules which are the :
1: General rules
2:Payload Detection rules
3: Non- Payload detection rules
**### CREATING A SNORT LOCAL RULES**

**TASK 1: Use "task9.pcap". Write a rule to filter IP ID "35369" and run it against the given pcap file. What is the request name of the detected packet? You may use this command: "snort -c local.rules -A full -l . -r task9.pcap"**

This task require creating a snort rules,  i use the command **_sudo nano local.rules_** to open the local rules and edit the rules to alert for any ICMP traffic on the network:

_alert tcp any any <> any any (msg:”ID Test”;id:35369;sid:10000000001; rev:1;)_

<img width="482" height="359" alt="Image" src="https://github.com/user-attachments/assets/85774df1-f51c-4000-8c4e-9c1d5cadd54f" />

After the rule is set i run the command **_sudo snort -c local.rules -A full -l . -r task9.pcap_** to cound and read the packet on the traffic.
I found the name of the request name to be **TIMESTAMP REQUEST**

TASK 2:Clear the previous alert file and comment out the old rules. Create a rule to filter packets with Syn flag and run it against the given pcap file. What is the number of detected packets?
In this task i edited the local.file with sudo nano local.rule  to create a new rules to filter the packet with Syn flag. as shown below:
alert tcp any any <> any any (msg:”FLAG TEST”;flags:S;sid:10000000002; rev:1)
  this create an alert file and i read the file using the **_cat alert_** command 


