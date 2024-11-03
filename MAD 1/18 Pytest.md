Pytest is a framework to make testing easier in python

It is opinionated: Provides several defaults to make it easier to write tests

helpful features: Can automatically set up environments, tear it down after test etc
Test fixtures and monkeypatching etc

Python standard iibrary is unittest - pytest is an alternative

Example
```python
# contents of test_sample.py
def func(x):
	return x+1

def test_answer():
	assert func(3) == 5
```
Assertion is a statement that takes an expression,  if it fails raises error
Code can be wrong or the test can be wrong

Running pytest, it looks at all files that starts with test_ , so anything starting with _test is a test file


Test for exceptions

Temporary directories 
```python
# content of test_tmpdir.py
def test_needsfiles(tmpdir):
	print(tmpdir)
	assert 0
```
assert 0 means the test fails as 0 means false
Here a temporary folder gets created without destroying anything in the dir and removes it after the test is over.

### Test fixtures
setup some data before the test
remove after the test
ex: initialize dummy database, create dummy users, files


```python
# test_fruit.py

import pytest

@pytest.fixture
def setup_list();
	return ["apple", "bannana"]

def test_apple(setup_list):
	assert "apple" in setup_list

def test_bannana(setup_list):
	assert "bannana" in setup_list

def test_mango(setup_list):
	assert "mango" in setup_list
```

The decorated function cannot be called directly, the variable setup_list does not exist.
but when the tests are run, the list gets created as text fixture, even if it is modified it will not affect the other tests.

The result will be `..F` which means two passed and third failed

### Conventions

Test discovery starts from current dir or testpaths variable
recurse into subdirectories unless specified not to

search for files test `_*.py` or `*_test.py` 
from those files: 
`test` prefixed test functions or methods outside of class
`test` prefixed test functions or methods inside `Test` prefixed test classes (without an `__init__` method)
also supports standard python `unittest`


### Testing Flask applications
create a `client` fixture known to Flask which can be used to generate requests to the flask application
within fixture dummy database, temp dir, etc can be set up
Uses `requests` library to generate the queries


Testing login and other features

