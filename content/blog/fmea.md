+++
title = 'Lessons from safety critical-systems and use cases in Security (FMEA) '
date = 2025-05-31T08:55:56+02:00
draft = false
+++

Despite the availability of various techniques, the approach to safety ultimately depends on the specific problem you're addressing and the environment in which it operates. In high-stakes settings, one effective method is **Failure Modes and Effects Analysis (FMEA)**

## Failure Modes and Effects Analysis
When dealing with a small number of well-understood, critical parts or subsystems, the FMEA approach originally pioneered by NASA and widely used in aviation takes a **bottom-up** rather than a **top-down** perspective.The process begins at the component level by identifying possible failure modes and their direct consequences. From there, we trace upward through the system to understand how each failure could affect overall functionality and ultimately impact the mission.

The analysis focuses on four key aspects: how a system might fail, its immediate effects, the cause, and the impact on the mission. This can also extend to the broader mission outcome
- **What could go wrong?** (_Failure Mode_)
- **What would happen if it did?** (_Effect_)
- **Why would it happen?** (_Cause_)
- **How serious is it, and can we detect it before it causes problems?** (*Analysis*)

Lets say you are going you want to Fly a plane over the ocean or mountains where
you can’t glide to an airport
- **What could go wrong?** Engine failure
- **What would happen if it did?** Plane can't continue flying
- **Why would it happen?** Running out of fuel
- **How bad is it?** Plane might crash
- **Mitigation** A second engine, one more fuel tank

Extending FMEA from safety to security: imagine you're driving home at nightyour mission is to arrive safely.
- **What could go wrong?** Headlights fail
- **Effect?** You lose control
- **Cause?** Attacker hijacks the entertainment system to send a malicious "lamp off" command
- **Severity?** Crash, possibly fatal
- **Mitigation** Use a firewall between the cabin and powertrain CAN buses (per ISO 21434)

Safety aims to prevent rare failures like one in a billion hours. But security asks: what if someone causes that failure on purpose? This is what Dr. Ross J. Anderson calls **Satan’s computer**.
Next, we’ll explore how safety meets security and why threat modeling matters.

### Sources
- [Security engineering by Dr Ross Anderson](https://www.cl.cam.ac.uk/archive/rja14/book.html)
- [Safeware: System Safety and Computers](http://sunnyday.mit.edu/book.html)
- [MIT Partnership for Systems Approaches to Safety and Security (PSASS)](https://psas.scripts.mit.edu/home/)