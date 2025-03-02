DHCP Issues

Problem: Devices are not getting an IP address.
Devices to Check:

  DHCP Server (R1, Core Switches) → Check pool availability.
  Access Switches (ASW) → Ensure DHCP snooping is configured correctly.

Diagnostic Steps & Fixes

  Check DHCP bindings (on the DHCP server)

    show ip dhcp binding

Verify DHCP pools (on the DHCP server)

    show ip dhcp pool

  If missing, create a pool:

    ip dhcp pool <POOL_NAME>
    network <NETWORK_IP> <SUBNET_MASK>
    default-router <ROUTER_IP>

Check DHCP relay settings (on VLAN interfaces)

    show run | include helper-address
