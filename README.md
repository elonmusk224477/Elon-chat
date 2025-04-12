<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Red & Black Chat</title>
    <style>
        body {
            background-color: #1a1a1a;
            color: #ff0000;
            font-family: Arial, sans-serif;
            margin: 0;
            display: flex;
            justify-content: center;
            height: 100vh;
        }
        .chat-container {
            width: 100%;
            max-width: 400px;
            background-color: #000;
            border: 2px solid #ff0000;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            height: 80vh;
            margin: 20px;
        }
        .chat-box {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            border-bottom: 1px solid #ff0000;
        }
        .message {
            margin: 5px 0;
            padding: 8px;
            background-color: #1a1a1a;
            border-radius: 5px;
            color: #ff0000;
        }
        .input-container {
            display: flex;
            padding: 10px;
        }
        input[type="text"] {
            flex: 1;
            padding: 8px;
            background-color: #1a1a1a;
            border: 1px solid #ff0000;
            color: #ff0000;
            border-radius: 5px 0 0 5px;
            outline: none;
        }
        button {
            padding: 8px;
            background-color: #ff0000;
            border: none;
            color: #000;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
        }
        button:hover {
            background-color: #cc0000;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-box" id="chatBox"></div>
        <div class="input-container">
            <input type="text" id="messageInput" placeholder="Type a message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            const input = document.getElementById('messageInput');
            const chatBox = document.getElementById('chatBox');
            const messageText = input.value.trim();

            if (messageText !== '') {
                const message = document.createElement('div');
                message.className = 'message';
                message.textContent = messageText;
                chatBox.appendChild(message);
                input.value = '';
                chatBox.scrollTop = chatBox.scrollHeight; // Auto-scroll to bottom
            }
        }

        // Allow sending message with Enter key
        document.getElementById('messageInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
    </script>
</body>
</html>
