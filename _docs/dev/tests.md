---
title: Tests
category: Development
order: 2
---

You can check that everything works by launching the test suite:

``` sh
grunt
```

If you want to launch tests from a single test, you can specify the file as command line argument.
For example, you can launch the backend tests on the `test/unit-backend/webserver/index.js` file like this:

``` sh
grunt test-unit-backend --test=test/unit-backend/webserver/index.js
```

Note: This works for backend and midway tests.

Some specialized Grunt tasks are also available, check the `Gruntfile.js` file for more:

```
grunt linters # launch hinter and linter against the codebase
grunt test-frontend # only run the fontend unit tests
grunt test-unit-backend # only run the unit backend tests
grunt test-midway-backend # only run the midway backend tests
grunt test # launch all the testsuite
```