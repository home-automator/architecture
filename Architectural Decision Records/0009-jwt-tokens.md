# 9. JWT

Date: 09-27-2020

## Status

Adopted

## Context

Home Automator will provide access and control to important household
technologies.  Therefore great care must be given to authentication and
authorization of users.

Use of JSON Web Tokens (JWT) is widely adopted by developers due to its
stateless self-contained nature that is ideal for a micro-service
architecture, as each service can validate access based on the signed
payload of the token.

Home Automator will be comprised of individual in-home servers, a cloud
infrastructure (for signaling, AI workloads, etc), and multiple client
applications (web, mobile, TVs, etc).  Security among these components
will be paramount.

## Decision

Access JWTs will be issued by the HA cloud service and utilized to authorize
access to protected endpoints and user databases (via CouchDB native support
for JWT access).  Access tokens will be short-lived and normally stored in
memory on the client for maximum protection.

Long-lived Refresh JWTs will also be issued to provide for continued
reissuing of Access Tokens on each client.  Refresh Tokens will be issued
via HTTP Cookie and provided via response payload for use when HTTP Cookie
storage is not feasible.  To facilitate scale, Valid Access Tokens submitted
during the refresh will be validated and reissued with extended expirations.
Extended Access Tokens will only be reissued if the Refresh Token and
submitted previous Access Token user identified in the claims match.

A token blacklist will be established to provide for scenarios where token
revocation is necessary.  Tokens will be automatically removed from the
blacklist upon expiration to ensure optimal lookup performance.  The blacklist
will be initially established in CouchDB, but may later be moved to Redis or
another suitable platform for scale.

## Impacts

There are disadvantages to the use of JWTs such as the pain of revocation and
some known exploits - which should be remediated with the proper implementation.
A token based authentication system should help facilitate scale and is aligns
well with the distributed nature of the Home Automator platform.
 
