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
First, I created a virtual machine in Azure named "VM-W" for Windows 10, and I also set up another virtual machine, "VM-L," running Linux (Ubuntu).
</p>
<br />

<img width="891" alt="downloak wireshark in RD Windows" src="https://github.com/kavismith/network-protocol/assets/143667203/66e84c67-13d8-4a8c-9d53-a5e0c30b36f9">

</p>
<p>
To access VM-W through remote desktop, you should sign in using the username and password that you created in Azure. After successfully signing in, you can proceed to download and install Wireshark on the virtual machine. 
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/34d9657f-6efb-4d07-acff-131769ef4b10)

</p>
<p>

Once Wireshark has been downloaded and installed, you can go to the Azure portal and locate the private IP address of VM-L (Ubuntu), which is 10.0.0.5. In Wireshark, you should search for ICMP traffic. After that, open PowerShell and initiate a ping command to the private IP address of VM-L. You will be able to observe the request and reply traffic between VM-W and VM-L's private IP address in the Wireshark capture.


</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/a2151c45-d45b-40b5-af29-730f8d958562)


</p>
<p>
In PowerShell, initiate a ping to "www.youtube.com" and observe the network traffic between the private IP address of VM-W and the public address of YouTube. You will be able to observe the request and reply signals exchanged between VM-W and YouTube in the network capture.
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/440112fe-9637-4438-943b-c15f050be687)


</p>
<p>
By using the continuous command line "ping 10.0.0.5 -t" and targeting the private IP address of VM-L, you will observe that the replies are continuous, indicating an ongoing and persistent ping connection.
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/e2ee5274-e71c-4923-8df4-2256dc797164)

<img width="900" alt="timed out" src="https://github.com/kavismith/network-protocol/assets/143667203/f3f2306b-a3a0-4e4f-a2b5-bdf4919aedfd">

![image](https://github.com/kavismith/network-protocol/assets/143667203/b3e5d3f2-26cf-4eb6-b3d1-77a4a38411d8)

<p>
 Now, navigate to the Azure portal and proceed to deny traffic for VM-L by searching for the network security group and selecting VM-L. Then, select the Inbound security rules and create a new rule. Adjust the protocol to ICMP, change the action to Deny, and set the priority to 200 to ensure it takes precedence over other rules. After adding this rule, you will observe that the continuous replies will time out.

Subsequently, return to VM-L's Inbound rules and edit the rule to allow traffic. Following this adjustment, you will notice that the traffic resumes, and the replies start again. 
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/873f553d-d06c-4d53-ae49-328b908334c7)

![image](https://github.com/kavismith/network-protocol/assets/143667203/03296368-6bd6-4bb7-8e50-50d5fb6eb6bd)

![image](https://github.com/kavismith/network-protocol/assets/143667203/daf75109-9acb-4942-bd9a-e4b014d07e39)

</p>
<p>
Search for SSH protocol in Wireshark, and then, in PowerShell, enter the command "SSH labuser@10.0.0.5." You will receive a message indicating that the host connection could not be established. To proceed, type "yes" to confirm the connection, and then input your password to connect to the Linux server. To disconnect from the Linux server, you can type "exit."
</p>
<br />

![image](https://github.com/kavismith/network-protocol/assets/143667203/440112fe-9637-4438-943b-c15f050be687)


</p>
<p>
  Search for DHCP traffic in Wireshark. In powershell key in command ipconfig /renew to get VM-L a new IP address. You will see in wireshark that 
</p>
<br />
