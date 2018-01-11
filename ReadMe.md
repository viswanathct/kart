Kart
====

  An experimental mock, to help with developing Eka. The mocks should essentially be able to convey the structure of Swiggy.

ToDo
----

* Write the other apps.

* Write the imports.

* Write an MVP.

* List out the modules needed to process the structure.

Notes
-----

* The essential goal is to encourage, the formalization of frequently used structures.

* Everything is a resource, may it be a state, record or something else. ie: They have to support CRUD operations.

* The complex structures allowed are limited to Lists and Maps, as these are the only needed structures to represent any complex structures.

* Variable names are resolved from the local scope to the global scope.

* Structures act as classes, when acting as providers and as singletons, when not.

* Only changes would be transmitted by default.

* Object overlays have three parts: first the extension through providers, then any customizations and then the hiding of items by making them private.

* Imports are simple object extensions, with collision detection. Implicit overlays are considered as collisions. Imports should occur only from top to bottom and not right to left. ie: Providers shouldn't override earlier providers (left to right), but customizations should be done for such providers (top to bottom). This is to reign-in hidden structures.

* A lot of assumptions are made, like, by default, time being persisted in UTC and displayed in local time.

Decisions
---------

* Decided have the same syntax, without exceptions, to denote the structures, so to allow for automation.

* Decided to infer permissions, rather than providing structures to explicitly set them, as the later doesn't seem to be necessary. Even if it were, it could later be added as a plugin.

* Decided to combine create and update as a single method, save, as no specific reason for the separation could be imagined. Though the method is on, the core follows REST to play well with other tools. This also would reflect on the available permissions. Instead of CRUD permissions, there only would be read / write access (like a filesystem). Any further restriction could be imposed through code.

* Nulls won't equal anything else, even other nulls (as in SQL), so to ease declarations.

* Decided not to have partial providers, as it would mess-up the structure by complicating the abstractions. ie: Parts of structures, implicitly combined to make a a structure is often impossible to comprehend or maintain.

* Routes of the UI represent actual visual elements. Elements are under a strict tree, even the loose ones like message-boxes reside under global.popups element.

* Every property would support the value, none, to unset existing settings and possibly use defaults. And the value inherit, to inherit the value of its parent. just like CSS.

* Evaluated items are read-only by default.

* Decided to disallow YAML tags, as they aren't needed and also limit some expressions. This goes for any other feature that fulfills the said conditions.

Thoughts
--------

* Writing native services would quicken the MVP.

* SQL expressions could be borrowed to achieve language independence. The choice is due to SQL being declarative, already. And also because of the availability of a well defined spec.

* Fields could be declared to be invisible, by setting the super property of the ui-schema, hidden to true.

* Lazy-evaluation on the client, of the UI, could improve performance.

* The ui:order property will be auto-generated from the YAML configuration, while transforming it to JSON.

* Package specific configuration could be specified by, using the package ID-s as keys in the configuration.

* Optimization shouldn't be done on the structure, but by the parser.

* All platform functions should be expressable through configuration.

* The configuration is the common language.

* Bots could be used to analyze the flow (on production) and optimize the structure.

* Examples with increasing complexity to implement D3 (design driven development).

* A structure can't be built, until it's fully parsed (along with all the dependencies.). This requires a set of tools to debug the parsing process. It would be prudent to allow for partial builds too. Partial builds could also speed up the build process.

* Dictionaries are implicitly converted to a list of its keys according to the context. The same goes for the conversion of a single item list to a variable (as in SQL). This greatly simplifies the implementation.

* i18n could be done through overriding existing properties with language specific extensions.

* DB migrations through object diffs, with previous commits. Or maintaining a last-known-good-build file of the super structure.

* Dev version of the Apps could be built by adding dev-plugins to the build.

* Message boxes could be derived through schema, with buttons replacing radios.

Learned
-------

* Type specific interpretation of nulls isn't possible. Ex: Interpreting null for the type integer as 0, could prove correct for addition, but not for multiplication.

* Applying functions over lists are a lot more efficient, than applying the same over items, as the abstraction allows for Optimizations.

Later
-----

* Scopes can be figured-out automatically. The same could also be done for data-types, this could also include the detection of type collisions.

* Libraries of custom-types like, GUID, age etc.

* Generating mock data from the structures. Though it wouldn't be needed for testing, it might be for demos.

* A plugin for, request batching.

* Generating clients for testing (probing) purposes.

* Unused variables could be detected and skipped from the builds.

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

* 180106

  * 1135  Decided to disallow explicit definitions of contracts within structures. Contracts are to be generated by mapping out the relationship of the structure with other structures. In case of structures, which are pure services, there could be an external structure of type, contract, for which no artifact would be built. The decision essentially is to enforce automatic dependency detection, so to avoid dependency conflicts like, circular dependency.
  * 1146  Introduced dotted notation for types, so to allow for namespaces.
  * 1200  Decided to do away with the defined scopes. Scopes are to be derived from the namespace names of the apps. This way they would be extendable.
  * 1210 Introduced the property, private, to compensate for the removed scope, local.
  * 1345  Decided not to transfer private properties for the intended cross-checking of them with their public counterparts, as it's a wrong implementation and it complicates the structure. In case of a needed validation, one more layer of abstraction should be used between the expected and actual values, through an intermediate object (like a view).
  * 1630  Introduced the property filter.extend.

* 180109

  * 1700  Introduced sync types: wait and noWait.

* 180110

  * 1114  Renamed the property group.children to group.members.
  * 1157  Redid the structure of the master file, to follow a common syntax of the other files. It is now a special file only by convention.
  * 1400  Decided to have standardized errors.
  * 1422  Figured out error handling.
  * 1635  Replaced the property private, with sharing, so to support readOnly and writeOnly fields.
  * 1645  Reassigned the property, config to handler specific configuration.
  * 1650  Introduced the property field<x>.optional.
  * 1654  Introduced the function, refresh, to re-evaluate expressions.
  * 1745  Introduced the function, ensure.

* 180111

  * 1000  Decided not to use hyphens in property names and values, so to ease the translation to other languages. camelCase would be used instead.
  * 1003  Introduced mixins.
  * 1335  Described the main-screen.
