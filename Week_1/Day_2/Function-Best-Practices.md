# Function Best Practices
### Taken from Eloquent JavaScript.
***
### Growing Functions [Link](http://eloquentjavascript.net/03_functions.html#h_eVDWIAuyBK)

There are a couple ways that you might find yourself needing to use a function.
* You find yourself writing similar code multiple times.
* You find you need some functionality that you haven't written yet and it sounds like it deserves it's own function.

* A useful principle is to not add cleverness unless you are absolutely sure you’re going to need it. It can be tempting to write general “frameworks” for every bit of functionality you come across. Resist that urge. You won’t get any real work done—you’ll just be writing code that you never use.

### Function & Side Effects [Link](http://eloquentjavascript.net/03_functions.html#h_EdyBGBF6y/)

* Functions that create values are easier to combine in new ways than functions that directly perform side effects.

* A _pure_ function is a specific kind of value-producing function that not only has no side effects but also doesn’t rely on side effects from other code
  * When called with the same arguments, it always produces the same value (and doesn't do anything else).
  * Non-Pure functions tend to require more scaffolding to test.

***

A good name is short and explains exactly what the function does as unanbigously as possible.

* It is ideal if functions try to avoid reading outer scope variables. If a function needs some information / data, then that data should instead be passed in as a parameter, making it available within the function's inner scope.