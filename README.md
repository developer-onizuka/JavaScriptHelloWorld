# JavaScriptHelloWorld

```
mkdir hello
cd hello
```
```
sudo apt install -y npm
npm init -y
npm install express
```
```
cat <<EOF > server.js 
const express = require('express');
const path = require('path');

const DEFAULT_PORT = process.env.PORT || 3000;

// initialize express.
const app = express();

// Initialize variables.
let port = DEFAULT_PORT;

// Setup app folders.
app.use(express.static('app'));

// Set up a route for index.html
app.get('*', (req, res) => {
    res.sendFile(path.join(__dirname + '/index.html'));
});

// Start the server.
app.listen(port);
EOF
```
```
mkdir app
cd app
```
```
cat <<EOF > alert.js
alert("hello world");
EOF
```
```
cat <<EOF > hello.js
document.write("Hello world!!");
EOF
```
```
cat <<EOF > index.html
<script type="text/javascript" src="./alert.js"></script>
<script type="text/javascript" src="./hello.js"></script>
EOF
```
```
cd ..
npm start
```
```
google-chrome-stable http://localhost:3000
```
