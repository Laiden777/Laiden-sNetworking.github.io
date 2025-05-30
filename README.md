<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Networking Academy - Virtual AI Classroom</title>
    <style>
        :root {
            --primary: #3a86ff;
            --primary-dark: #2667cc;
            --secondary: #ff006e;
            --dark: #212529;
            --light: #f8f9fa;
            --gray: #6c757d;
            --success: #38b000;
            --warning: #ffbe0b;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fb;
            color: var(--dark);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }
        
        .logo {
            display: flex;
            align-items: center;
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .logo svg {
            margin-right: 0.5rem;
        }
        
        .nav-links {
            display: flex;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            padding: 0.5rem 1rem;
            margin-left: 0.5rem;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        
        .nav-links a:hover {
            background-color: var(--primary-dark);
        }
        
        .nav-links a.active {
            background-color: var(--primary-dark);
        }
        
        main {
            flex: 1;
            max-width: 1200px;
            width: 100%;
            margin: 0 auto;
            padding: 2rem 1rem;
        }
        
        .container {
            display: flex;
            gap: 2rem;
            height: calc(100vh - 160px);
        }
        
        .sidebar {
            width: 250px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            padding: 1.5rem;
            height: 100%;
            overflow-y: auto;
        }
        
        .sidebar h3 {
            margin-bottom: 1rem;
            color: var(--dark);
            font-size: 1.2rem;
        }
        
        .topics {
            list-style: none;
        }
        
        .topics .topic {
            padding: 0.75rem;
            margin-bottom: 0.5rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
            border-left: 3px solid transparent;
        }
        
        .topics .topic:hover {
            background-color: #f0f4ff;
            border-left-color: var(--primary);
        }
        
        .topics .topic.active {
            background-color: #ebf2ff;
            border-left-color: var(--primary);
            font-weight: 500;
        }
        
        .content {
            flex: 1;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            height: 100%;
        }
        
        .content-header {
            padding: 1.5rem;
            border-bottom: 1px solid #eaeaea;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .content-header h2 {
            font-size: 1.5rem;
            color: var(--dark);
        }
        
        .tab-buttons {
            display: flex;
            gap: 0.5rem;
        }
        
        .tab-button {
            padding: 0.5rem 1rem;
            background-color: #f0f4ff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            color: var(--primary);
            transition: background-color 0.3s;
        }
        
        .tab-button:hover {
            background-color: #e0eaff;
        }
        
        .tab-button.active {
            background-color: var(--primary);
            color: white;
        }
        
        .content-body {
            padding: 1.5rem;
            flex: 1;
            overflow-y: auto;
        }
        
        /* Different tabs */
        .tab-content {
            display: none;
            height: 100%;
        }
        
        .tab-content.active {
            display: block;
            height: 100%;
        }
        
        /* Learn tab */
        .ai-teacher {
            display: flex;
            flex-direction: column;
            height: 100%;
        }
        
        .lesson-content {
            flex: 1;
            overflow-y: auto;
            margin-bottom: 1rem;
            padding: 1rem;
            background-color: #f8f9fa;
            border-radius: 8px;
        }
        
        .lesson-content h3 {
            margin-bottom: 1rem;
        }
        
        .lesson-content p {
            margin-bottom: 1rem;
            line-height: 1.6;
        }
        
        .lesson-content ul, .lesson-content ol {
            margin-left: 1.5rem;
            margin-bottom: 1rem;
        }
        
        .lesson-content li {
            margin-bottom: 0.5rem;
        }
        
        .chat-interface {
            display: flex;
            flex-direction: column;
            height: 200px;
            border: 1px solid #eaeaea;
            border-radius: 8px;
        }
        
        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 1rem;
        }
        
        .message {
            margin-bottom: 1rem;
            padding: 0.75rem;
            border-radius: 8px;
            max-width: 80%;
        }
        
        .user-message {
            background-color: #e0eaff;
            color: var(--dark);
            align-self: flex-end;
            margin-left: auto;
        }
        
        .ai-message {
            background-color: #f0f4ff;
            color: var(--dark);
        }
        
        .chat-input {
            display: flex;
            border-top: 1px solid #eaeaea;
            padding: 0.75rem;
        }
        
        .chat-input input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid #eaeaea;
            border-radius: 4px;
            margin-right: 0.5rem;
        }
        
        .chat-input button {
            padding: 0.75rem 1.5rem;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
        }
        
        .chat-input button:hover {
            background-color: var(--primary-dark);
        }
        
        /* Quiz tab */
        .quiz-container {
            height: 100%;
            overflow-y: auto;
        }
        
        .question {
            margin-bottom: 2rem;
        }
        
        .question h3 {
            margin-bottom: 0.5rem;
        }
        
        .options {
            list-style: none;
        }
        
        .option {
            padding: 1rem;
            margin-bottom: 0.5rem;
            border: 1px solid #eaeaea;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .option:hover {
            background-color: #f0f4ff;
        }
        
        .option.selected {
            background-color: #ebf2ff;
            border-color: var(--primary);
        }
        
        .option.correct {
            background-color: #d8f3dc;
            border-color: var(--success);
        }
        
        .option.incorrect {
            background-color: #ffd7e1;
            border-color: var(--secondary);
        }
        
        .quiz-buttons {
            margin-top: 2rem;
            display: flex;
            justify-content: space-between;
        }
        
        .submit-quiz, .next-question, .restart-quiz {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            color: white;
        }
        
        .submit-quiz {
            background-color: var(--success);
        }
        
        .next-question {
            background-color: var(--primary);
        }
        
        .restart-quiz {
            background-color: var(--warning);
            color: var(--dark);
        }
        
        .quiz-result {
            text-align: center;
            margin-top: 2rem;
            padding: 2rem;
            background-color: #f0f4ff;
            border-radius: 8px;
        }
        
        .quiz-result h3 {
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }
        
        /* Notes tab */
        .notes-container {
            height: 100%;
            display: flex;
            flex-direction: column;
        }
        
        .notes-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1rem;
        }
        
        .notes-list {
            flex: 1;
            overflow-y: auto;
            margin-bottom: 1rem;
        }
        
        .note {
            padding: 1rem;
            margin-bottom: 0.5rem;
            background-color: #f8f9fa;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .note:hover {
            background-color: #f0f4ff;
        }
        
        .note.selected {
            background-color: #ebf2ff;
            border-left: 3px solid var(--primary);
        }
        
        .note-title {
            font-weight: 500;
            margin-bottom: 0.5rem;
        }
        
        .note-preview {
            color: var(--gray);
            font-size: 0.9rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .note-editor {
            display: flex;
            flex-direction: column;
            height: 300px;
            border: 1px solid #eaeaea;
            border-radius: 8px;
            overflow: hidden;
        }
        
        .note-editor-header {
            display: flex;
            padding: 0.75rem;
            border-bottom: 1px solid #eaeaea;
        }
        
        .note-editor-header input {
            flex: 1;
            padding: 0.5rem;
            border: 1px solid #eaeaea;
            border-radius: 4px;
        }
        
        .note-editor-body {
            flex: 1;
            padding: 0.75rem;
        }
        
        .note-editor-body textarea {
            width: 100%;
            height: 100%;
            padding: 0.5rem;
            border: 1px solid #eaeaea;
            border-radius: 4px;
            resize: none;
        }
        
        .note-editor-footer {
            display: flex;
            justify-content: flex-end;
            padding: 0.75rem;
            border-top: 1px solid #eaeaea;
        }
        
        .save-note, .new-note, .delete-note {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 0.5rem;
            font-weight: 500;
        }
        
        .save-note {
            background-color: var(--success);
            color: white;
        }
        
        .new-note {
            background-color: var(--primary);
            color: white;
        }
        
        .delete-note {
            background-color: var(--secondary);
            color: white;
        }
        
        footer {
            text-align: center;
            padding: 1rem;
            background-color: var(--dark);
            color: var(--light);
            margin-top: auto;
        }
        
        /* Responsive design */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
                height: auto;
            }
            
            .sidebar {
                width: 100%;
                margin-bottom: 1rem;
            }
            
            .content {
                height: auto;
                min-height: 500px;
            }
            
            .chat-interface {
                height: 300px;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <rect x="2" y="2" width="20" height="8" rx="2" ry="2"></rect>
                    <rect x="2" y="14" width="20" height="8" rx="2" ry="2"></rect>
                    <line x1="6" y1="6" x2="6.01" y2="6"></line>
                    <line x1="6" y1="18" x2="6.01" y2="18"></line>
                </svg>
                Networking Academy
            </div>
            <div class="nav-links">
                <a href="#" class="active">Classroom</a>
                <a href="#">Resources</a>
                <a href="#">About</a>
            </div>
        </nav>
    </header>
    
    <main>
        <div class="container">
            <div class="sidebar">
                <h3>Networking Topics</h3>
                <ul class="topics">
                    <li class="topic active" data-topic="network-fundamentals">Network Fundamentals</li>
                    <li class="topic" data-topic="osi-model">OSI Model</li>
                    <li class="topic" data-topic="tcp-ip">TCP/IP Protocol Suite</li>
                    <li class="topic" data-topic="ip-addressing">IP Addressing & Subnetting</li>
                    <li class="topic" data-topic="routing">Routing Protocols</li>
                    <li class="topic" data-topic="switching">Switching & VLANs</li>
                    <li class="topic" data-topic="wireless">Wireless Networking</li>
                    <li class="topic" data-topic="network-security">Network Security</li>
                    <li class="topic" data-topic="cloud-networking">Cloud Networking</li>
                    <li class="topic" data-topic="sdn">Software-Defined Networking</li>
                </ul>
            </div>
            
            <div class="content">
                <div class="content-header">
                    <h2 id="topic-title">Network Fundamentals</h2>
                    <div class="tab-buttons">
                        <button class="tab-button active" data-tab="learn">Learn</button>
                        <button class="tab-button" data-tab="quiz">Quiz</button>
                        <button class="tab-button" data-tab="notes">Notes</button>
                    </div>
                </div>
                
                <div class="content-body">
                    <!-- Learn Tab -->
                    <div class="tab-content active" id="learn">
                        <div class="ai-teacher">
                            <div class="lesson-content" id="lesson-content">
                                <h3>Introduction to Network Fundamentals</h3>
                                <p>Welcome to the Network Fundamentals module! This is your introduction to the world of computer networking.</p>
                                <p>A computer network is a collection of interconnected devices that can communicate and share resources with each other. These networks form the backbone of modern information systems and enable everything from simple file sharing to complex global communications.</p>
                                <h4>Key Concepts:</h4>
                                <ul>
                                    <li><strong>Network Types:</strong> LANs, WANs, MANs, PANs, etc.</li>
                                    <li><strong>Network Topologies:</strong> Star, Bus, Ring, Mesh, and Hybrid</li>
                                    <li><strong>Network Devices:</strong> Routers, Switches, Hubs, Bridges, etc.</li>
                                    <li><strong>Data Transmission:</strong> Bandwidth, Latency, Throughput</li>
                                </ul>
                                <p>Feel free to ask any questions about these topics in the chat below!</p>
                            </div>
                            
                            <div class="chat-interface">
                                <div class="chat-messages" id="chat-messages">
                                    <div class="message ai-message">
                                        Hello! I'm your AI networking instructor. What questions do you have about Network Fundamentals?
                                    </div>
                                    <div class="message user-message">
                                        What's the difference between a router and a switch?
                                    </div>
                                    <div class="message ai-message">
                                        Great question! A switch operates at Layer 2 (Data Link Layer) of the OSI model and forwards data based on MAC addresses within a local network. It creates a direct connection between communicating devices in the same network.

                                        A router operates at Layer 3 (Network Layer) and forwards data based on IP addresses. Routers connect different networks together and determine the best path for data to travel between networks. They're essential for internet connectivity and more complex network configurations.
                                    </div>
                                </div>
                                <div class="chat-input">
                                    <input type="text" id="user-input" placeholder="Ask a question about this topic...">
                                    <button id="send-button">Send</button>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Quiz Tab -->
                    <div class="tab-content" id="quiz">
                        <div class="quiz-container" id="quiz-container">
                            <div class="question">
                                <h3>Question 1 of 5</h3>
                                <p>Which of the following is NOT a type of network topology?</p>
                                <ul class="options">
                                    <li class="option">Star</li>
                                    <li class="option">Square</li>
                                    <li class="option">Ring</li>
                                    <li class="option">Mesh</li>
                                </ul>
                            </div>
                            <div class="quiz-buttons">
                                <button class="submit-quiz">Submit Answer</button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Notes Tab -->
                    <div class="tab-content" id="notes">
                        <div class="notes-container">
                            <div class="notes-header">
                                <h3>Your Notes</h3>
                                <button class="new-note" id="create-note">New Note</button>
                            </div>
                            
                            <div class="notes-list" id="notes-list">
                                <div class="note selected">
                                    <div class="note-title">Network Fundamentals Key Points</div>
                                    <div class="note-preview">LAN = Local Area Network, typically in a single location...</div>
                                </div>
                                <div class="note">
                                    <div class="note-title">OSI Model Layers</div>
                                    <div class="note-preview">7. Application, 6. Presentation, 5. Session, 4. Transp...</div>
                                </div>
                            </div>
                            
                            <div class="note-editor">
                                <div class="note-editor-header">
                                    <input type="text" id="note-title" placeholder="Note title..." value="Network Fundamentals Key Points">
                                </div>
                                <div class="note-editor-body">
                                    <textarea id="note-content" placeholder="Start typing your notes here...">LAN = Local Area Network, typically in a single location like home or office
WAN = Wide Area Network, covers large geographic area
MAN = Metropolitan Area Network, covers a city

Topologies:
- Star: All devices connect to central hub
- Bus: All devices connect to single backbone
- Ring: Devices connect in a loop
- Mesh: Devices interconnected for redundancy

Remember: Switches operate at Layer 2, Routers at Layer 3</textarea>
                                </div>
                                <div class="note-editor-footer">
                                    <button class="delete-note" id="delete-note">Delete</button>
                                    <button class="save-note" id="save-note">Save</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
    <footer>
        <p>© 2025 Networking Academy - Virtual Classroom Experience</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Topic navigation
            const topics = document.querySelectorAll('.topic');
            const topicTitle = document.getElementById('topic-title');
            
            topics.forEach(topic => {
                topic.addEventListener('click', function() {
                    // Remove active class from all topics
                    topics.forEach(t => t.classList.remove('active'));
                    // Add active class to clicked topic
                    this.classList.add('active');
                    // Update topic title
                    topicTitle.textContent = this.textContent;
                    
                    // Here you would typically load new content based on the selected topic
                    // For this example, we'll just update the lesson content heading
                    const lessonContent = document.querySelector('.lesson-content h3');
                    lessonContent.textContent = `Introduction to ${this.textContent}`;
                });
            });
            
            // Tab navigation
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');
            
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    // Remove active class from all buttons and contents
                    tabButtons.forEach(btn => btn.classList.remove('active'));
                    tabContents.forEach(content => content.classList.remove('active'));
                    
                    // Add active class to clicked button
                    this.classList.add('active');
                    
                    // Show corresponding content
                    const tabId = this.getAttribute('data-tab');
                    document.getElementById(tabId).classList.add('active');
                });
            });
            
            // Quiz option selection
            const quizOptions = document.querySelectorAll('.quiz-container .option');
            
            quizOptions.forEach(option => {
                option.addEventListener('click', function() {
                    // Remove selected class from all options in this question
                    this.parentNode.querySelectorAll('.option').forEach(opt => {
                        opt.classList.remove('selected');
                    });
                    
                    // Add selected class to clicked option
                    this.classList.add('selected');
                });
            });
            
            // Note selection
            const notes = document.querySelectorAll('.note');
            
            notes.forEach(note => {
                note.addEventListener('click', function() {
                    // Remove selected class from all notes
                    notes.forEach(n => n.classList.remove('selected'));
                    
                    // Add selected class to clicked note
                    this.classList.add('selected');
                    
                    // Here you would typically load the note content into the editor
                    // For this example, we'll just update the editor with some dummy data
                    document.getElementById('note-title').value = this.querySelector('.note-title').textContent;
                    document.getElementById('note-content').value = this.querySelector('.note-preview').textContent;
                });
            });
            
            // Chat functionality (basic implementation)
            const sendButton = document.getElementById('send-button');
            const userInput = document.getElementById('user-input');
            const chatMessages = document.getElementById('chat-messages');
            
            sendButton.addEventListener('click', sendMessage);
            userInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            function sendMessage() {
                const message = userInput.value.trim();
                if (message) {
                    // Add user message
                    const userMsg = document.createElement('div');
                    userMsg.className = 'message user-message';
                    userMsg.textContent = message;
                    chatMessages.appendChild(userMsg);
                    
                    // Clear input
                    userInput.value = '';
                    
                    // Simulate AI response after a short delay
                    setTimeout(() => {
                        const aiMsg = document.createElement('div');
                        aiMsg.className = 'message ai-message';
                        aiMsg.textContent = getAIResponse(message);
                        chatMessages.appendChild(aiMsg);
                        
                        // Scroll to bottom
                        chatMessages.scrollTop = chatMessages.scrollHeight;
                    }, 1000);
                }
            }
            
            function getAIResponse(message) {
                // Simple response logic - in a real app this would call an API
                const responses = {
                    "router": "A router is a networking device that forwards data packets between computer networks.",
                    "switch": "A network switch connects devices on a computer network by using packet switching to receive and forward data.",
                    "default": "I'm your AI networking instructor. Could you clarify your question about networking concepts?"
                };
                
                message = message.toLowerCase();
                if (message.includes('router')) {
                    return responses["router"];
                } else if (message.includes('switch')) {
                    return responses["switch"];
                } else {
                    return responses["default"];
                }
            }
        });
    </script>
</body>
</html>
