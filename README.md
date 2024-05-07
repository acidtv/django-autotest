# django-autotest

Autotest automatically runs django tests when python files change.

 * It only runs the tests from the django app in which the file(s) changed
 * If you change a `test_*.py` file, only the tests in that file are run
 * If tests fail it keeps running only the failed tests on subsequent changes


```
$ autotest
Watching for changes to python files...


########################################################
Testing home.tests
########################################################
Creating test database for alias 'default'...
Found 1 test(s).
System check identified no issues (0 silenced).
F
======================================================================
FAIL: test_foo (home.tests.FooTestCase)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/alex/tmp/djangotest/mysite/home/tests.py", line 6, in test_foo
    self.assertFalse(True)
AssertionError: True is not false

----------------------------------------------------------------------
Ran 1 test in 0.000s

FAILED (failures=1)
Destroying test database for alias 'default'...

# 🔴 1 Tests failed!
# - FAIL: home.tests.FooTestCase
# 0 testcase(s) in queue.
```

## Installation

 * Clone the repo
 * Install watchfiles with `$ pip install --user watchfiles`
 * Put autotest in a directory that's in your `$PATH`
   * For example on Linux you can link it in `/usr/local/bin` with `ln -s /path/to/repo/autotest /usr/local/bin/autotest`

## Usage

In your Django root directory run: `$ autotest`.

```
$ autotest --help
usage: autotest [-h] [-k PATTERN]

Automatically run Django tests when files change.

options:
  -h, --help  show this help message and exit
  -k PATTERN  Only run test methods and classes that match the pattern. Passed to Django.
```

# Caveats

 * Tests are only found if they are in a class of which the name ends with "TestCase"

