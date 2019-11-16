# 8. Embedded NodeRed

Date: 11-08-2019

## Status

Adopted

## Context

Home Automator will require automation capabilities that will allow the
creation of routines for automatically controlling Widgets based on
time, state, and other changes throughout the system.

The IFTTT pattern is a popular choice among other home automation
systems.  While this approach is simple and useful for basic automation,
it falls flat when more complex automation is desired.  It is also
limited to the scope of the capabilities of the home automation system.

NodeRed is a popular open source flow based visual programing environment
written in Javascript.  It originated from IBM, and has many developer
community contributed modules called Nodes.

## Decision

We will add embedded NodeRed to Home Automator and include special custom
Nodes that will allow full automation of Widgets within NodeRed Flows.
The NodeRed runtime editor will only be accessible directly from the
server and will be customized to blend into the admin UI.

## Impacts

While we may ultimately add IFTTT style automation capabilities, NodeRed
provides for virtually any imaginable automation routines, while also
providing a an easy to understand interface that will serve both experts
and novices well.

Home Automator automation flows can also leverage the many community
contributed Nodes, extending well beyond the limits of Widget Features.

Due to NodeRed architecture limitations, administration of automation
flows will be restricted to the server only (not available within the
client apps).  To overcome this limitation, heavy modification of NodeRed
would likely be necessary.
 
