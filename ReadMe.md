Kart
====

  An experimental mock, to help with developing Eka. The mocks should essentially be able to convey the structure of Swiggy.

ToDo
----

* Think of using the dot notation, instead of using square brackets. As, it might be more readable.

Notes
-----

* Everything is a resource, may it be a state, record or something else.

* The complex structures allowed are limited to Lists and Maps, as these are the only needed structures to represent any complex structures.

* There are six identified scopes: UI, client, server, store, shared and local. The scope local signifies the object lives in the local scopes of both the server and the client, but aren't shared. There might be a need for defining four more scopes: server-in, server-out, client-in and client-out. Below the scopes are explained.
  * UI - A sealed scope, accessible only within the UI.
  * client - Processed by the client and passed on to the server.
  * server - Processed by the server and passed on to the client. These essentially are read-only resources (objects/ properties).
  * shared - Processed on both ends and are shared. These are writable resources.
  * local - Processed on both ends, independently.
  * store - A sealed scope, accessible only within the server side store layer (SI - Storage Interface).

Thoughts
--------

* Later, SQL expressions could be borrowed to achieve language independence. The choice is due to SQL being declarative, already. And also because of the availability of a well defined spec. As of now, the square bracket syntax of accessing members is preferred, as it could be used without changes in few languages like JS, Python, PHP and Ruby.

* Fields could be declared to be invisible, by setting the super property of the ui-schema, hidden to true.

* Lazy-evaluation on the client, of the UI, could improve performance.

* The ui:order property will be auto-generated from the YAML configuration, while transforming it to JSON.

* Package specific configuration could be specified by, using the package id-s as keys in the configuration.

Later
-----

* Scopes can be figured-out automatically. The same could also be done for data-types, this could also include the detection of type collisions.

* Libraries of custom-types like, GUID, age etc.

Log
---

* 171227

  * 1438  Initial commit, with a basic structure, pulled solely out of the existing conception of the App.
  * 1930  Added filtering.

* 171228

  * 1130  Introduced the super keys, imports and declarations, as a consequence the existing structure is nested under the super key, structure.
  * 1313  Decided to adopt JSON schema for defining the structures, to be lean.
  * 1318  Decided to postpone the envisioned DLS parsing, till the structure becomes stable.
  * 1505  Identified the scopes.
  * 1508  Decided to use lowercase for property names, for simplicity.
  * 1735  Notation, group introduced. 
