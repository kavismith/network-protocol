<h1>Observing Network Traffic</h1>

<h2>Environments Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 
- Ubuntu Server 

<h2>Description</h2>

For this project we will be observing multiple traffic between Windows virtual Machine and and Linux(Umbunctu) virtual machine. I will be using various network protocol in wireshark and different command lines in powershell. 

<h2>Actions and Observations</h2>

<img width="898" alt="windows VM" src="https://github.com/kavismith/network-protocol/assets/143667203/8fdf4396-5d64-45a5-b926-17e12373947c">

<img width="899" alt="linux vm" src="https://github.com/kavismith/network-protocol/assets/143667203/739f7431-d509-42c0-8b99-8f21f43fde72">

</p>
<p>
First, I created a virtual machine in Azure for Windows 10 called VM-W and another virtual machine Linux(Umbunctu) called VM-L
</p>
<br />

<img width="891" alt="downloak wireshark in RD Windows" src="https://github.com/kavismith/network-protocol/assets/143667203/66e84c67-13d8-4a8c-9d53-a5e0c30b36f9">

</p>
<p>
Sign into VM-W remote desktop with username and password created in Azure and then download Wireshark 
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/34d9657f-6efb-4d07-acff-131769ef4b10)

</p>
<p>
After wireshark is downloaded, head over to Azure portal and copy VM-L(unbunctu) private IP address which is 10.0.0.5. search for the ICMP traffic in wireshark. Then open up powershell and ping VM-L private IP address. YOu will see the request and reply traffic between VM-W and VM-L private address. 
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/a2151c45-d45b-40b5-af29-730f8d958562)


</p>
<p>
Ping www.youtube.com in powershell and watch the traffic between VM-W private IP address and Youtube public address. You will notice the request and reply signals between VM-W and Youtube.
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/440112fe-9637-4438-943b-c15f050be687)


</p>
<p>
Use the continuous command line ping 10.0.0.5 -t and ping VM-L private IP address. You will notice that the reply will be continuos.
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/e2ee5274-e71c-4923-8df4-2256dc797164)

<img width="900" alt="timed out" src="https://github.com/kavismith/network-protocol/assets/143667203/f3f2306b-a3a0-4e4f-a2b5-bdf4919aedfd">

![image](https://github.com/kavismith/network-protocol/assets/143667203/b3e5d3f2-26cf-4eb6-b3d1-77a4a38411d8)

<p>
  Now, go to azure portal and deny traffic for VM-L by search for network security group in azure and select VM-L and select Inbound security rules. Create a new rule. Change the protocol to ICMP, change the action to Deny and priority to be 200 so it can be first in line out of the other priorities. Once you add the rule, you will notice that the continuous reply will time out. Then go back to VM-L Inbound rule and edit the rule and allow traffic. You will then see the traffic will start to reply again. 
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/873f553d-d06c-4d53-ae49-328b908334c7)

![image](https://github.com/kavismith/network-protocol/assets/143667203/03296368-6bd6-4bb7-8e50-50d5fb6eb6bd)

![image](https://github.com/kavismith/network-protocol/assets/143667203/daf75109-9acb-4942-bd9a-e4b014d07e39)

</p>
<p>
Search for SSH protocol in wireshard and go to powershell and type in command SSH labuser@10.0.05 and you will see the host connection could not be established. Type yes to continue the connection and then key in your password to connect to Linux server. Type in exit to disconect from the Linux server.
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/440112fe-9637-4438-943b-c15f050be687)


</p>
<p>
  Search for DHCP traffic in Wireshark. In powershell key in command ipconfig /renew to get VM-L a new IP address. You will see in wireshark that 
</p>
<br />
