# Node-note

### making a node project
To make a node project you type "npm init" then define the information about your node, or you type "npm init -y" and it will be auto filled.

This is how to make a function reachable by the main javascript file. 
"module.exports.(function title)"
can include for loops or anything else a function may normally have
```
module.exports.count = () => {
    for(let i=0; i<=10; i++){
        console.log(i)
    }
}
```

### This is how you allow functions from other js files to be used on your main js file
Used for both custom fuctions as well as any npm you may use.
```
const myModule = require('./myModule.js')
var oneLinerJoke = require('one-liner-joke');
```
### .gitignore

Because your filles can become bloated with modules it is best practice to make a .gitignore file.

This is how you assure the modules wont be uploaded to your github.
```
echo "node_modules/" >> .gitignore
```

