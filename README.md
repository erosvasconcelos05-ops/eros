<script>
function sendMessage() {
  let input = document.getElementById("userInput").value;
  if (input.trim() === "") return;

  addMessage("Você: " + input, "user");
  document.getElementById("userInput").value = "";

  // 🔹 Envia a pergunta para o n8n
  fetch("https://SEU-ENDERECO-N8N/webhook/auxilio-saude", {
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
