DHCP Issues

Problem: Devices are not getting an IP address.
Devices to Check:

  DHCP Server (R1, Core Switches) → Check pool availability.
  Access Switches (ASW) → Ensure DHCP snooping is configured correctly.

Diagnostic Steps & Fixes

  Check DHCP bindings (on the DHCP server)

    show ip dhcp binding
<img width="720" alt="image" src="https://github.com/user-attachments/assets/65003f3b-2dbe-4649-91ec-378009fcf556" />

Usually, if the dhcp binding table is empty, then dhcp is not leasing any addresses to clients, this could be due to there being no clients requesting/been assigned dhcp addresses, devices are configured with static IPs instead of obtaining addresses dynamically via dhcp, they won’t appear in the binding table etc, dhcp has been misconfigured etc..


Verify DHCP pools (on the DHCP server)

    show ip dhcp pool
<img width="721" alt="image" src="https://github.com/user-attachments/assets/c0bdfa11-90d3-4e36-b3eb-91312e5eb6e4" />
This DHCP server has multiple pools for different VLANs, each corresponding to specific offices (Office A, Office B, etc.). If a required pool is missing, the DHCP server will not be able to assign IP addresses to clients in that VLAN. However, whether clients can even reach the DHCP server depends on proper VLAN routing and DHCP relay configuration.


  If missing, create a pool:

    ip dhcp pool <POOL_NAME>
    network <NETWORK_IP> <SUBNET_MASK>
    default-router <ROUTER_IP>

Check DHCP relay settings (on VLAN interfaces)

    show run | include helper-address
    
