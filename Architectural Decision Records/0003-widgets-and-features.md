# 3. Widgets and Features

Date: 11-08-2019

## Status

Adopted  

## Context

Home automation systems that are extensible usually require that the
developer implement their extension using or conforming to a predefined
entity class with predefined controllable capabilities.  For instance, a
developer might implement the latest smart bulb using a Light class which
includes an On/Off and Brightness capability.  By constraining the
developer to defined classes and/or capabilities, UI representations are
relatively simple and uniform.  However, this approach can also be limiting
when unique devices and services emerge that don't fit well within that
class system.  Or with some systems, the capabilities of a single device
may be represented as multiple entities rather than one.

## Decision

Home Automator will incorporate a flexible approach to the classification
of devices and services.  There will only be one entity class called
"Widget", which will be assigned characteristic "Features" that each will
include properties that define its capability, state, labeling, and other
key attributes.

Widgets will be implemented as an ES Class, which will be passed by reference
and extended through Home Automator Extension modules.  Each Feature will
be assigned properties from immutable Feature Types such as SWITCH, HUE,
LUMINOSITY, SENSOR, etc..  Each Widget may include multiple Features.

Home Automator client app implementations will receive JS data Objects that
contain the Widget properties, including Features and state, that allow for
proper representation in the UI.

## Impacts

Because each Widget can include multiple Features, a unique device or service
representation is easily achievable.  For example, a smart wall plug can not
only include a binary Switch Feature, but also incorporate a energy usage
Sensor Feature as well.  In other systems, those two capabilities may require
representation as two separate devices.

The abstraction of devices and services also significantly normalizes the
development of extensions, albeit while introducing the slight complexity
associated with defining feature properties.  Also, the lack of predefined
entity classes naturally introduces a possible lack of uniformity.