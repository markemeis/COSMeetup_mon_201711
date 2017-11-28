# Monitoring Overview

Monitoring in a container app world

---

## Roll your own items
   - snmp, JMS
    - downsides
     - sprawl and doing this.  Maybe in a base layer?

---

## Traditional 
### (mostly JVM)
   - APM
   - New Relic
   - AppDynamics

---

## logging
   - Sumo, Splunk, Elastic Stack,

---

## metrics
   - whitebox vs blackbox

---

## Prometheus deep dive

---

# Demo

---

## What to do with all that data? 

- Freshtracks
- Prelert (Part of elastic)

---
 
## Key Takeaways or what's right for my project?
- Are you using it for debugging your app?
   - Logging
   - Whitebox
- Are you using it for SLA of your app?
   - Blackbox
   - If using a JVM language
      - Add whitebox
 
 