# Emotional-Pliot
my emotional pilot with using aviation charts
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Flight in Progress</title>
  <style>
    body {
      font-family: 'Orbitron', sans-serif;
      background-color: #0e1117;
      color: #f5f5f5;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    h1 {
      margin-top: 2rem;
      font-size: 1.8rem;
      text-align: center;
    }
    .emotion-buttons {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: 2rem 1rem;
      gap: 1rem;
    }
    button {
      background-color: #1e2633;
      color: white;
      border: none;
      padding: 0.8rem 1.2rem;
      border-radius: 10px;
      font-size: 1rem;
      cursor: pointer;
    }
    .ticket {
      margin-top: 1rem;
      padding: 1.5rem;
      border: 2px solid #f5f5f5;
      border-radius: 10px;
      max-width: 300px;
      text-align: left;
      background-color: #1e2633;
    }
    .logbook {
      margin-top: 2rem;
      width: 90%;
    }
    .log-entry {
      border-bottom: 1px solid #444;
      padding: 1rem 0;
    }
  </style>
</head>
<body>
  <h1>How high did your feelings fly today?</h1>

  <div class="emotion-buttons">
    <button onclick="generateTicket('Grateful')">🙏 Grateful</button>
    <button onclick="generateTicket('Nostalgic')">🎵 Nostalgic</button>
    <button onclick="generateTicket('Out of Place')">⚠️ Out of Place</button>
    <button onclick="generateTicket('Excited')">✈️ Excited</button>
    <button onclick="generateTicket('Calm')">🌙 Calm</button>
  </div>

  <div class="ticket" id="ticket" style="display: none;"></div>

  <div class="logbook" id="logbook">
    <h2>Emotion Logbook</h2>
    <div id="log"></div>
  </div>

  <script>
    const ticketDiv = document.getElementById('ticket');
    const logDiv = document.getElementById('log');

    function generateTicket(emotion) {
      const altitude = Math.floor(Math.random() * 20000) + 2000;
      const latitude = (Math.random() * 180 - 90).toFixed(2);
      const longitude = (Math.random() * 360 - 180).toFixed(2);
      const notam = `Feeling recorded: ${emotion}`;
      const date = new Date().toLocaleString();

      ticketDiv.style.display = 'block';
      ticketDiv.innerHTML = `
        <strong>Emotion:</strong> ${emotion}<br>
        <strong>Altitude:</strong> ${altitude} FT<br>
        <strong>Coordinates:</strong> ${latitude}°, ${longitude}°<br>
        <strong>NOTAM:</strong> ${notam}<br>
        <strong>Time:</strong> ${date}<br>
      `;

      const logEntry = document.createElement('div');
      logEntry.className = 'log-entry';
      logEntry.innerHTML = `<strong>${emotion}</strong> – ${altitude} FT – ${latitude}°, ${longitude}°<br><em>${notam}</em><br><small>${date}</small>`;
      logDiv.prepend(logEntry);
    }
  </script>
</body>
</html>
