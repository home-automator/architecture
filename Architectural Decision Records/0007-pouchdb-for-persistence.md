# 7. PouchDB For Persistence

Date: 11-08-2019

## Status

Adopted

## Context

Home Automator will ultimately require data persistence for the storage
and retrieval of documents such as state change records.  Persistent
storage will be necessary for machine learning and the presentation of
Widget Feature history graphs.

## Decision

We will add PouchDB on the client and server, along with express-pouch as
a lightweight document database server-side.  Widget state change records
will be stored as individual documents and alternatively synced to the
Home Automator Cloud for any heavy workloads such as machine learning.

On the client, PouchDB will be used for storage/retrieval of the user's
data, and any other DB related operations with the server.

## Impacts

PouchDB is a mature, proven, and popular solution for many Javascript
applications.  It pairs well with any remote CouchDB database, providing
reliable syncing capabilities.

Express-pouch effectively mimics the CouchDB API, and provides a suitable
database solution without the complexity of a fully standalone database
server.  However, express-pouch has its quirks and does not seem to receive
regular updates.  We will likely have to fix any serious bugs encountered
ourselves.
