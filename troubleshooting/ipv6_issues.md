IPv6 Issues

Problem: IPv6 devices cannot communicate.
Devices to Check:

  Routers (R1, DSWs, CSWs) → Ensure IPv6 is enabled.

Diagnostic Steps & Fixes

  Check IPv6 interface settings

    show ipv6 interface brief

Verify IPv6 routing

    show run | include ipv6 unicast-routing

  If missing, enable:

ipv6 unicast-routing
