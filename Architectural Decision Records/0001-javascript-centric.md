# 1. Javascript Centric

Date: 11-08-2019

## Status

Adopted

## Context

Home Automator is intended to be an open source project that will
be easy for the average developer to understand and extend to
control a multitude of devices and services.  The important choice
of a programing language for the project directly impacts adoption
and the scale of contributions by the developer community.
Javascript is the #1 worldwide programing language on Github. 

## Decision

Home Automator will be predominantly built using ECMAScript 6 (ES6)
or greater.  Node will be used for the backend server components.
Client apps will be developed using ES6+ and React wherever possible.
Furthermore, any associated system components and solutions will be
selected that are Javascript centric or generally Javascript friendly.

## Impacts

This decision is expected to positively impact the speed that Home
Automator can be improved and enhanced, as the Javascript developer
community is very large and shared NPM modules are abundant.  Home
Automator will likely attract contributions from both novice and 
expert developers who may also be passionate about general technology.

This decision will certainly exclude (or discourage) those developers
who favor other popular languages such as Java or Python.  For those
individuals, there are other excellent open source home automation
projects they can readily contribute to.  However, Javascript is also
regarded as an easy language to learn, and the overall benefits of 
distinguishing Home Automator features may be appealing enough to
compel those developers to pick up the language.