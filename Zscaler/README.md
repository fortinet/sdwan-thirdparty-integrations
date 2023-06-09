## Introduction: 

This project is provided (in FortiManger version 7.4) as a general guideline with configured objects, needed to integrate with Zscaler cloud security services. One should consider understanding the requirements of the connectivity in terms of routing, Underlay and Overlay (IPsec) configurations and SDWAN rules for application steering. Three templates provided contain all the needed elements to integrate with said vendor but not limited to, as there may be additional configuration required due to unique circumstances for Firewall policies to allow traffic, Routing and Overlay (IPSec) configurations, along with SDWAN rules that will ultimately, steer HTTP and HTTPs traffic from FortiGate to Zscaler services. 

This diagram is referenced form Fortinet documentation below and attached CLI scripts are configured according to the diagram, however, only one FortiGate device configuration is provided in the CLI vs two in the diagram architecture, but the concept is the same. FortiGate Site A has two Underlay links (port1 and port2) each configured with one overlay (Pri Zscaler-SF and Sec Zscaler-DC overlays) per underlay, terminating at Zscaler cloud gateway. 

![Netskope](./Pictures/6.png)

## Requirements:

Three CLI text files are provided, however, “FirewallPolicy_Route_Zscaler” is only for reference, and provided configuration in this file, is a generic CLI script for policy and route configurations. User will need to configure static route(s) or routing for reaching Zscaler GW and Firewall policy will also be specific to deployment needs, with proper, source and destination addresses, outgoing and incoming interfaces, and allowed traffic or services, etc. 

1. FirewallPolicy_Route_Zscaler: (For Reference only, it is a sample config, user must not deploy this script but customize it before deploying per deployment needs, to avoid any connectivity issues or network interruptions)
2. IPsec_Template_Zscaler: (For Deploying IPsec Tunnel)
3. SDWAN_Template_Zscaler: (Deploying SDWAN Rules, SLAs, SDWAN-Interface Configuration)



Since there are many dependencies and variables involved in order to configure SD-WAN correctly, therefore, provided CLI templates are only functional when precise information is provided for the following objects:

This function requires: 

- FortiManager 7.4 or higher
- FortiOS 7.0 or higher
- Firewall Policy Configuration: Provide relevant information
  - From and to Interfaces, internal LAN to SDWAN Zones (Overlay)
  - Source and Destination IP addresses or blocks
  - Services allow or block per requirement
- Static Route(s): 
  - Set device IP or FQDN and priority 
- IPsec Template: provided IPsec CLI is for reference only as specific configuration will be required for IPsec tunnels. 
  - Remote Device: IP address or Dynamic DNS
  - Remote Gateway IP and subnet
  - Phase 1 and 2 proposals for SA
  - Pre-shared Key
  - Tunnel interface IP
  - Phase 2 configuration
- SDWAN Template: Basic information is provided with generic data prefilled for SDWAN template to get started. However, user must configure and refine further with the following: 
  - SDWAN Zones and member interfaces for underlay and overlay 
  - Performance SLAs with preferred values
  - SDWAN rules to steer web traffic to Zscaler gateway 

## How to use the project: 

1.	Login to FortiManager running 7.4 
2.	From the left navigational menu, click on Device Manager -> Scripts -> Import CLI Scripts

![Netskope](./Pictures/1.png)

3.	From the dialogue box, drag and drop CLI files or click on Add Files and then click on import. 

![Netskope](./Pictures/2.png)

4.	Once the scripts are uploaded, user can run them one by one to the target devices (FortiGates). 

![Netskope](./Pictures/3.png)

5.	Click OK to confirm running script. 

![Netskope](./Pictures/4.png)

6.	You should see successful installation of the script on target device. 

![Netskope](./Pictures/5.png)

7.	Repeat the process till all scripts are installed successfully, and then follow the required steps in the requirement section of this document, needed to fine tune the configuration per device for the final integration of FortiGate with Zscaler Gateway. 

## Zscaler Documentation:
Zscaler provides documentation on integration: Deployment Guide and instructions on integrating Zscaler Internet Access (ZIA) with the Fortinet platform.
https://help.zscaler.com/zscaler-technology-partners/zscaler-and-fortinet-deployment-guide
This document provides GUI examples for configuring ZIA and Fortinet. This guide is intended for standing up proof-on-concept topologies and demos, evaluating interoperability, and joint integration.

## Fortinet Documentation: 
This document demonstrates the interoperability of Zscaler Internet Access (ZIA) and Fortinet secure SD-WAN. You can use this guide as an example to deploy ZIA and Fortinet secure SD-WAN.
https://docs.fortinet.com/document/fortigate/6.4.2/sd-wan-deployment-with-zscaler/938236/zscaler-internet-access-and-fortinet-sd-wan

## Support:

Fortinet-provided scripts in this and other GitHub projects do not fall under the regular Fortinet technical support scope and are not supported by FortiCare Support Services. For direct issues, please refer to the Issues tab of this GitHub project. For other questions related to this project, contact github@fortinet.com.

## License:
License © Fortinet Technologies. All rights reserved.

