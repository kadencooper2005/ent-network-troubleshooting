Logging & SNMP Issues

Problem: Logs are missing, or SNMP monitoring is not working.
Devices to Check:

  Syslog Server → Verify logging settings.
  SNMP-enabled Devices (Core Switches, Routers) → Ensure SNMP is configured.

Diagnostic Steps & Fixes

  Check logging configuration (on affected device)

    show logging

Verify SNMP settings (on the monitored device)

    show snmp community

  If missing, configure:

    snmp-server community <COMMUNITY_STRING> r
