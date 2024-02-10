OOP in [[Ruby]] works similarly to other languages, with a few notable exceptions.
* member variables are private by default
* getters are defined as `varname` by convention
* setters must follow the pattern `varname=`
* instance variables are prefixed with `@`
* static variables are prefixed with `@@` and are singleton but not const
* static const variables do not have a prefix and are ALL CAPS.
* static methods are prefixed with `self.`.
* `self` is equivalent to `this` in C# or java.
* You can add additional functionality a class using the same syntax you would use to define a new class. ("monkey patching")

