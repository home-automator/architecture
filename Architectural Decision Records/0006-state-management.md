# 6. State Management

Date: 11-08-2019

## Status

Adopted

## Context

In Home Automator, the state of Widgets must be managed in a manner that
ensures changes can be easily relayed to client applications. State is
also central to React and React Native, which Home Automator will employ
for much of the front end development.

## Decision

State will be managed server-side and transmitted to the clients via
the WebRTC data channel.  Clients may only make requests for state
changes through "Update Actions" via the data channel.  Clients will never
make state changes directly.  The server state store is the single source
of truth for Home Automator, and is the only place state mutations are
allowed.

We will use Redux for state management.  A conventional single Redux store
will be established server-side, along with requisite actions and reducers.
Subscriptions to state store changes will trigger server state change
handlers, which will propagate the latest state throughout the system.

Widgets will 1) receive and process client Update Actions, 2) perform
associated actions on devices and services, and 3) invoke resulting state
changes on the central state store.  The resulting State will then be
delivered back to Widgets for postprocessing and to the clients for
propagation throughout the UI.

## Impacts

State management is inherently complex, so the utilization of a well
established Redux solution - borrowed from popular front end patterns -
should provide for resiliency and maintainability.  Many community
developers should find state management within Home Automator to be
familiar.  The strict "full life cycle" implementation for state changes
for both clients and Widgets alike, should result in fewer bugs and
unanticipated side affects.

Redux does add some additional complexity and a lot more boilerplate
code.  However, it's all there for a reason and is what makes the above
benefits achievable.
