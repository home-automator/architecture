# 5. WebRTC P2P

Date: 11-08-2019

## Status

Adopted

## Context

Home Automator must allow for both local and outside network control of
devices and services to be fully useful.  The typical home network
consists of a consumer level router/firewall.  Configuring remote access
to local network resources for the average admin is complicated and prone
to the introduction of security risks.

WebRTC is a maturing standards based approach to multimedia and data
communication among peers with little reliance on infrastructure beyond
signaling.  WebRTC browser support is mainstream, and native implementations
for iOS and Android are available.

## Decision

Home Automator will use of WebRTC for P2P communications.  Multimedia
channels will be used to allow for server resources such and video to be
streamed to clients.  Data channels will be be used for the exchange of
state and client invoked actions.

We will utilize the simple-peer module, which provides both browser and
Node support - initially using the default public NAT traversal services.
Default signaling will be provided via Home Automator Cloud.

## Impacts

WebRTC will greatly simplify the access to Home Automator server instances
from outside the home network, and also provide streaming capabilities
for media such as camera video feeds and audio without the reliance of
additional technologies.

Client platform support may be spotty, so a fallback approach may ultimately
be required.

