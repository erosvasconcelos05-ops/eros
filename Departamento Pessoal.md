
function sendMessage() {
  let input = document.getElementById("userInput");
  let message = input.value.trim();
  if (message === "") return;

  addMessage("Você: " + message, "user");
  input.value = "";

  let resposta = "";
  let msg = message.toLowerCase();

  if (msg.includes("olá") || msg.includes("oi") || msg.includes("boa tarde") || msg.includes("bom dia")) {
    resposta = "Olá! Como posso te ajudar hoje? Posso dar informações sobre **auxílio-saúde** ou o **plano UNIMED/HAPVIDA**.";
  } else if (msg.includes("auxílio-saúde") || msg.includes("auxilio saude") || msg.includes("reembolso")) {
    resposta = "Para qual assunto sobre o auxílio-saúde você precisa de ajuda? **Elegibilidade** ou **Prazos e Procedimentos**?";
  } else if (msg.includes("elegibilidade") || msg.includes("quem tem direito")) {
    if (msg.includes("mensalista") || msg.includes("horista")) {
      resposta = "Para **Mensalistas** e **Horistas**: titulares e dependentes (cônjuge, companheiro(a), filhos e enteados) têm direito. Filhos entre 21 e 24 anos devem comprovar vínculo universitário.";
    } else if (msg.includes("instrutor") || msg.includes("professor")) {
      resposta = "Para **Instrutores** e **Professores Horistas**: somente o titular tem direito ao auxílio. Dependentes não são elegíveis.";
    } else {
      resposta = "Você é Mensalista/Horista ou Instrutor/Professor Horista? Para que eu possa te dar a informação correta.";
    }
  } else if (msg.includes("prazo") || msg.includes("procedimento") || msg.includes("como solicitar")) {
    resposta = "Você pode solicitar o benefício a partir do **primeiro mês de admissão**, após **15 dias de trabalho**. A requisição de reembolso é feita pelo **Portal RM** entre os dias **1 e 15** de cada mês. É preciso anexar o boleto, o comprovante de pagamento e o demonstrativo dos beneficiários.";
  } else if (msg.includes("plano unimed") || msg.includes("plano hapvida") || msg.includes("adesão") || msg.includes("contratar plano")) {
    resposta = "Para aderir ao plano UNIMED/HAPVIDA, entre em contato com a **Fecomercio** pelos números: **(85) 98728-8314** ou **(85) 98883-4292**.";
  } else if (msg.includes("obrigado") || msg.includes("obrigada") || msg.includes("valeu")) {
    resposta = "De nada! Se tiver mais alguma dúvida, é só perguntar.";
  } else if (msg.includes("tchau") || msg.includes("até logo") || msg.includes("fui")) {
    resposta = "Até logo! Se precisar de algo, estarei aqui para ajudar.";
  } else {
    resposta = "Desculpe, não entendi. Por favor, reformule sua pergunta.";
  }

  setTimeout(() => addMessage("ChatBot: " + resposta, "bot"), 500);
}

function addMessage(text, sender) {
  let chatBox = document.getElementById("chatBox");
  let messageElement = document.createElement("div");
  messageElement.className = "chat-message " + sender;
  messageElement.innerHTML = text; // Use innerHTML para formatar o texto com negrito
  chatBox.appendChild(messageElement);
  chatBox.scrollTop = chatBox.scrollHeight;
}

document.getElementById("sendButton").addEventListener("click", sendMessage);
document.getElementById("userInput").addEventListener("keypress", function(event) {
    if (event.key === "Enter") {
        sendMessage();
    }
});
</body>
</html>
