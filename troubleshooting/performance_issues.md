 Performance Issues

Problem: High latency or packet loss.
Devices to Check:

  All Switches & Routers → Check CPU and memory usage.

Diagnostic Steps & Fixes

  Check interface errors

    show interfaces

   <img width="707" alt="image" src="https://github.com/user-attachments/assets/19b69d56-15f9-44ff-889e-f31ac6c07a6d" />


   To address high latency or packet loss, I first checked for interface errors using show interfaces, Suspecting a duplex mismatch, I verified the interface settings with show interfaces F0/2 and found it set to half-duplex while the connecting device was on full-duplex. I resolved the issue by manually setting both sides to full-duplex using interface f0/2, followed by duplex full, and after clearing interface counters with clear counters, the errors stopped, improving performance.

Monitor CPU usage

    show processes cpu sorted

Due to Packet Tracer having limited commands, Screenshots for this command can not be provided
