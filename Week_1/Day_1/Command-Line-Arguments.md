# Reading on Command Line Arguments
### [Link](https://stackabuse.com/command-line-arguments-in-node-js/)
##### Note: Not including section on Minimist or Using the Yargs Module. 

`[runtime] [script_name] [argument-1 argument-2 argument-3 ... argument-n]`

* The runtime is what executes the program/script
* Arguments are seperated byt a space, some can use commas

## Using the process.argv array

* The first element of the `process.argv` array will always be a _file system path_ pointing to the `node` executable.
* The second element is the name of the JS file that is being executed
* The third element is the first argument actually passed by the user

The following script iterates through each of the command line arguments passed to the application, along with their index
```javascript
'use strict';

for (let j = 0; j < process.argv.length; j++) {
  console.log(j + ' -> ' + (process.argv[j]))
}

// Output for:
// node processargv.js hello there
0 -> .../node
1 -> .../processargv.js
2 -> hello
3 -> there
```

## Notable takeaways
`process.argv` is a accessible array that allows devs to access arguments that were passed in through cli.