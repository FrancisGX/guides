Best Practices
==============

A guide for programming well.

General
-------

* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* [Exceptions should be exceptional].
* [Keep the code simple].

[Exceptions should be exceptional]: http://www.readability.com/~/yichhgvu
[Keep the code simple]: http://www.readability.com/~/ko2aqda2

Object-Oriented Design
----------------------

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small objects with a single, well-defined responsibility. When an
  object exceeds 100 lines, it may be doing too many things.
* [Tell, don't ask].

[Tell, don't ask]: http://robots.thoughtbot.com/post/27572137956/tell-dont-ask

Ruby
----

* Avoid optional parameters. Does the method do too much?
* Avoid monkey-patching.
* Prefer `private` when indicating scope. Use `protected` only with comparison
  methods like `def ==(other)`, `def <(other)`, and `def >(other)`.

Rails
-----

* Avoid naming methods after database columns in the same class.
* Don't change a migration after it has been merged into master if the desired
  change can be solved with another migration.
* Don't use instance variables in partials. Pass local variables to partials
  from view templates.
* Don't use SQL or SQL fragments (`where('inviter_id IS NOT NULL')`) outside of
  models.
* If there are default values, set them in migrations.
* Try to limit the number of instance variables in each controller action / view.

Testing
-------

* Avoid using instance variables in tests.
* Avoid testing private methods.
* Use an `it` example or test method for each execution path through the method.

Sass
----

* Use `image-url` and `font-url`, not `url`, so the asset pipeline will re-write
  the correct paths to assets.

Browsers
--------

* Don't support clients without Javascript.
* Don't support IE6 or IE7.
