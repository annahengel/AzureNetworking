# AzureNetworking

This repo consists of a resource group template deploying an environment to demo Azure Networking capabilities:
- 3 networks (2 in East US region [HubVnet, Spoke1Vnet] and 1 in CentralUS [Spoke2Vnet-2ndregion])
- Azure Firewall - with a policy
- public and private DNS zones with child zones
- 3 VMs

  ![AZ104-Networking](https://github.com/annahengel/AzureNetworking/assets/73529093/a690c74d-800a-4b0f-b6ef-ba1b83ccc8fa)


Relationships/network topology:
![topology](https://github.com/annahengel/AzureNetworking/assets/73529093/7e74614b-66b0-411c-9645-dd23d798e7b2)

- peering between HubVNet and Spoke1Vnet
- Firewall protecting HubVnet and 
