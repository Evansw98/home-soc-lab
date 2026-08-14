# Day 3: Installing Wazuh On a Dedicated SIEM Server

Today, I installed a dedicated SIEM server using Ubuntu on which to run Wazuh. This involved configuring a static IP address.

<img src="../Screenshots/Day 3/ubuntu_network_config.png" width="700">
<img src="../Screenshots/Day 3/ubuntu_setup.png" width="700">

Unfortunately, the allocated CPU space and RAM were not enough to accomodate the third VM, so steps were taken to manually expand its storage and memory. A clean snapshot of the VM was taken after.

<img src="../Screenshots/Day 3/ubuntu_resize.png" width="700">

Next, the Wazuh stack was installed on the Ubuntu server.

<img src="../Screenshots/Day 3/wazuh_installed.png" width="700">

From the Windows VM, I access the Wazuh dashboard, using the provided admin credentials, and installed the Wazuh Agent on the Windows machine, connecting it to the Ubuntu Wazuh Manager.

<img src="../Screenshots/Day 3/wazuh_agent.png" width="700">

After configuring Wazuh to collect the Sysmon event channel, we simulated process creation events in PowerShell as well as the nmap function from the Kali machine to confirm end-to-end telemetry. 

<img src="../Screenshots/Day 3/wazuh_sysmon-config.png" width="700">

<img src="../Screenshots/Day 3/wazuh_dashboard_alert.png" width="700">

