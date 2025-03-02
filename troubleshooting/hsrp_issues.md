HSRP Issues

Problem: HSRP failover is not working, or the standby router is not taking over.
Devices to Check:

    Distribution Switches (DSW) → Ensure HSRP settings match on both devices.

Diagnostic Steps & Fixes

  Check HSRP status (on both primary and standby switches)

    show standby brief

Verify priority settings (on the primary router)

    show running-config | include standby

  Adjust priority if needed:

    interface vlan <VLAN_ID>
    standby <GROUP_ID> priority 110

Check preempt settings (on the standby router)

    show standby

  If missing, enable:

    interface vlan <VLAN_ID>
    standby <GROUP_ID> preempt

