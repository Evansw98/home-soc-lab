# Day 2: Improving VM Networking and Exploring Sysmon Logs

Today I worked on improving communications between my attacker computer (Kali) and defender computer (Windows). I did this by creating an isolated internal network inside VirtualBox. In the network settings of VirtualBox, I created an internal network named "SOCNET" and assigned it to adapter 2 on both VMs. 



<img src="../Screenshots/Day 2/network_settings.png" width="700">

<img src="../Screenshots/Day 2/socnet_creation.png" width="700">



After creating the network, I powered on both VMs and ran "ip a" and "ipconfig" in Kali and Windows respectively to ensure they could detect SOCNET. 



<img src="../Screenshots/Day 2/ip_confirmation.png" width="900">



It was at this point I learned that VirtualBox internal networks do not provide DHCP services by default. I then assigned static IP addresses manually to each VM. 



<img src="../Screenshots/Day 2/kali_static_ip.png" width="700">

<img src="../Screenshots/Day 2/windows_static_ip.png" width="700">



I then pinged Windows to ensure the two VMS could communicate over my new network. The initial pings failed, and that was because Windows Firewall was automatically blocking responses. So, I shut down the firewall and then successfully pinged the Windows machine over my new internal network. 



<img src="../Screenshots/Day 2/kali_failed_pings.png" width="700">

<img src="../Screenshots/Day 2/turn_off_firewall.png" width="700">

<img src="../Screenshots/Day 2/kali_successful_pings.png" width="700">



Now that the two machines were communicating and the firewall was down, I ran Nmap in Kali to see the difference in the Sysmon logs. Unlike before, Nmap was able to return information on the target computer, and Sysmon immediately detected the connection attempt, clearly showing the relationship between attacker activity and defensive visibility.  


<img src="../Screenshots/Day 2/kali_nmap.png" width="700">

<img src="../Screenshots/Day 2/sysmon_nmap_detected.png" width="700">