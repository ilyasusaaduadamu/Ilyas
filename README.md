<!DOCTYPE html>
<html lang="ha">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ilyasu Web</title>
  <style>
    body {
      background-color: white;
      color: blue;
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }
    .container {
      width: 90%;
      max-width: 400px;
      margin: 50px auto;
      padding: 20px;
      border: 2px solid blue;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,255,0.3);
    }
    h1 {
      margin-bottom: 20px;
    }
    input {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid blue;
      border-radius: 10px;
    }
    button {
      background-color: blue;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    button:hover {
      background-color: darkblue;
    }
    .link {
      color: blue;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="container" id="signupPage">
    <h1>Register</h1>
    <input type="text" id="signupName" placeholder="Enter your name"><br>
    <input type="email" id="signupEmail" placeholder="Enter your email"><br>
    <input type="password" id="signupPassword" placeholder="Enter your password"><br>
    <button onclick="signup()">Sign Up</button>
    <p>Already have an account? <span class="link" onclick="showLogin()">Login</span></p>
  </div>

  <div class="container" id="loginPage" style="display:none;">
    <h1>Login</h1>
    <input type="email" id="loginEmail" placeholder="Email"><br>
    <input type="password" id="loginPassword" placeholder="Password"><br>
    <button onclick="login()">Login</button>
    <p>Don’t have an account? <span class="link" onclick="showSignup()">Sign Up</span></p>
  </div>

  <div class="container" id="homePage" style="display:none;">
    <h1>Welcome to Ilyasu Web</h1>
    <h3>Account Balance: ₦0.00</h3>
    <p>Today’s Earnings: ₦0.00</p>
    <p><b>Invite Friends</b></p>
    <p><b>Sign In Bonus</b></p>
    <p><b>Task Center</b></p>
    <p><b>Withdraw</b></p>
    <p><b>Profile</b></p>
    <button onclick="logout()">Logout</button>
  </div>

  <script>
    function showLogin() {
      document.getElementById('signupPage').style.display = 'none';
      document.getElementById('loginPage').style.display = 'block';
    }

    function showSignup() {
      document.getElementById('loginPage').style.display = 'none';
      document.getElementById('signupPage').style.display = 'block';
    }

    function signup() {
      let name = document.getElementById('signupName').value;
      let email = document.getElementById('signupEmail').value;
      let password = document.getElementById('signupPassword').value;
      if (name && email && password) {
        localStorage.setItem('user', JSON.stringify({ name, email, password }));
        alert('Account created successfully!');
        showLogin();
      } else {
        alert('Please fill all fields.');
      }
    }

    function login() {
      let email = document.getElementById('loginEmail').value;
      let password = document.getElementById('loginPassword').value;
      let user = JSON.parse(localStorage.getItem('user'));
      if (user && user.email === email && user.password === password) {
        document.getElementById('loginPage').style.display = 'none';
        document.getElementById('homePage').style.display = 'block';
      } else {
        alert('Invalid email or password.');
      }
    }

    function logout() {
      document.getElementById('homePage').style.display = 'none';
      document.getElementById('loginPage').style.display = 'block';
    }
  </script>
</body>
</html>
