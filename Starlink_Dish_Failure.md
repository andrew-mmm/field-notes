---
layout: default
---
# Starlink Offline - Faulty Dish Isolation

**Date:** 2026-08-31 -- 2026-09-01 <br>
**Timeline:** Day 1: on-site diagnosis | Day 2: dish swap & service restoration <br>
**Environment:** Residential Multi-Room Outside Balcony <br>
**Technician:** Andrew Moe Myint Maung

## 1. Executive Summary

Site lost external internet connectivity. On-site diagnostics confirmed the local network, router, and cabling were 100% functional. The fault was isolated to a dead Starlink dish. Swapped the faulty one with a working spare dish - restoring full service.
## 2. The Scenario

Starlink service at a residential Units went offline. The Starlink app showed a red status on the particular Starlink dish while others remaind online (green). Client reported no internet connectivity. User reported that the light on the router remained solid white. They've unplugged and plugged back the power, but the issue persists. I was called to physically go on-site to troubleshoot the issue.
## 3. Component Isolation Summary
| **Component**    | **Test Result**                                      | **Conclusion**        |
| ---------------- | ---------------------------------------------------- | --------------------- |
| Router           | Gateway reachable, DHCP working, links to spare dish | Healthy               |
| Cable            | Original cable works with spare dish                 | Healthy               |
| Original Dish    | No link with original or spare cable                 | Faulty                |
| Starlink Service | Other terminals online                               | Not a regional outage |
## 4. Diagnosis
### 4.1 On-Site Network Tests

The first things I noticed when I got to the Units were:
- The router was fully powered on with a solid white light - no light would suggest otherwise.
- Wi-Fi SSID from the router was broadcasting and clients could connect to it, but no internet access.
- I was able to ping the router's default gateway and observed that it was handing out DHCP addresses normally - confirming that local connectivity was healthy.
- Pings to 1.1.1.1 was `Destination Net Unreachable` so I was able to confirm that the main issue was external connectivity.
### 4.2 Physical Observations

After the initial network tests, I came to the conclusion that the issue was either the cable (connection between the router and the dish) or the dish itself. One thing I've also noticed with the dish: the mount wasn't stable because even with a light breeze, the dish was noticeably wobbling / shaking (poorly welded probably).
## 5. Isolation Steps Performed

1. Power-cycled the router and re-seated the cables on both ends - no recovery.
2. Tested with a spare working cable between router and dish - still no internet.
3. Tested with a spare working dish (same type) while keeping the router in place.
4. With the spare dish connected, Starlink app status changed from unreachable to active and it began its orientation process. 
The substitution was the decisive test. The router successfully communicated with the spare dish,proving the router and test cable path were functioning.
## 6. Recovery & Confirmation

- Spare dish eventually came back online after given a clearer sky view.
- External pings to 1.1.1.1 were successful with 0% packet loss, and minor packet loss to google.com.
- Original cable was re-tested with the working dish and functioned normally.
- Service was fully restored once the spare dish was properly placed back on the rooftop with a stabler mount.
## 7. Root Cause

The original Starlink dish was faulty. It failed to establish a usable link even after power-cycling, testing with a known-good working cable. Replacing with a spare dish immediately allowed the router to detect the dish and began the orientation process, confirming the dish as the failed component.
## 8. Additional Notes

- Dish mount stability was poor (visible wobble in wind). While it might not be the primary cause of the outage, a loose mount might contribute to intermittent performance and should be addressed when the replacement dish is permanently installed.
- Temporary testing was performed with the spare cable and dish on the balcony - final stable operation required clear sky view.
- Both dishes are actuated (motorized) type.
## 9. Closing Note

The local network and router were never the problem. The failure was isolated to the original mounted dish through systematic testing and substitution. Once a working dish was connected and given a clear sky view, service returned and the original cable was confirmed good.
