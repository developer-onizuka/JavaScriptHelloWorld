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
```
```
cat <<EOF > app/index.html
<script type="text/javascript" src="./alert.js"></script>
<script type="text/javascript" src="./hello.js"></script>
EOF
```
```
cat <<EOF > app/alert.js
alert("hello world");
EOF
```
```
cat <<EOF > app/hello.js
document.write("Hello world!!");
EOF
```

# 5. Test
```
npm start
```
```
google-chrome-stable http://localhost:3000
```

# 6. Create Login form
The function of **validata()** in login.js executes on click of login button in index.html. See **onclick="validate()"** in index.html.
```
cat <<EOF > app/login.js
var attempt = 3; // Variable to count number of attempts.

// Below function Executes on click of login button.
function validate(){
    var username = document.getElementById("username").value;
    var password = document.getElementById("password").value;
    if ( username == "Formget" && password == "formget#123"){
        alert ("Login successfully");
        window.location = "success.html"; // Redirecting to other page.
        return false;
    }
    else{
        attempt --;// Decrementing by one.
        alert("You have left "+attempt+" attempt;");

        // Disabling fields after 3 attempts.
        if( attempt == 0){
            document.getElementById("username").disabled = true;
            document.getElementById("password").disabled = true;
            document.getElementById("submit").disabled = true;
            return false;
        }
    }
}
EOF
```
```
cat <<EOF > app/index.html
<html>
  <head>
    <title>Javascript Login Form Validation</title>
    <!-- Include JS File Here -->
    <script type="text/javascript" src="./alert.js"></script>
    <script type="text/javascript" src="./hello.js"></script>
    <script type="text/javascript" src="./login.js"></script>
  </head>

  <body>
    <div class="container">
      <div class="main">
        <h2>Javascript Login Form Validation</h2>
        <form id="form_id" method="post" name="myform">
          <label>User Name :</label>
          <input type="text" name="username" id="username"/>
          <label>Password :</label>
          <input type="password" name="password" id="password"/>
          <input type="button" value="Login" id="submit" onclick="validate()"/>
        </form>

        <span>
          <b class="note">Note : </b>For this demo use following username and password. <br/>
          <b class="valid">User Name : Formget<br/>Password : formget#123</b>
        </span>
      </div>
    </div>
  </body>
</html>
EOF
```
```
cat <<EOF > app/success.html 
Login successfully
EOF
```
