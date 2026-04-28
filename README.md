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

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 6px;
      margin-bottom: 15px;
      border: 1px solid #e0e0e0;
      border-radius: 5px;
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
    }

    button:hover {
      background-color: #2e7d32;
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

    .hidden {
      display: none;
    }

    iframe {
      width: 100%;
      height: 300px;
      border: 0;
      margin-top: 15px;
      border-radius: 6px;
    }
  </style>
</head>

<body>

<div class="header">
  Rapid Crisis Response System
</div>

<!-- LOGIN -->
<div class="container" id="loginPage">
  <h2>Login</h2>
  <input type="email" placeholder="Email ID">
  <input type="password" placeholder="Password">
  <button onclick="login()">Login</button>
</div>

<!-- DASHBOARD -->
<div class="container hidden" id="dashboard">
  <h2>Crisis Reporting Dashboard</h2>

  <label>Crisis Type</label>
  <select id="crisisType">
    <option>Flood</option>
    <option>Earthquake</option>
    <option>Medical Emergency</option>
    <option>Fire Accident</option>
  </select>

  <label>Location (City / Area)</label>
  <input type="text" id="location" placeholder="Enter affected location">

  <label>People Affected</label>
  <input type="number" placeholder="Approximate number of people">

  <label>Priority Level</label>
  <select id="priority">
    <option>High</option>
    <option>Medium</option>
    <option>Low</option>
  </select>

  <button onclick="submitCrisis()">Submit Crisis Request</button>

  <!-- ALERTS -->
  <div class="alert user-alert hidden" id="userAlert">
    ✅ Your crisis request has been submitted. Help is on the way.
  </div>

  <div class="alert gov-alert hidden" id="govAlert">
    🚨 Government Alert: High priority crisis detected. Immediate action required.
  </div>

  <!-- MAP -->
  <h3>Live Location Tracking</h3>
  <iframe
    id="map"
    src="https://www.google.com/maps?q=India&output=embed">
  </iframe>
</div>

<script>
  function login() {
    document.getElementById("loginPage").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
  }

  function submitCrisis() {
    const location = document.getElementById("location").value;
    const priority = document.getElementById("priority").value;

    // Show alerts
    document.getElementById("userAlert").classList.remove("hidden");

    if (priority === "High") {
      document.getElementById("govAlert").classList.remove("hidden");
    }

    // Update map location
    if (location !== "") {
      document.getElementById("map").src =
        "https://www.google.com/maps?q=" + location + "&output=embed";
    }
  }
</script>

</body>
</html>
