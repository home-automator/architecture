# 6. Redux State Management

Date: 11-01-2020

## Status

Adopted (Supersedes 0006)

## Context

In Home Automator, the state of Widgets must be managed in a manner that
ensures changes can be easily relayed to client applications. State is
also central to React and React Native, which Home Automator will employ
for much of the front end development.

ADR 0006 previously established Redux as the central store, which caused
significant complexity impacting maintainability.

## Decision

State will be managed server-side and transmitted to the clients via
the WebRTC data channel.  Clients may only make requests for state
changes through "Update Actions" via the data channel.  Clients will never
make state changes directly.  The server state store is the single source
of truth for Home Automator, and is the only place state mutations are
allowed.

We will use deep-state-observer (as a replacement for Redux) for state
management.  A single store will be established server-side.  Subscriptions
to state store changes will trigger server state change handlers, which will
propagate the latest state throughout the system.

On the server, Widgets will 1) receive and process client Update Actions,
2) perform associated actions on devices and services, and 3) invoke
necessary state changes on the central state store.  The resulting State
will then be delivered back to Widgets for postprocessing and to the clients
for propagation throughout the UI.  There will be strict adherence to this
State Change Life Cycle to ensure consistency.

## Impacts

The elimination of Redux decreases complexity and boilerplate code. The
deep-state-observer module provides a simpler alternative while still
adhering to immutability concepts and adding robust subscription features.