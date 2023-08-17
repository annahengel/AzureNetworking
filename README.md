# AzureNetworking

This repo consists of a resource group template deploying an environment to demo Azure Networking capabilities:

Resource Topology:
![AZ104-Networking2](https://github.com/annahengel/AzureNetworking/assets/73529093/38fc8acf-36cb-4115-8619-ac0a719cadc3)

Description:
- 3 networks:
    - 2 in EastUS region:
      - HubVnet - 10.0.0.0/16,
      - Spoke1Vnet - 10.1.0.0/16
    - 1 in CentralUS:
    -   Spoke2Vnet-2ndregion - 10.2.0.0/16
- Azure Firewall - with a policy
- public and private DNS zones with child zones
- 2 Standard VMs
- VPN Gateway
- Route table
  
Relationships/network topology:
![image](https://github.com/annahengel/AzureNetworking/assets/73529093/d8ebf471-ba35-4eb3-9333-ef6435714645)

Description:
- A typical Hub-and-Spoke Topology with traffic to and from Spokes is routed through the Firewall (forced tunneling and/or UDR).
        - VM: AZ104-Firewall-VM - publicly accessibile over RDP over Firewall (DNAT rule)
        - VM: AZ104-Peering - accessible over Bastion
  - Firewall policy:
  -     application: allow www.google.com and www.bing.com over HTTP/s to 10.0.1.4 (AZ104-Peering)
  -     network: allowed custom DNS
  -     dnat: allowed RDP to the Az104-Firewall through the Firewall
  - Public DNS Zone resolving az104.com (with a child zone: student.104.com) - domain not purchased
  - Private DNS Zone resolving az104.net - Spoke1Vnet connected for autoregistration adn HubVnet for resolution
  - Peering enabled between HubVNet and Spoke1Vnet with "allow gateway transit"
  - Route table: traffic towards the internet routed through the IIP of the firewall for the subnets hosting VMs in HubVnet and Spoke1Vnet





