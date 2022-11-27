# JavaScriptHelloWorld

# 1. Create directory for App
```
mkdir hello
cd hello
```

# 2. Install npm and express
```
sudo apt install -y npm
npm init -y
npm install express
```

# 3. Create server.js
If the "scripts" object does not define a "start" property, npm will run node server.js.
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
console.log(\`Listening on port ${port}...\`);
EOF
```

# 4. Create index.html and some scripts working in browser
```
mkdir app
cd app
```
```
cat <<EOF > index.html
<script type="text/javascript" src="./alert.js"></script>
<script type="text/javascript" src="./hello.js"></script>
EOF
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

# 5. Test
```
cd ..
npm start
```
```
google-chrome-stable http://localhost:3000
```
