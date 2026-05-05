<image src= "<img width="1425" height="792" alt="Screenshot 2026-05-05 165302" src="https://github.com/user-attachments/assets/3e13a279-75cb-480b-a67a-01e69668631c" />

This diagram shows the **Azure resources required before a Virtual Machine (VM) can run**.
The creation flow is usually:

1. **Resource Group**
2. **Virtual Network (VNet)**
3. **Subnet**
4. **Public IP**
5. **Network Security Group (NSG)**
6. **Network Interface Card (NIC)**
7. **Associate NSG with NIC/Subnet**
8. **Virtual Machine**

Here’s what each resource does:

| Resource                     | Purpose                                     |
| ---------------------------- | ------------------------------------------- |
| Resource Group               | Logical container for all Azure resources   |
| Virtual Network (VNet)       | Private network inside Azure                |
| Subnet                       | Smaller network inside the VNet             |
| Public IP                    | Gives internet access to VM                 |
| Network Security Group (NSG) | Firewall rules for inbound/outbound traffic |
| Network Interface (NIC)      | Connects VM to network                      |
| NSG Association              | Applies security rules to NIC or subnet     |
| Virtual Machine              | Actual Linux/Windows server                 |

Typical dependency chain:

```text
Resource Group
   ↓
VNet
   ↓
Subnet
   ↓
NIC ← Public IP
   ↓
NSG Association
   ↓
VM
```

For a Linux VM using Terraform, this is why you create resources in this order:

```hcl
azurerm_resource_group
azurerm_virtual_network
azurerm_subnet
azurerm_public_ip
azurerm_network_security_group
azurerm_network_interface
azurerm_network_interface_security_group_association
azurerm_linux_virtual_machine
```

Important real-world point:

* VM cannot connect to internet without:

  * Public IP
  * NSG rule allowing SSH (port 22)

Example SSH NSG rule:

```hcl
security_rule {
  name                       = "SSH"
  priority                   = 1001
  direction                  = "Inbound"
  access                     = "Allow"
  protocol                   = "Tcp"
  source_port_range          = "*"
  destination_port_range     = "22"
  source_address_prefix      = "*"
  destination_address_prefix = "*"
}
```

Then connect using:

```bash
ssh azureuser@<public-ip>
```

Your recent Terraform work directly matches this architecture.
