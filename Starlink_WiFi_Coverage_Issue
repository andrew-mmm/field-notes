---
layout: default
---

# Intermittent Wi-Fi in a Multi-Room Starlink Residential Network

**Date:** 2026-08-18 <br>
**Environment:** Six-room Linear Residential Property  <br>
**Technician:** Andrew Moe Myint Maung <br>

## 1. Executive Summary

Users reported intermittent connectivity and suspected a compromised Wi-Fi password. On-site diagnostics confirmed that external connectivity was healthy. The actual problem was that a single router on a 5 GHz band signal is not stable enough to push through multiple walls in a linear building. Instead of buying new hardware or resetting the password (which would create more unnecessary work), the 2.4 GHz and 5 GHZ were separated. Stability was instantly restored, complaints ceased, and the phantom "mesh node" error in the Starlink app was dismissed as a software glitch.

## 2. The Scenario

A six-room residential property using a single Starlink Gen 2 wireless router positioned at the centre of a linear building. Approximately 18 client devices were connected (assumption: ~3 devices per room).
**Physical layout (linear):** 

	    [ Room 6  |  Room 5  |  Room 4  |  Room 3  |  Room 2  |  Room 1 ]
					                            ↑ 
                            Starlink Gen 2 router
                                                                           
Starlink app status at time of investigation: “The mesh node is currently connecting to your network.” No physical mesh node was located on site. Whether this is a genuine pending node or an application layer glitch remained unconfirmed.

## 3. Operational Constraints

- Work performed off-site during a single two-hour window on company time at the request of management.
- Visit occurred in the morning; normal evening client load was not present, so associated client count and airtime utilisation could not be meaningfully assessed.
- The previous installer stated the deployment consisted only of the Starlink Gen 2 router and dish (no mesh node). 
	- That individual has previously proven unreliable.
- Starlink app displays a pending mesh node with no available option to forget/remove.
- Channel selection and advanced radio configuration are not accessible on the Gen 2 router hardware.

## 4. Component Isolation Summary

- Starlink WAN performance
- Local Wi-Fi coverage
- DHCP / DNS behaviour
- Unauthorised device access
- User-specific or device-specific issue

Apply a low-risk, immediate improvement using only existing equipment. No unauthorised password changes, no factory resets, no speculative hardware placement.

## 5. On-Site Network Tests

- Continuous ICMP to gateway IP, public IP, and hostname, local gateway reachable with no loss - public path showed minor loss and variable latency.
- Speed test near the router via Starlink app - WAN healthy at time of test.
- Comparative device-to-router and device-to-internet tests at the router location versus the far-room bed area on both 5 GHz and 2.4 GHz.
- Channel optimization is not possible on this hardware.

# 6.1. Evidence

All tests performed during the same investigation window. Results are point-in-time and subject to Starlink’s normal variability.

| Test                              | Result                       | Interpretation                           |
| --------------------------------- | ---------------------------- | ---------------------------------------- |
| WiFiman internet speed test       | 26.6 ↓ / 20.1 ↑ Mbps         | Usable, lower than direct Starlink test  |
| Speedtest.net                     | 52.75 ↓ / 20.72 ↑ Mbps       | Starlink service working at time of test |
| Starlink basic speed test         | 97 ↓ / 19 ↑ Mbps / 56 ms     | Starlink router-to-internet path healthy |
| Device ↔ router (near router)     | 226 ↓ / 218 ↑ Mbps           | Strong local Wi-Fi near the router       |
| Device ↔ internet (near router)   | 49 ↓ / 8 ↑ Mbps / 69 ms      | Usable end-to-end near router            |
| Far-room 5 GHz ↔ router (bed)     | 0.1 ↓ / 0 ↑ Mbps             | Severe 5 GHz dead zone and coverage      |
| Far-room 2.4 GHz ↔ router (bed)   | ~10 ↓ / 10 ↑ Mbps            | Better range, still weak                 |
| Far-room 2.4 GHz ↔ internet (bed) | 4 ↓ / 0.1 ↑ Mbps / 204 ms    | Poor real-world performance              |
| Gateway ICMP                      | No loss during test          | Local gateway stable                     |
| Public IP / Hostname ICMP         | Minor loss, variable latency | WAN variation normal; DNS functional     |
## 6.2 Physical Observations

Since the specific router only has two ports with no external devices connected physically, and the physical node was never located - the phantom mesh node can be ruled out as a software glitch.

## 7. Action & Outcome

- **Immediate low-risk change:** separated the 2.4 GHz and 5 GHz SSIDs. Distant users were directed to the longer-range 2.4 GHz network, and devices near the router remained on 5 GHz.
- **Initial user feedback and follow-up testing:** indicated improved stability. The remaining coverage limitation was documented, along with the unresolved “pending mesh node” status in the Starlink app.

## 8. What Was Deliberately Not Done

- Did not change the Wi-Fi password without evidence or owner authorisation.
- Did not claim DNS/DHCP failure without isolating symptoms.
- Did not factory-reset the Starlink router.
- Did not place a mesh solution inside a dead zone without confirming strong backhaul.
- Did not treat anecdotal reports as confirmed network evidence.

## 9. Closing Note

A healthy WAN speed test proves nothing about the user’s experience. Measuring device-to-router throughput at the actual location of complaint isolated the local Wi-Fi coverage as the immediate fault. The phantom mesh node message has been ruled out as an app error. Client complaints ceased after the band split. The architecture is still a single router covering a linear building, but the immediate problem is resolved. Can be improved by installing a mesh node or an access point, but until clients continue experiencing the same problem and if management approves, no changes will be made.
