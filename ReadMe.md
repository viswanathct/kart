Kart
====

  An experimental mock, to help with developing Eka. The mocks should essentially be able to convey the structure of Swiggy.

Notes
-----

* Everything is a resource, may it be a state, record or something else.

* The complex structures allowed are limited to Lists and Maps, as these are the only needed structures to represent any complex structures.

Thoughts
--------

* Later, SQL expressions could be borrowed to achieve language independence. The choice is due to SQL being declarative, already. And also because of the availability of a well defined spec. As of now, the square bracket syntax of accessing members is preferred, as it could be used without changes in few languages like JS, Python, PHP and Ruby.

* Fields could be declared to be invisible, by setting the super property of the ui-schema, hidden to true.

* Lazy-evaluation on the client, of the UI, could improve performance.

Log
---

* 171227

  * 1438  Initial commit, with a basic structure, pulled solely out of the existing conception of the App.
  * 1930  Added filtering.
