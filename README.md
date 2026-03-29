<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title> Aplicação WebSocket com JavaScript</title>
</head>
<body>

  <h1>📡 Aplicação Simples com WebSocket (JavaScript + HTML)</h1>

  <p>
    Este projeto demonstra uma aplicação simples utilizando <strong>WebSocket</strong> com 
    <strong>JavaScript puro</strong> e <strong>HTML</strong>, permitindo comunicação em tempo real entre cliente e servidor.
  </p>

  <hr>

  <h2>📌 Objetivo</h2>
  <p>
    Criar uma aplicação básica que:
  </p>
  <ul>
    <li>Estabelece conexão com um servidor WebSocket</li>
    <li>Envia mensagens do cliente para o servidor</li>
    <li>Recebe mensagens do servidor em tempo real</li>
    <li>Exibe logs de comunicação na tela</li>
  </ul>

  <hr>

  <h2>🛠️ Tecnologias Utilizadas</h2>
  <ul>
    <li>HTML5</li>
    <li>JavaScript (Vanilla JS)</li>
    <li>WebSocket API</li>
  </ul>

  <hr>

  <h2>📁 Estrutura do Projeto</h2>
  <pre>
project/
│
├── index.html
├── script.js
└── README.html
  </pre>

  <hr>

  <h2>🚀 Como Executar</h2>
  <ol>
    <li>Clone o repositório</li>
    <li>Abra o arquivo <code>index.html</code> no navegador</li>
    <li>Certifique-se de que um servidor WebSocket está rodando</li>
  </ol>

  <p><strong>Exemplo de servidor local:</strong></p>
  <pre>
ws://localhost:8080
  </pre>

  <hr>

  <h2>💻 Exemplo de Código</h2>

  <h3>HTML (index.html)</h3>
  <pre>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
  &lt;title&gt;WebSocket Demo&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;

  &lt;h1&gt;WebSocket Cliente&lt;/h1&gt;

  &lt;input type="text" id="input" placeholder="Digite uma mensagem"&gt;
  &lt;button onclick="sendMessage()"&gt;Enviar&lt;/button&gt;

  &lt;ul id="messages"&gt;&lt;/ul&gt;

  &lt;script src="script.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
  </pre>

  <h3>JavaScript (script.js)</h3>
  <pre>
const socket = new WebSocket("ws://localhost:8080");

const messages = document.getElementById("messages");

socket.onopen = () =&gt; {
  console.log("Conectado ao servidor");
};

socket.onmessage = (event) =&gt; {
  const li = document.createElement("li");
  li.textContent = "Servidor: " + event.data;
  messages.appendChild(li);
};

socket.onclose = () =&gt; {
  console.log("Conexão encerrada");
};

function sendMessage() {
  const input = document.getElementById("input");
  socket.send(input.value);

  const li = document.createElement("li");
  li.textContent = "Você: " + input.value;
  messages.appendChild(li);

  input.value = "";
}
  </pre>

  <hr>

  <h2>🔄 Fluxo da Aplicação</h2>
  <ol>
    <li>Cliente abre conexão com o servidor WebSocket</li>
    <li>Servidor aceita a conexão (handshake)</li>
    <li>Cliente envia mensagens</li>
    <li>Servidor responde em tempo real</li>
    <li>Mensagens são exibidas na interface</li>
  </ol>

  <hr>

  <h2>⚠️ Observações</h2>
  <ul>
    <li>WebSocket utiliza protocolo <code>ws://</code> ou <code>wss://</code></li>
    <li>Necessário backend ativo para comunicação real</li>
    <li>Pode ser expandido para chats, notificações e sistemas em tempo real</li>
  </ul>

  <hr>

  <h2>📚 Possíveis Melhorias</h2>
  <ul>
    <li>Adicionar autenticação</li>
    <li>Persistência de mensagens</li>
    <li>Interface mais avançada (React, Vue)</li>
    <li>Uso de WebSocket seguro (WSS)</li>
  </ul>

  <hr>

  <h2>👨‍💻 Autor</h2>
  <p>
    Desenvolvido para fins de estudo e prática com comunicação em tempo real usando WebSocket.
  </p>

</body>
</html>
