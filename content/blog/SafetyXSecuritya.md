+++
title = 'Lessons from safety critical-systems and use cases in Security'
date = 2025-05-29T17:02:36+02:00
draft = false
+++

Critical computer systems are those where failure must be either prevented entirely or tightly controlled. These systems support functions that are essential to **safety**, **business continuity**, **security**, or other high-impact domains.

Ensuring the reliability of such systems requires proven engineering methods — approaches that are not just theoretical, but time-tested in real-world conditions. These methods follow a clear principle:

**Safety is not added later — it is built in from the start and carried through the entire project.**

## Eliminating Hazards

The ideal cases, is to be able to eliminate hazards entirely through better design. For example, in a motor control circuit, a poorly designed switch setup could short the battery if it partially fails—causing a fire. 

But by rearranging the circuit so that the switch controls the motor side instead of the battery side, any failure will only short the motor, which is much safer. This redesign prevents a hazardous outcome rather than just trying to manage it.

*Insent Image here*

In security engineering, OAuth 2.0 is of a framework designed to eliminate the hazards that comes from the need to share credentials with third-party applications to access a user’s resources—hosted on another service(like google drive).

The is idea is that Instead of requiring the third party to handle or store the user's password, OAuth introduces an **authorization server** that issues **time-limited access tokens**. 

These tokens grant the third party specific, limited access on behalf of the user, thereby eliminating the need to share credentials and significantly reducing the risk associated with credential theft or misuse.

Another to design out hazards is **STPA (Systems Theoretic Process Analysis)** Traditionally, when designing for safety, the approach is straightforward: "If component A might fail, we’ll add Control X to prevent it."

However, the STPA (Systems-Theoretic Process Analysis) method goes further. It assumes that even Control X might fail—or be delayed, incorrect, or completely missing. Instead of relying solely on the control working perfectly, STPA encourages designing with safety constraints, additional checks, and fallback mechanisms to ensure the system remains safe, even when controls don’t function as expected.

To build even more resilient systems, we must also consider how failures can still occur despite these safeguards—this is where **Fault Trees and Threat Trees** come in.
## Fault Trees and Threat Trees
Eliminating known hazards is only the starting point resilient systems require anticipating how failures might still occur. Fault Tree Analysis (FTA) is a structured, top-down technique used to trace the potential causes of a specific undesirable event, such as a security breach or system outage.

Think of it as reverse-engineering a disaster: you start with the failure at the top of the tree, then break it down into contributing events and conditions that could lead there.

Each branch of the tree represents a logical path showing how combinations of smaller issues might align to cause major failures. 

Once the tree is complete, you can identify targeted controls to break those paths, strengthen weak links, and reduce the chance of a cascading incident.

*Image here*

In security engineering, fault tree analysis is adapted into "attack trees" or "Threat trees Really good for Threat Hunting and Threat Modeling These trees map out how an attacker could achieve a specific malicious goal, with each node representing a step or method of attack, in some tress you even have sub branches for the counter measures.

*Image here*

Despite the availability of various techniques, the approach to safety ultimately depends on the specific problem you're addressing and the environment in which it operates. In high-stakes settings, one effective method is **Failure Modes and Effects Analysis (FMEA)**.
## Failure Modes and Effects Analysis
When dealing with a small number of well-understood, critical parts or subsystems, the FMEA approach originally pioneered by NASA and widely used in aviation takes a **bottom-up** rather than a **top-down** perspective.The process begins at the component level by identifying possible failure modes and their direct consequences. From there, we trace upward through the system to understand how each failure could affect overall functionality and ultimately impact the mission.

The analysis focuses on four key aspects: how a system might fail, its immediate effects, the cause, and the impact on the mission. This can also extend to the broader mission outcome
- **What could go wrong?** (_Failure Mode_)
- **What would happen if it did?** (_Effect_)
- **Why would it happen?** (_Cause_)
- **How serious is it, and can we detect it before it causes problems?** (*Analysis*)

Lets say you are going you want to Fly a plane over the ocean or mountains where
you can’t glide to an airport
- What could go wrong? : Engine failure
- What would happen if it did? : Plane can't continue flying
- Why would it happen? : Running out of fuel
- How bad is it? : Plane might crash 
- Solution: A second engine, one more fuel tank

Extending FMEA from safety to security: imagine you're driving home at night—your mission is to arrive safely.
- **What could go wrong?** Headlights fail
- **Effect?** You lose control
- **Cause?** Attacker hijacks the entertainment system to send a malicious "lamp off" command
- **Severity?** Crash, possibly fatal
- **Mitigation:** Use a firewall between the cabin and powertrain CAN buses (per ISO 21434)

Safety aims to prevent rare failures—like one in a billion hours. But security asks: what if someone causes that failure on purpose? This is what Dr. Ross J. Anderson calls Satan’s computer.
Next, we’ll explore how safety meets security—and why threat modeling matters.

