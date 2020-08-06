# Node-note

### making a node project
To make a node project you type "npm init" then define the information about your node, or you type "npm init -y" and it will be auto filled.

### .gitignore

Because your filles can become bloated with modules it is best practice to make a .gitignore file.

This is how you assure the modules wont be uploaded to your github.
```
echo "node_modules/" >> .gitignore
```

### Create modules 
This is the syntax to create modules
```
var express = require('express');
var router = express.Router();
```

### Export modules
module.export. is the proper syntax to make this aquireable in another file within your project
```
const PI = 3.14159265359;

export function area(radius) {
  return (radius ** 2) * PI;
}

export function circumference(radius) {
  return 2 * radius * PI;
}
```
### Import modules
```
import { area, circumference } from './circle.mjs';

const r = 3;

console.log(`Circle with radius ${r} has
  area: ${area(r)};
  circunference: ${circumference(r)}`);
```
### Node packages
Used NPM packages
express, nodemon, ejs

### Adding express to node app
Firstly you install express by typing 
"npm i express" into console
Then add this syntax to use 
```
const express = require('express')
const app = express()
```

### This is how you allow functions from other js files to be used on your main js file
Used for both custom fuctions as well as any npm you may use.
```
const myModule = require('./myModule.js')
var oneLinerJoke = require('one-liner-joke');
```

### Express routes
Simple console log to page
```
app.get('/', function (req, res) {
  res.send('hello world')
})
```

### Views
Views are ejs files with javascript and html 
can be called in express routes like so 
```
app.get('/foods', function(req, res) {
  res.render('foods', {title: 'Favorite Foods', foods: ['hotdog', 'burger']});
});
```

### Layouts
Partial page that can be added to all ejs files
example: adds links to all other pages
```
<!DOCTYPE html>
<html lang="en">
<head>

    <title>Faves&Hates</title>
</head>
<body>
    <ul>
        <li><a href='/faves/foods'>Favorite Foods</a></li>
        <li><a href='/faves/animals'>Favorite Animals</a></li>
        <li><a href='/hates/foods'>Just Bad Foods</a></li>
        <li><a href='/hates/animals'>Worst Animals</a></li>
      </ul>
    <%- body %> 
</body>
</html>
```

### Controllers
Used to simplify express routes which otherwise could be very hard to keep track of.

Must add Router() and module.exports so the express routes can be referenced back to
```
var express = require('express');
var router = express.Router();

router.get('/foods', function(req, res) {
  res.render('faves/foods', {title: 'Favorite Foods', foods: ['hotdog', 'burger']});
});

router.get('/animals', function(req, res) {
  res.render('faves/animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});

module.exports = router;
```

Also requires reference to be established on main js file.
This tells the app to reference to the controller folder when the url includes 
"/faves" or "/hates"
```
app.use('/faves', require('./controller/faves'));
app.use('/hates', require('./controller/hates'));
```
