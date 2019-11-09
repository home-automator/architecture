# 1. ESM Extensions

Date: 11-08-2019

## Status

Adopted

## Context

Home Automator is intended to be extensible to allow for third party
developers to easily add IOT device and service support.  A Javascript
(ES6+) centric architecture has been adopted for Home Automator, with
Node as the server environment. NPM serves as a repository for over
1-million Javascript packages that have been contributed by developers.


## Decision

Home Automator extensions will be constructed as independent ES (ESM)
modules that may published to NPM and/or directly incorporated into
the Home Automator core.  These modules will export a single function
that will take defined arguments, which will allow the server to pass
references to the necessary components to properly load a functioning
extension using documented standard methods.

Extension modules, and their dependencies,  will be installed like any
other package modules (via NPM or Yarn) and their associated settings
will included in an admin defined configuration.

## Impacts

Extensibility through Javascript modules is a very common pattern and
a logical approach for a Javascript centric platform.  Therefore,
extension development for Home Automator should be a very comfortable
process for most Javascript developers - further aided by the simplicity
of our approach.  Additionally, the publishing of Home Automator
extensions as modules will increase visibility and provide a very deep
well of examples as the number of extensions grow.  Finally, the
extensions may also leverage other Javascript module dependencies,
accelerating the support for new devices and services.

The choice of ES modules (over CJS) for use in a Node system may not
be intuitive for some developers.  However, since front end development,
utilizing modern frameworks such as React and Vue, commonly make use of
ES modules, many developers should find the consistency of this approach
appealing.

