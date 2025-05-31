+++
title = 'Lessons from safety critical-systems and use cases in Security (Eliminating Hazards)'
date = 2025-05-31T08:47:11+02:00
draft = false
+++


Critical computer systems are those where failure must be either prevented entirely or tightly controlled. These systems support functions that are essential to **safety**, **business continuity**, **security**, or other high-impact domains.

Ensuring the reliability of such systems requires proven engineering methods  approaches that are not just theoretical, but time-tested in real-world conditions. These methods follow a clear principle:

**Safety is not added later  it is built in from the start and carried through the entire project.**

## Eliminating Hazards

The ideal cases, is to be able to eliminate hazards entirely through better design. For example, in a motor control circuit, a poorly designed switch setup could short the battery if it partially failscausing a fire.

But by rearranging the circuit so that the switch controls the motor side instead of the battery side, any failure will only short the motor, which is much safer. This redesign prevents a hazardous outcome rather than just trying to manage it.

<img src="/images/lamp.png" alt="Description of Image">

*Circuit example*

In security engineering, OAuth 2.0 is of a framework designed to eliminate the hazards that comes from the need to share credentials with third-party applications to access user’s resources hosted on another service(like google drive).

The is idea is that Instead of requiring the third party to handle or store the user's password, OAuth introduces an **authorization server** that issues **time-limited access tokens**.

These tokens grant the third party specific, limited access on behalf of the user, thereby eliminating the need to share credentials and significantly reducing the risk associated with credential theft or misuse.

Another way to design out hazards is **STPA (Systems Theoretic Process Analysis)** Traditionally, when designing for safety, the approach is straightforward: "If component A might fail, we’ll add Control X to prevent it."

However, the STPA (Systems-Theoretic Process Analysis) method goes further. It assumes that even Control X might failor be delayed, incorrect, or completely missing. Instead of relying solely on the control working perfectly, STPA encourages designing with safety constraints, additional checks, and fallback mechanisms to ensure the system remains safe, even when controls don’t function as expected.

To build even more resilient systems, we must also consider how failures can still occur despite these safeguards, this is where [**Fault Trees and Threat Trees**](/blog/trees) comes in.


### Sources
- [Security engineering by Dr Ross Anderson](https://www.cl.cam.ac.uk/archive/rja14/book.html)
- [Safeware: System Safety and Computers](http://sunnyday.mit.edu/book.html)
- [MIT Partnership for Systems Approaches to Safety and Security (PSASS)](https://psas.scripts.mit.edu/home/)