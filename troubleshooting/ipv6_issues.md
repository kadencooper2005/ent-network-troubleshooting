IPv6 Issues

Problem: IPv6 devices cannot communicate.
Devices to Check:

  Routers (R1, DSWs, CSWs) → Ensure IPv6 is enabled.

Diagnostic Steps & Fixes

  Check IPv6 interface settings

    show ipv6 interface brief
  <img width="485" alt="image" src="https://github.com/user-attachments/assets/7ed79ac6-bb8b-46bb-86b5-da74d9d3402e" />
  the ipv6 interfaces are in the up state


Verify IPv6 routing

    show run | include ipv6 unicast-routing

  If missing, enable:

    ipv6 unicast-routing
  <img width="509" alt="image" src="https://github.com/user-attachments/assets/44336a58-c11d-44ef-bf98-d4e9d12d5af8" />

  ipv6 unicast-routing was missing so I enabled it using the given command
  
