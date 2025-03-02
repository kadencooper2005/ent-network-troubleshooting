OSPF Issues

Problem: OSPF neighbors are not forming or routes are missing.
Devices to Check:

  Core Switches (CSW) → Verify neighbor formation.
  Routers (R1, DSWs) → Ensure correct OSPF configurations.

Diagnostic Steps & Fixes

  Check OSPF neighbor status (on core/distribution switches and routers)

    show ip ospf neighbor

  Initially, the OSPF neighbor 10.0.0.81 was stuck in an "EXSTART" state, indicating a mismatch in OSPF parameters. After running show ip ospf interface GigabitEthernet1/1/3, I noticed that the interface was configured in a different OSPF area than the rest of the neighbors. 
  
  If no neighbors appear, ensure interfaces are in the same OSPF area:

    router ospf 1
    network <NETWORK_IP> 0.0.0.255 area <AREA_ID>

  <img width="699" alt="image" src="https://github.com/user-attachments/assets/83f64f42-1d0a-49e1-a7e2-05c79edded1c" />

  I corrected this by updating the interface configuration with router ospf 1, followed by network 10.0.0.54 0.0.0.0 area 0, and after resetting the OSPF process with clear ip ospf process, the neighbor reached the FULL state successfully.
  


Verify OSPF interfaces (on all OSPF-enabled devices)

    show ip ospf interface

<img width="699" alt="image" src="https://github.com/user-attachments/assets/49fb1fdb-e20b-499f-8008-fbc48f0b843f" />
here is a screenshot of the g1/1/3 interface in the correct area group after configuration


Check passive interfaces (on routers)

    show run | include passive-interface

  If incorrectly configured, remove passive interface:

    router ospf 1
    no passive-interface <INTERFACE>
