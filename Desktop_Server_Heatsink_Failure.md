---
layout: default
---
# Desktop Server Intermittent Shutdown – Faulty Heatsink Isolation

**Date:** 2026-09-01 <br>
**Environment:** Small Office Room <br>
**Technician:** Andrew Moe Myint Maung

## 1. Executive Summary

A desktop computer used as a 24/7 server was repeatedly powering off after operating for only a few minutes. Initial investigaion considered unstable or insufficient power from the UPS. Physical inspection identified severe dust accumulation on the motherboard, an unusually slow CPU cooling fan, and aged thermal paste.

The motherboard was cleaned, fresh thermal paste re-applied, and a working CPU cooler/fan was installed from a spare desktop. The server remained powered on and resumed normal operation after the repair.

## 2. The Scenario

The deployed continuously running server desktop began exhibiting the following behavior:
- Powered on normally.
- Stayed powered on for a few minutes.
- Shut down automatically by itself.
- Repeated this cycle on repeated attempts - preventing the system from providing reliable server services.

## 3. Diagnosis

My initial hypothesis was UPS or power-supply failure because sudden shutdowns can be a result from loss of input power, UPS overload, UPS battery failure, or power-supply instability. The UPS was considered as a possible cause.

## 4. Component Isolation Summary

Direct wall power testing ruled out the UPS as the cause. The internal power-supply was not separately isolated but was deprioritized after physical inspection revealed clear thermal failure indicators.

## 5. Physical Observations

The desktop case was opened for internal inspection, and the following issues were identified:
- Significant dust buildup on the motherboard and the cooling areas.
- CPU fan rotating at an unusual slow speed compared to the fan on a known-working spare desktop - leading to the probability of inadequate CPU cooling.
- Aged / dry thermal paste between the CPU and the heatsink.
- The desktop wouldn't stay powered on long enough to run a thermal test.

## 6. Troubleshooting Steps Performed

A spare desktop was used as reference and as a source of a known working CPU cooling assembly. 

### 6.1. Harvesting the known-good cooler (spare desktop): 

- The CPU and the heatsink / fan was bonded tightly by aged thermal paste. Forcefully pulling it out was not an option since it could destroy the CPU on the spare desktop.
- I saw a comment from a YouTube short to run a CPU test to loosen the aged thermal paste.
- By not wanting to install any additional third-party apps, I ran `1..(Get-CimInstance Win32_Processor).NumberOfLogicalProcessors | ForEach-Object { Start-Job { $r=1; foreach($n in 1..2147483647){$r=$r*$n} } }` in PowerShell for 10 minutes.
- Was able to remove it with no damage to the CPU.

### 6.2. Repair (server): 

- Cleaned the dust from the motherboard, removed residue thermal paste on the CPU and the heatsink with *isopropyl alcohol*.
- Applied fresh thermal paste, and installed the working spare CPU cooler / fan.
- Reassembled the desktop and reconnected power.
- Powered the system on and verified that it remained online.

## 7. Root Cause

The primary cause of the repeated shutdowns was most likely by insufficient CPU cooling. The most probable contributing factors were:
- Heavy dust accumulation
- Slow / underperforming CPU fan
- Degraded thermal paste
- Poor heat dissipation
- Rapid CPU temperature increase

## 8. Residual Risk

The UPS was investigation and was not identified as the primary cause because direct wall-power testing did not resolve the shutdown issue. However, a separate power-cut event later indicated that the UPS may have a degraded battery or capacity issue and should be tested independently.

## 9. Closing Note

- Intermittent shutdowns on a previously stable system should prompt inspection of cooling and power delivery.
- Physical contamination (dust) and aged thermal materials can transform a previously adequate cooling solution into a failure point.
- Comparing a suspect component against a known-working spare is an effective diagnostic technique when instrumentation is limited.
