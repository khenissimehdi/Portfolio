+++
title = 'Lessons from safety critical-systems and use cases in Security (Eliminating Hazards)'
date = 2025-05-31T08:47:11+02:00
draft = false
+++


Critical computer systems are those where failure must be either prevented entirely or tightly controlled. These systems support functions that are essential to **safety**, **business continuity**, **security**, or other high-impact domains.

Ensuring the reliability of such systems requires proven engineering methods approaches that are not just theoretical, but time-tested in real-world conditions. These methods follow a clear principle:

**Safety is not added later  it is built in from the start and carried through the entire project.**

## Eliminating Hazards

The ideal cases, is to be able to eliminate hazards entirely through better design. For example, in a motor control circuit, a poorly designed switch setup could short the battery if it partially failscausing a fire.

But by rearranging the circuit so that the switch controls the motor side instead of the battery side, any failure will only short the motor, which is much safer. This redesign prevents a hazardous outcome rather than just trying to manage it.

<img src="/images/lamp.png" alt="Description of Image">

*Circuit example*

## OAuth 2.0 as a security hazard elimination example
In security engineering, OAuth 2.0 is of a framework designed to eliminate the hazards that comes from the need to share credentials with third-party applications to access user’s resources hosted on another service(like google drive).

The is idea is that Instead of requiring the third party to handle or store the user's password, OAuth introduces an **authorization server** that issues **time-limited access tokens**.

These tokens grant the third party specific, limited access on behalf of the user, thereby eliminating the need to share credentials and significantly reducing the risk associated with credential theft or misuse.

## STPA (Systems Theoretic Process Analysis)
Another way to design out hazards is **STPA (Systems Theoretic Process Analysis)** Traditionally, when designing for safety, the approach is straightforward: "If component A might fail, we’ll add Control X to prevent it."

However, the STPA (Systems-Theoretic Process Analysis) method goes further. It assumes that even Control X might failor be delayed, incorrect, or completely missing. Instead of relying solely on the control working perfectly, STPA encourages designing with safety constraints, additional checks, and fallback mechanisms to ensure the system remains safe, even when controls don’t function as expected.

---

## Example of Hazard elimination using STPA Applied to Autonomous Drone Delivery

Imagine an autonomous drone designed to deliver packages in a dense urban environment. The goal is to avoid collisions, deliver to the correct location, and land safely even if systems fail.

### Hazard: The drone drops the package in the wrong location or crashes due to a misinterpreted sensor signal.

### Misalignments That Can Cause the Hazard:

* **GPS signal is weak**
  → *Drone perception system*: Trusts faulty GPS data without cross-checking

* **Sensor reports malfunction**
  → *Control logic*: Makes decisions without verifying sensor health

* **Operator updates mission mid-flight**
  → *Human operator*: Assumes the drone can immediately adapt safely

* **Communication drops in flight**
  → *Wireless comm module*: Drone continues without updated commands

* **Package latch reports "locked" incorrectly**
  → *Hardware module*: Drone proceeds to release based on incorrect state

### STPA-Inspired Constraints and Safety Measures:

1. **Sensor Cross-Validation**: Require at least two independent sensors (e.g., GPS + vision) to agree before location is trusted.
2. **Fallback Modes**: If sensors are degraded, the drone hovers and signals for human intervention.
3. **Operator Confirmation**: Interface requires explicit confirmation before mission changes take effect.
4. **Comms Redundancy**: Drone automatically returns to base if communication is lost for more than 10 seconds.
5. **Package Lock Verification**: Drone will not release unless physical and software confirmation both succeed.

### Narrative Flow:

* The drone takes off with a package and heads toward its target.
* Mid-flight, urban interference corrupts GPS. The drone detects the inconsistency between GPS and visual landmarks.
* Instead of proceeding, it enters a hover-safe state and pings the operator.
* Communication drops briefly; the drone holds position using onboard logic.
* The operator reconnects, reviews the error, and authorizes a safe return to base.
* Throughout the event, hazard is avoided not because any one system was perfect, but because the design anticipated misalignment and responded with layered safety constraints.

### Key Insight:

The hazard didn’t emerge from one failure it emerged from **interacting assumptions across systems**. STPA helps identify where these assumptions might misalign and guides the design of **constraints, feedback, and failsafes** to eliminate hazards before they lead to loss.

---

To build even more resilient systems, we must also consider how failures can still occur despite these safeguards, this is where [**Fault Trees and Threat Trees**](/blog/trees) comes in.


---


### Sources
- [Security engineering by Dr Ross Anderson](https://www.cl.cam.ac.uk/archive/rja14/book.html)
- [Safeware: System Safety and Computers](http://sunnyday.mit.edu/book.html)
- [MIT Partnership for Systems Approaches to Safety and Security (PSASS)](https://psas.scripts.mit.edu/home/)
