---
layout: post
title:  "Python Class Access Control"
date:   2018-07-29 -0400
categories: Python
---

This article was inspired by my co-worker asking the meaning of the two underscores i had before a property in a Python class.

In the following Python code, I will show the convention that I use for access control of methods and properties.

```python
class Parent(object):

  # Public method.
  # This is available everywhere.
  def public_method(self):
    print(self, 'calling public method')

  # Protected method.
  # This is actually available everywhere
  # but should only be access in the class and its subclasses.
  def _protected_method(self):
    print(self, 'calling protected method')

  # Access protected methods via public methods
  def call_protected_method(self):
    self._protected_method()

  # Private method.
  # This name can only be used within the class
  # but is available outside by a different name due to name mangling.
  def __private_method(self):
    print(self, 'calling private method')

  # Access private methods via public methods
  def call_private_method(self):
    self.__private_method()

  def __repr__(self):
    return 'Parent'

class Child(Parent):

  # Reference a protected method from Parent
  def call_protected_method(self):
    self._protected_method()

  def __repr__(self):
    return 'Child'


p = Parent()
p.public_method()
p.call_protected_method()
p._protected_method() # Shouldn't do this but is allowed
p.call_private_method()
p._Parent__private_method() # Shouldn't do this but is allowed

c = Child()
c.public_method()
c.call_protected_method()
c._protected_method() # Shouldn't do this but is allowed
c._Parent__private_method() # Shouldn't do this but is allowed
```


Output
```
Parent calling public method
Parent calling protected method
Parent calling protected method
Parent calling private method
Parent calling private method
Child calling public method
Child calling protected method
Child calling protected method
Child calling private method
```

If don't like my explanation then checkout [Private, protected and public in Python](http://radek.io/2011/07/21/private-protected-and-public-in-python/) by [Radek Pazdera](http://radek.io/about/).
