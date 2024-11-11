<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>High-Tech Chatbot</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(to right, #1e3c72, #2a5298);
            color: #fff;
        }
        .chat-container {
            width: 450px;
            height: 600px;
            background: #1e1e1e;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            animation: slideIn 1s;
        }
        .chat-header, .chat-footer {
            padding: 20px;
            background: #2e2e2e;
            text-align: center;
        }
        .chat-header {
            font-size: 24px;
            border-bottom: 1px solid #444;
        }
        .chat-body {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            background: #1e1e1e;
            animation: fadeIn 1s;
        }
        .message {
            margin-bottom: 15px;
            padding: 10px;
            border-radius: 10px;
            max-width: 75%;
            animation: fadeInUp 1s;
        }
        .message.user {
            background: #007bff;
            align-self: flex-end;
            border: 1px solid #0056b3;
        }
        .message.bot {
            background: #333;
            align-self: flex-start;
            border: 1px solid #444;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-100%);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        input[type="text"] {
            width: calc(100% - 40px);
            padding: 15px;
            border: none;
            border-radius: 5px;
            background: #2e2e2e;
            color: #fff;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">High-Tech Chatbot</div>
        <div class="chat-body" id="chat-body">
            <div class="message bot">Hello! How can I help you today?</div>
        </div>
        <div class="chat-footer">
            <input type="text" id="user-input" placeholder="Type your message here..." onkeypress="sendMessage(event)">
        </div>
    </div>

    <script>
        function sendMessage(event) {
            if (event.key === "Enter") {
                const userInput = document.getElementById("user-input");
                if (userInput.value.trim() !== "") {
                    const chatBody = document.getElementById("chat-body");
                    const userMessage = document.createElement("div");
                    userMessage.className = "message user";
                    userMessage.textContent = userInput.value;
                    chatBody.appendChild(userMessage);

                    const botMessage = document.createElement("div");
                    botMessage.className = "message bot";
                    botMessage.textContent = "You said: " + userInput.value;
                    chatBody.appendChild(botMessage);

                    chatBody.scrollTop = chatBody.scrollHeight;
                    userInput.value = "";
                }
            }
        }
    </script>
</body>
</html>
