VLAN Issues

Problem: Devices in the same VLAN cannot communicate.
Devices to Check:

  Access Switches (ASW) → Ensure correct VLAN assignment.
  Distribution Switches (DSW) → Verify trunking and VLAN propagation.

Diagnostic Steps & Fixes

  Check VLAN assignment (on the affected switch)

    show vlan brief
  <img width="751" alt="image" src="https://github.com/user-attachments/assets/0f8f3afd-0fa8-42a2-9ebe-08561d3cbaf0" />
  The problem we have here is interface f0/1 is missing from the PCs VLAN

  what we need to do is use these commands to add f0/1 to VLAN 10

    int f0/1
    switchport access vlan 20
  <img width="663" alt="image" src="https://github.com/user-attachments/assets/c7373723-f06a-4e2c-b1b8-c925b0dae117" />

  when viewing the VLANS with show vlan brief, you can see that interface f0/1 in now in both VLAN 10 (PCs) and VLAN 20 (Phones)
  
  If missing, create the VLAN:

    vlan <VLAN_ID>

<img width="663" alt="image" src="https://github.com/user-attachments/assets/045ffb06-28ea-410b-8797-8b5a49600b82" />

  no VLANS are missing as we can see in the screen shot, each ASW in Office b should have VLANS 10,20,30,99

Verify trunk configuration (on the uplink switch)

    show interfaces trunk
  <img width="660" alt="image" src="https://github.com/user-attachments/assets/9f21bee3-2d2f-45a2-9690-af33e04e126f" />
  
Everything seems to be fine with the trunk links, so we don't have to worry about adding anything to the allowed interfaces

  If VLAN is missing, add it to the trunk:

    switchport trunk allowed vlan add <VLAN_ID>
