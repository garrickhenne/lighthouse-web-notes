### Tips

* Returning a console.log function is not a good practice generally. like so:
  ```javascript
  ...
  return console.log("I'm here!");
  ...
  ```
  Instead, consider just calling console.log() as in most cases we have no need to return this function itself.
  ```javascript
  console.log("I'm here!");
  return;
  ```

* Make sure to add comments where needed or else you'll forget what you're code was doing in the future!

