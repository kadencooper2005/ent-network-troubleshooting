Logging & SNMP Issues

Problem: Logs are missing, or SNMP monitoring is not working.
Devices to Check:

  Syslog Server → Verify logging settings.
  SNMP-enabled Devices (Core Switches, Routers) → Ensure SNMP is configured.

Diagnostic Steps & Fixes

  Check logging configuration (on affected device)

    show logging
  after we enable logging with logging trap debugging, we are now logging all severity messages
  <img width="728" alt="image" src="https://github.com/user-attachments/assets/b1f4ba99-2f0e-4efa-a17a-4e444a6608de" />


Verify SNMP settings (on the monitored device)

    show snmp community

  If missing, configure:

    snmp-server community <COMMUNITY_STRING> r
