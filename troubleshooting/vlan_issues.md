VLAN Issues

Problem: Devices in the same VLAN cannot communicate.
Devices to Check:

  Access Switches (ASW) → Ensure correct VLAN assignment.
  Distribution Switches (DSW) → Verify trunking and VLAN propagation.

Diagnostic Steps & Fixes

  Check VLAN assignment (on the affected switch)

    show vlan brief

  If missing, create the VLAN:

    vlan <VLAN_ID>

Verify trunk configuration (on the uplink switch)

    show interfaces trunk

  If VLAN is missing, add it to the trunk:

    switchport trunk allowed vlan add <VLAN_ID>
