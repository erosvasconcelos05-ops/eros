<script>
function sendMessage() {
  let input = document.getElementById("userInput").value;
  if (input.trim() === "") return;

  addMessage("Você: " + input, "user");
  document.getElementById("userInput").value = "";

  // 🔹 Envia a pergunta para o n8n
  fetch("https://eros05.app.n8n.cloud/webhook-test/auxilio-saude", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ pergunta: input })
  })
  .then(response => response.json())
  .then(data => {
    addMessage("ChatBot: " + data.resposta, "bot");
  })
  .catch(error => {
    addMessage("ChatBot: Ocorreu um erro ao buscar resposta.", "bot");
  });
}
</script>
