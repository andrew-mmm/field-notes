---
layout: default
---
# Faulty Cable Isolation - Single Uplink Cable Failure Took Down Two Network Segments

**Date:** 2026-07-15 <br>
**Environment:** (Segment A) and (Segment B) <br>
**Technician:** Andrew Moe Myint Maung

## 1. Executive Summary

Two network segments lost connectivity simultaneously. The issue was a single uplink cable failure between two switching layers - cascading to all downstream devices.

## 2. The Scenario

**Simplified topology:** Core device → Distribution switch (Segment A) → Access switch (Segment B)

The Segment B switch depended entirely on the Segment A switch for its uplink. A failure on the single cable between the core device and the Segment A switch took both segments offline.

## 3. Physical Observations

- **Upstream switch:** powered on, all port lights blinking rapidly in sync.
- **Downstream switch:** same behaviour - power present, all lights blinking fast in sync.
- **Core device uplink port:** link lights off, but comes back on when plugged in with a working spare cable.

## 4. Diagnosis

The rapid synchronised blinking on both switches with power present is consistent with devices that have no valid uplink and are continuously searching or cycling link state, or a broadcast storm.

- **Action taken at the uplink port:** the existing cable was unplugged and a known-good test cable was plugged into the same port - link lights came up immediately.
- **Conclusion:** the original cable between the core device and the Segment A switch had failed. The switches themselves were not the primary fault. Can rule out broadcast storms.

## 5. Immediate Resolution

Requested maintenance to replace the failed cable. Once the new cable was installed and linked, both area networks returned to service.

## 6. Proposed Improvement

I proposed running a second unplugged uplink cable as a cold standby between the segments (an effective but less technical alternative). In the event of another primary cable failure, the spare would be connected immediately, reducing downtime while a permanent replacement was arranged. 

Recognised downside: an idle cable in the same physical path could be degraded by environmental factors before it was ever needed. This was a low-cost, low-complexity redundancy measure aimed at reducing mean time to recovery (MTTR).

However, I was instead advised to armor / better protect the existing (replacement) cable to reduce the likelihood of future physical damage. The chosen approach prioritised improving mean time between failures (MTBF) of the single path over adding a rapid-recovery spare.

## 7. Residual Risk & Ongoing Status

- The topology remains a single point of failure. Any future loss of the link will again take down both areas.
- Recovery time still depends on physical cable integrity and maintenance response.
- This document will be updated if a similar outage repeats, or if the physical path is further modified.

## 8. What Was Deliberately Not Done

- Did not assume the downstream switches had failed simply because they went dark.
- Did not reboot or factory reset switches as the first action.
- Did not implement the cold standby cable.

## 9. Closing Note

One cable failed. Two network segments disappeared. The switches were only symptoms. Testing the uplink port with a known good cable isolated the fault in minutes. Service was restored by replacing the cable. The underlying design is the link between the network devices, and it remains as a single point-of-failure.
