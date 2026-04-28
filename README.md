<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Rapid Crisis Response System</title>

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #f9fdfb;
      color: #2c2c2c;
    }

    .header {
      background-color: #2e7d32;
      color: white;
      padding: 15px;
      text-align: center;
      font-size: 22px;
    }

    .container {
      max-width: 900px;
      margin: 30px auto;
      background: white;
      padding: 25px;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    }

    button {
      background-color: #66bb6a;
      color: white;
      border: none;
      padding: 12px;
      width: 100%;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background-color: #2e7d32;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 6px;
      margin-bottom: 15px;
      border: 1px solid #e0e0e0;
      border-radius: 5px;
    }

    .alert {
      padding: 12px;
      margin-top: 15px;
      border-radius: 5px;
      font-weight: bold;
    }

    .user-alert {
      background-color: #e8f5e9;
      color: #2e7d32;
    }

    .gov-alert {
      background-color: #fff3e0;
      color: #e65100;
    }

    iframe {
      width: 100%;
      height: 300px;
      border: 0;
      border-radius: 6px;
      margin-top: 15px;
    }

    .hidden {
      display: none;
    }
  </style>
</head>

<body>

<div class="header">Rapid Crisis Response System</div>

<!-- MAIN PAGE -->
<div class="container" id="mainPage">
  <h2>Select Login Type</h2>
  <button onclick="openCitizenLogin()">Login as Citizen</button>
  <button onclick="openGovLogin()">Login as Government Official</button>
</div>

<!-- CITIZEN LOGIN -->
<div class="container hidden" id="citizenLogin">
  <h2>Citizen Login</h2>
  <input type="email" placeholder="Email ID">
  <input type="password" placeholder="Password">
  <button onclick="openCitizenDashboard()">Login</button>
</div>

<!-- GOVERNMENT LOGIN -->
<div class="container hidden" id="govLogin">
  <h2>Government Official Login</h2>
  <input type="email" placeholder="Official Email ID">
  <input type="password" placeholder="Password">
  <button onclick="openGovDashboard()">Login</button>
</div>

<!-- CITIZEN DASHBOARD -->
<div class="container hidden" id="citizenDashboard">
  <h2>Citizen Crisis Dashboard</h2>

  <label>Crisis Type</label>
  <select id="crisisType">
    <option>Flood</option>
    <option>Earthquake</option>
    <option>Medical Emergency</option>
    <option>Fire Accident</option>
  </select>

  <label>Location</label>
  <input type="text" id="location" placeholder="Enter affected location">

  <label>Priority</label>
  <select id="priority">
    <option>High</option>
    <option>Medium</option>
    <option>Low</option>
  </select>

  <button onclick="submitCrisis()">Submit Crisis</button>

  <div class="alert user-alert hidden" id="userAlert">
    ✅ Your request has been submitted. Authorities have been notified.
  </div>

  <iframe id="userMap" src="https://www.google.com/maps?q=India&output=embed"></iframe>

  <button onclick="logout()">Logout</button>
</div>

<!-- GOVERNMENT DASHBOARD -->
<div class="container hidden" id="govDashboard">
  <h2>Government Monitoring Dashboard</h2>

  <div class="alert gov-alert">
    🚨 High-priority crisis alerts will appear here for immediate response.
  </div>

  <iframe src="https://www.google.com/maps?q=India&output=embed"></iframe>

  <button onclick="logout()">Logout</button>
</div>

<script>
  function hideAll() {
    document.querySelectorAll(".container").forEach(div => div.classList.add("hidden"));
  }

  function openCitizenLogin() {
    hideAll();
    document.getElementById("citizenLogin").classList.remove("hidden");
  }

  function openGovLogin() {
    hideAll();
    document.getElementById("govLogin").classList.remove("hidden");
  }

  function openCitizenDashboard() {
    hideAll();
    document.getElementById("citizenDashboard").classList.remove("hidden");
  }

  function openGovDashboard() {
    hideAll();
    document.getElementById("govDashboard").classList.remove("hidden");
  }

  function submitCrisis() {
    const location = document.getElementById("location").value;
    document.getElementById("userAlert").classList.remove("hidden");

    if (location !== "") {
      document.getElementById("userMap").src =
        "https://www.google.com/maps?q=" + location + "&output=embed";
    }
  }

  function logout() {
    hideAll();
    document.getElementById("mainPage").classList.remove("hidden");
  }
</script>

</body>
</html>
