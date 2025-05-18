<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Mein ChatBot</title>
  <style>
    body { font-family: Arial; background: #f0f0f0; padding: 20px; }
    #chatbox { width: 400px; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px #ccc; }
    .message { margin: 10px 0; }
    .bot { color: blue; }
    .user { color: green; }
    input[type="text"] { width: 100%; padding: 10px; margin-top: 10px; }
  </style>
</head>
<body>

<div id="chatbox">
  <div id="messages"></div>
  <input type="text" id="input" placeholder="Schreibe hier..." onkeydown="if(event.key === 'Enter') sendMessage()">
</div>

<script>
function sendMessage() {
  const input = document.getElementById("input");
  const text = input.value.trim();
  if (!text) return;

  addMessage("user", text);
  input.value = "";

  const response = getBotResponse(text.toLowerCase());
  setTimeout(() => addMessage("bot", response), 400);
}

function addMessage(sender, text) {
  const msg = document.createElement("div");
  msg.className = `message ${sender}`;
  msg.textContent = (sender === "user" ? "Du: " : "Bot: ") + text;
  document.getElementById("messages").appendChild(msg);
}

function getBotResponse(input) {
  if (input.includes("hallo") || input.includes("hi")) return "Hallo! Wie kann ich dir weiterhelfen?";
  if (input.includes("öffnungszeiten")) return "Wir haben Montag bis Freitag von 9:00 bis 18:00 Uhr geöffnet.";
  if (input.includes("kontakt") || input.includes("telefon")) return "Du erreichst uns unter kontakt@beispiel.de oder 0123-456789.";
  if (input.includes("produkt")) return "Wir bieten viele Produkte an. Möchtest du etwas Bestimmtes wissen?";
  if (input.includes("preis")) return "Unsere Preise variieren je nach Produkt. Was interessiert dich genau?";
  if (input.includes("adresse") || input.includes("wo finde ich euch") || input.includes("standort")) return "Unsere Adresse ist Musterstraße 1, 12345 Musterstadt.";
  if (input.includes("danke") || input.includes("tschüss")) return "Gern geschehen! Hab einen schönen Tag!";
  return "Das habe ich leider nicht verstanden. Bitte frag etwas anderes.";
}
</script>

</body>
</html>
