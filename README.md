<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vessel Tank Temperature & Humidity from E&I</title>
  <style>
    body { font-family: 'Arial', sans-serif; text-align: center; padding: 20px; }
    h1 { color: #333; }
    .data { font-size: 24px; margin: 10px 0; }
    .error { color: red; }
  </style>
</head>
<body>
  <h1>Vessel Tank Temperature & Humidity from E&I</h1>
  <div class="data">Temperature: <span id="temperature">--</span> °C</div>
  <div class="data">Humidity: <span id="humidity">--</span> %</div>
  <div class="error" id="error"></div>

  <script>
    async function fetchData() {
      try {
        const response = await fetch('http://YOUR_ESP32_IP_ADDRESS');  // Replace with your ESP32 IP
        const data = await response.json();
        document.getElementById('temperature').textContent = data.temperature.toFixed(2);
        document.getElementById('humidity').textContent = data.humidity.toFixed(2);
        document.getElementById('error').textContent = '';
      } catch (error) {
        document.getElementById('error').textContent = 'Failed to fetch data. Please check your ESP32.';
      }
    }
    setInterval(fetchData, 5000); // Fetch data every 5 seconds
    fetchData(); // Initial call
  </script>
</body>
</html># Tank-Sensor
