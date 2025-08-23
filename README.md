
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>ChatBot Simples</title>
  <style>
    body { font-family: Arial, sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; background: #f2f2f2; }
    .chat-container { width: 400px; background: white; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); display: flex; flex-direction: column; }
    .chat-box { flex: 1; padding: 10px; overflow-y: auto; border-bottom: 1px solid #ddd; }
    .chat-message { margin: 5px 0; }
    .user { text-align: right; color: blue; }
    .bot { text-align: left; color: green; }
    .input-box { display: flex; }
    input { flex: 1; padding: 10px; border: none; border-radius: 0 0 0 10px; outline: none; }
    button { padding: 10px; border: none; background: #007bff; color: white; cursor: pointer; border-radius: 0 0 10px 0; }
    button:hover { background: #0056b3; }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="chat-box" id="chatBox"></div>
    <div class="input-box">
      <input type="text" id="userInput" placeholder="Digite sua mensagem...">
      <button id="sendButton">Enviar</button>
    </div>
  </div>

  <script>
    function sendMessage() {
      let input = document.getElementById("userInput");
      let message = input.value.trim();
      if (message === "") return;

      addMessage("Você: " + message, "user");
      input.value = "";

      // Respostas simples do chatbot
      let resposta = "";
      let msg = message.toLowerCase();

      if (msg.includes("oi") || msg.includes("olá")) {
        resposta = "Olá! Chocoliudinha.";
      } else if (msg.includes("nome")) {
        resposta = "Eu sou um chatbot de demonstração 🤖";
      } else if (msg.includes("hora") || msg.includes("horas") || msg.includes("que horas são")) {
        const now = new Date();
        const options = { hour: '2-digit', minute: '2-digit' };
        resposta = `Agora são ${now.toLocaleTimeString('pt-BR', options)}.`;
      } else if (msg.includes("ajuda")) {
        resposta = "Posso responder 'oi', 'nome', 'ajuda' e 'que horas são'.";
      } else if (msg.includes("tchau")) {
        resposta = "Até logo! 👋";
      } else {
        resposta = "Desculpe, não entendi.";
      }

      setTimeout(() => addMessage("ChatBot: " + resposta, "bot"), 500);
    }

    function addMessage(text, sender) {
      let chatBox = document.getElementById("chatBox");
      let messageElement = document.createElement("div");
      messageElement.className = "chat-message " + sender;
      messageElement.innerText = text;
      chatBox.appendChild(messageElement);
      chatBox.scrollTop = chatBox.scrollHeight;
    }

    // Adicionamos um ID ao botão e um event listener no JavaScript
    document.getElementById("sendButton").addEventListener("click", sendMessage);
  </script>
</body>
</html>
