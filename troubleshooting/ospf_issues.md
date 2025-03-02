OSPF Issues

Problem: OSPF neighbors are not forming or routes are missing.
Devices to Check:

  Core Switches (CSW) → Verify neighbor formation.
  Routers (R1, DSWs) → Ensure correct OSPF configurations.

Diagnostic Steps & Fixes

  Check OSPF neighbor status (on core/distribution switches and routers)

    show ip ospf neighbor

  If no neighbors appear, ensure interfaces are in the same OSPF area:

    router ospf 1
    network <NETWORK_IP> 0.0.0.255 area <AREA_ID>

Verify OSPF interfaces (on all OSPF-enabled devices)

    show ip ospf interface

Check passive interfaces (on routers)

    show run | include passive-interface

  If incorrectly configured, remove passive interface:

    router ospf 1
    no passive-interface <INTERFACE>
