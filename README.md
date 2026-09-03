<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Portal</title>
    <style>
        :root {
            --primary: #4f46e5;
            --primary-hover: #4338ca;
            --bg-color: #1e293b;
            --card-bg: #334155;
            --text-color: #f8fafc;
            --error-color: #ef4444;
            --success-color: #22c55e;
        }
    body {
            font-family: Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

 .container {
            width: 100%;
            max-width: 400px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
        }
        h2 {
            margin-top: 0;
            color: #fbbf24;
            text-align: center;
        }

  .form-group {
            margin-bottom: 15px;
        }

  label {
        display: block;
            margin-bottom: 6px;
            font-weight: bold;
            font-size: 14px;
        }

  input {
          width: 100%;
            padding: 10px;
            box-sizing: border-box;
            border: 1px solid #475569;
            background: #1e293b;
            color: white;
            border-radius: 6px;
            font-size: 14px;
        }

 button {
            width: 100%;
            padding: 10px;
            background-color: var(--primary);
            border: none;
            color: white;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
            margin-top: 5px;
        }

  button:hover {
            background-color: var(--primary-hover);
        }

  .error-msg {
            color: var(--error-color);
            font-size: 13px;
            text-align: center;
            margin-bottom: 12px;
        }

.switch-text {
            text-align: center;
            margin-top: 20px;
            font-size: 14px;
            color: #cbd5e1;
        }

  .switch-text a {
            color: #fbbf24;
            text-decoration: none;
            font-weight: bold;
        }
    </style>
</head>
<body>
 <div class="container">
        <h2>Login Portal</h2>
        <div id="loginError" class="error-msg"></div>
        
  <form onsubmit="handleLogin(event)">
            <div class="form-group">
                <label for="loginUser">Username</label>
                <input type="text" id="loginUser" required>
            </div>
            <div class="form-group">
                <label for="loginPass">Password</label>
                <input type="password" id="loginPass" required>
            </div>
            <button type="submit">Login</button>
        </form>

 <div class="switch-text">
            Don't have an account? <a href="register.html">Register here</a>
        </div>
    </div>

 <script>
        function handleLogin(event) {
            event.preventDefault();
            const username = document.getElementById("loginUser").value.trim();
            const password = document.getElementById("loginPass").value;
            
            let db = JSON.parse(localStorage.getItem("app_users_db")) || {};

            if (db[username] && db[username].password === password) {
                // Save active user session
                localStorage.setItem("activeUser", username);
                
                // Redirect straight to your summary/analytics dashboard page (change filename if yours is named differently)
                window.location.href = "summary.html";
            } else {
                document.getElementById("loginError").textContent = "Invalid username or password.";
            }
        }
    </script>
</body>
</html>
