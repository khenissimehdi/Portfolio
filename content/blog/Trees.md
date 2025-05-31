+++
title = 'Lessons from safety critical-systems and use cases in Security (Fault Trees and Threat Trees) '
date = 2025-05-31T08:52:37+02:00
draft = false
+++

To build resilient systems, one must also consider how failures can still occur despite these safeguards, this is where **Fault Trees and Threat Trees** come in.

## Fault Trees and Threat Trees
Eliminating known hazards is only the starting point resilient systems require anticipating how failures might still occur. **Fault Tree Analysis (FTA)** is a structured, **top-down technique** used to **trace the potential causes** of a specific undesirable event, such as a security breach or system outage.

Think of it as reverse-engineering a disaster: you start with the failure at the top of the tree, then break it down into contributing events and conditions that could lead there.

Each branch of the tree **represents a logical path** showing how **combinations of smaller issues** might align to cause **major failures**.

Once the tree is complete, you can **identify targeted** controls to break those paths, **strengthen weak links**, and reduce the chance of a **cascading incident**.

<img src="/images/faulttree2.png" alt="Description of Image">

*Fault tree example*

In security engineering, **fault tree analysis** is adapted into **Attack trees** or **Threat trees** they are really good for Threat Hunting and Threat Modeling, these trees map out **how an attacker** could achieve a **specific malicious goal**, with each node representing a step or method of attack, in some tress you even have sub branches for the counter measures.

<img src="/images/attacktree.png" width="1500" height="600" alt="Description of Image">

*Attack tree example*

Despite the availability of various techniques, the approach to safety ultimately depends on the specific problem you're addressing and the environment in which it operates. In high-stakes settings, one effective method is [**Failure Modes and Effects Analysis (FMEA)**](/blog/fmea).

### Sources
- [Security engineering by Dr Ross Anderson](https://www.cl.cam.ac.uk/archive/rja14/book.html)
- [Safeware: System Safety and Computers](http://sunnyday.mit.edu/book.html)
- [MIT Partnership for Systems Approaches to Safety and Security (PSASS)](https://psas.scripts.mit.edu/home/)