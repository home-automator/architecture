# 4. Groups As Widgets

Date: 11-08-2019

## Status

Adopted

## Context

Like other home automation systems, Home Automator must allow for the admin
to define and control groups of devices and services (Widgets).

## Decision

Groups will be implemented as special Widgets that collect and present the
selected Features, by reference, from other Widgets.  Like any other Widget,
a Group will include a primary Feature that will invoke state changes to the
Group Members of a like Feature type.

Groups will be defined via admin configuration.

## Impacts

By leveraging Widgets for Group representations, nothing special has to be
done from a UI perspective, as ultimately they will be presented as any other
Widget would.

