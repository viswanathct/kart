Kart
====

  An experimental mock, to help with developing Eka. The mocks should essentially be able to convey the structure of Swiggy.

ToDo
----

* Figure out, error-handling.

* Write the other apps.

* Write the imports.

* List out the modules needed to process the structure.

Notes
-----

* Everything is a resource, may it be a state, record or something else. ie: They have to support CRUD operations.

* The complex structures allowed are limited to Lists and Maps, as these are the only needed structures to represent any complex structures.

* There are six identified scopes: UI, client, server, store, shared and local. The scope local signifies the object lives in the local scopes of both the server and the client, but aren't shared. There might be a need for defining four more scopes: server-in, server-out, client-in and client-out. Below the scopes are explained.
  * UI - A sealed scope, accessible only within the UI.
  * client - Processed by the client and passed on to the server.
  * server - Processed by the server and passed on to the client. These essentially are read-only resources (objects/ properties).
  * shared - Processed on both ends and are shared. These are writable resources.
  * local - Processed on both ends, independently.
  * store - A sealed scope, accessible only within the server side store layer (SI - Storage Interface).

* Variable names are resolved from the local scope to the global scope.

* Structures act as classes, when acting as providers and as singletons, when not.

Decisions
---------

* Decided have the same syntax, without exceptions, to denote the structures, so to allow for automation.

Thoughts
--------

* Later, SQL expressions could be borrowed to achieve language independence. The choice is due to SQL being declarative, already. And also because of the availability of a well defined spec.

* Fields could be declared to be invisible, by setting the super property of the ui-schema, hidden to true.

* Lazy-evaluation on the client, of the UI, could improve performance.

* The ui:order property will be auto-generated from the YAML configuration, while transforming it to JSON.

* Package specific configuration could be specified by, using the package id-s as keys in the configuration.

* Optimization shouldn't be done on the structure, but by the parser.

* All platform functions should be expressable through configuration.

* The configuration is the common language.

* Bots could be used to analyze the flow (on production) and optimize the structure.

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

* 171229

  * 1235  Decided to use both the dot and the square-brackets notations. First, for its readability and the second, for allowing dynamic property keys.

* 180102

  * 1210  Decided to give control of the properties to respective modules. Especially to use *$* to denote self attributes of UI trees.
  * 1213  Decided to implement processors as modules, to allow for evolutionary design.
  * 1222  Decided against using *$* properties, so to be explicit, thus readable. This also would encourage the use of modules (so readability could be maintained) and also eases automation, by reducing exceptions.
  * 1413  Decided to use the $ notation of KISS, at least for the UI.
  * 1632  Reverted the decision of using $ notations. Instead restructured the existing property *properties* to accommodate the needs.
  * 1632  Split the property, named properties into fields and nodes to differentiate data fields from UI nodes.
  * 2052  Made the params property optional on resources.

* 180103

  * 0942  Decided to use query strings to represent complex objects in URLs, for readability. This could be switched to JSON through configuration.
  * 1140  Wrote the first import.
  * 1210  Renamed the property sortKey, to sortOrder, so to allow for multiple sorts.
  * 1235  Extracted out the server configs.
  * 1629  Decided to differentiate between the dot and the square brackets access of object properties. The dot denotes the property of an object, where as the square brackets denotes the object of a class.

* 180104

  * 1327  Formalized the representation of the Complex types (through their ID-s), when they are in the fields of other types.
  * 1327  Renamed sortOrder to orderBy to mimic SQL syntax, so to reduce the learning curve.
  * 1335  Introduced groupBy.
  * 1507  Introduced route.
  * 1700  Removed the properties, params. It's now inferred from existing filters.
  * 1923  Introduced the keyword, Global.
  * 1926  Introduced the keyword, None.
  * 1933  Introduced property names with dotted notation, to provide component specific configuration.
  * 1923  Introduced the keyword, Local, as the counterpart of Global.

* 180107

  * 1135  Decided to disallow explicit definitions of contracts within structures. Contracts are to be generated by mapping out the relationship of the structure with other structures. In case of structures, which are pure services, there could be an external structure of type, contract, for which no artifact would be built. The decision essentially is to enforce automatic dependency detection, so to avoid dependency conflicts like, circular dependency.
  * 1146  Introduced dotted notation for types, so to allow for namespaces.
