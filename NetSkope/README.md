## Introduction: 

This project is provided (in FortiManger version 7.4) as a general guideline with configured objects needed to integrate with Netskope cloud services. One should consider understanding the requirements of the connectivity in terms of routing, Underlay and Overlay (IPsec) configurations and SDWAN rules for application steering. Three templates provided contain all the needed elements to integrate with said vendor but not limited to, as there may be additional configuration required due to unique circumstances for Firewall policies to allow traffic, Routing and Overlay (IPSec) configurations, along with SDWAN rules that will ultimately, steer HTTP and HTTPs traffic from FortiGate to Netskope services. 

## Requirements:

Since there are many dependencies and variables involved in order to configure SDWAN correctly, therefor, provided CLI templates are only functional when precise information is provided for the following:

This function requires: 

•	FortiManager 7.4 or higher
•	FortiOS 7.0 or higher
•	Firewall Policy Configuration: Provide relevant information
o	From and to Interfaces, internal LAN to SDWAN Zones (Overlay)
o	Source and Destination IP addresses or blocks
o	Services allow or block per requirement
•	Static Route(s): 
o	Set device IP or FQDN and priority 
•	IPsec Template: provided IPsec CLI is for reference only as specific configuration will be required for IPsec tunnels. 
o	Remote Device: IP address or Dynamic DNS
o	Remote Gateway IP and subnet
o	Phase 1 and 2 proposals for SA
o	Pre-shared Key
o	Tunnel interface IP
o	Phase 2 configuration
•	SDWAN Template: Basic information is provided with generic data prefilled for SDWAN template to get started. However, user must configure and refine further with the following: 
o	SDWAN Zones and member interfaces for underlay and overlay 
o	Performance SLAs with preferred values
o	SDWAN rules to steer web traffic to Netskope gateway 
