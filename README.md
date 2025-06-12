# chate-box
chate box
<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Chatbox</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #f0f0f0;
    display: flex;
    justify-content: center;
    padding: 20px;
  }
  #chatbox {
    width: 400px;
    height: 500px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    display: flex;
    flex-direction: column;
  }
  #messages {
    flex: 1;
    padding: 10px;
    overflow-y: auto;
    border-bottom: 1px solid #ddd;
  }
  .message {
    margin: 5px 0;
  }
  .user {
    text-align: right;
    color: blue;
  }
  .bot {
    text-align: left;
    color: green;
  }
  #input-area {
    display: flex;
    padding: 10px;
  }
  #input-area input[type="text"] {
    flex: 1;
    padding: 10px;
    font-size: 16px;
  }
  #input-area button {
    padding: 10px 20px;
    font-size: 16px;
    margin-left: 5px;
    cursor: pointer;
  }
</style>
</head>
<body>

<div id="chatbox">
  <div id="messages"></div>
  <div id="input-area">
    <input type="text" id="message-input" placeholder="Typ je bericht..." />
    <button id="send-btn">Verstuur</button>
  </div>
</div>

<script>
  const messages = document.getElementById('messages');
  const input = document.getElementById('message-input');
  const sendBtn = document.getElementById('send-btn');

  function addMessage(text, sender) {
    const msgDiv = document.createElement('div');
    msgDiv.classList.add('message', sender);
    msgDiv.textContent = text;
    messages.appendChild(msgDiv);
    messages.scrollTop = messages.scrollHeight; // scroll naar beneden
  }

  sendBtn.addEventListener('click', () => {
    const text = input.value.trim();
    if (text === '') return;
    addMessage(text, 'user');
    input.value = '';

    // Simpele bot-reactie
    setTimeout(() => {
      addMessage('Je zei: ' + text, 'bot');
    }, 500);
  });

  input.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      sendBtn.click();
    }
  });
</script>

</body>
</html>
