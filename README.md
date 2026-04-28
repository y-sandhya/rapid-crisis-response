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
      max-width: 800px;
      margin: 40px auto;
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

    .result {
      background-color: #f1f8f4;
      border-left: 5px solid #2e7d32;
      padding: 15px;
      margin-top: 20px;
    }

    .hidden {
      display: none;
    }
  </style>
</head>

<body>

  <div class="header">
    Rapid Crisis Response System
  </div>

  <!-- LOGIN PAGE -->
  <div class="container" id="loginPage">
    <h2>Login</h2>
    <input type="email" placeholder="Email ID">
    <input type="password" placeholder="Password">
    <button onclick="login()">Login</button>
  </div>

  <!-- DASHBOARD -->
  <div class="container hidden" id="dashboard">
    <h2>Crisis Dashboard</h2>

    <label>Crisis Type</label>
    <select id="crisisType">
      <option>Flood</option>
      <option>Earthquake</option>
      <option>Medical Emergency</option>
      <option>Fire Accident</option>
    </select>

    <label>Location</label>
    <input type="text" id="location" placeholder="Enter affected location">

    <label>Available Resources</label>
    <input type="text" id="resources" placeholder="Food, Medical Kits, Rescue Teams">

    <label>Priority Level</label>
    <select id="priority">
      <option>High</option>
      <option>Medium</option>
      <option>Low</option>
    </select>

    <button onclick="generateResponse()">Generate AI Recommendation</button>

    <div class="result hidden" id="resultBox">
      <strong>AI Recommendation:</strong>
      <p id="resultText"></p>
    </div>
  </div>

  <script>
    function login() {
      document.getElementById("loginPage").classList.add("hidden");
      document.getElementById("dashboard").classList.remove("hidden");
    }

    function generateResponse() {
      const crisis = document.getElementById("crisisType").value;
      const priority = document.getElementById("priority").value;

      let recommendation = "";

      if (priority === "High") {
        recommendation = "Deploy emergency teams immediately. Allocate medical and rescue resources first.";
      } else if (priority === "Medium") {
        recommendation = "Allocate resources in phases. Monitor situation using AI-based analysis.";
      } else {
        recommendation = "Prepare resources and maintain surveillance using AI decision support.";
      }

      document.getElementById("resultText").innerText =
        crisis + " situation detected. " + recommendation +
        " (AI-powered decision simulated using Google Vertex AI / Gemini).";

      document.getElementById("resultBox").classList.remove("hidden");
    }
  </script>

</body>
</html>
