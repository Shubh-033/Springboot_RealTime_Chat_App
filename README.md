# Real-Time Chat Application

A modern, real-time chat application built with **Spring Boot** and **WebSocket** technology. The application features a clean, user-friendly UI inspired by popular messaging platforms like WhatsApp and Instagram.

## 🚀 Features

- **Real-Time Messaging**: Instant message delivery using WebSocket protocol (STOMP over SockJS)
- **Modern UI**: WhatsApp-style chat interface with message bubbles
- **User-Friendly**: Simple name entry to join chat, no authentication required
- **Responsive Design**: Works seamlessly on different screen sizes
- **Message Timestamps**: Each message includes a timestamp for reference
- **Message Differentiation**: Visually distinct styling for sent (green) and received (white) messages
- **Enter to Send**: Quick message sending with Enter key support

## 🛠️ Technology Stack

### Backend
- **Spring Boot 4.0.1**: Framework for building Java applications
- **Spring WebSocket**: Real-time bidirectional communication
- **Spring Messaging**: Message handling with STOMP protocol
- **Thymeleaf**: Server-side template engine for HTML rendering
- **Lombok**: Reduce boilerplate code with annotations
- **Maven**: Dependency management and build tool

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with flexbox layout
- **Vanilla JavaScript**: Client-side logic without external frameworks
- **SockJS**: WebSocket emulation for better browser compatibility
- **STOMP**: Messaging protocol over WebSocket

### Infrastructure
- **Java 17**: Programming language
- **Apache Tomcat 11.0.15**: Embedded web server

## 📋 Project Structure

```
src/
├── main/
│   ├── java/com/chat/app/
│   │   ├── AppApplication.java           # Main Spring Boot application
│   │   ├── config/
│   │   │   └── WebSocketConfig.java      # WebSocket configuration
│   │   ├── controller/
│   │   │   └── ChatController.java       # Chat endpoints and message mapping
│   │   └── model/
│   │       └── ChatMessage.java          # Chat message data model
│   └── resources/
│       ├── application.properties         # Application configuration
│       └── templates/
│           └── chat.html                  # Main UI template
└── test/
    └── java/com/chat/app/
        └── AppApplicationTests.java       # Unit tests
```

## 🔧 Configuration

### Application Properties
Located in `src/main/resources/application.properties`:

```properties
spring.application.name=app
server.port=8081
```

The application runs on **port 8081** by default.

### WebSocket Configuration
- **Endpoint**: `/chat`
- **Message Broker**: Simple in-memory broker at `/topic`
- **Application Prefix**: `/app` for client messages
- **Allowed Origins**: `http://localhost:8080` (configurable)

## 🚀 Getting Started

### Prerequisites
- Java 17 or higher
- Maven 3.6+
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Shubh-033/Springboot_RealTime_Chat_App.git
   cd Springboot_RealTime_Chat_App
   ```

2. **Build the project**
   ```bash
   ./mvnw clean install
   ```
   Or on Windows:
   ```bash
   mvnw.cmd clean install
   ```

3. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```
   Or on Windows:
   ```bash
   mvnw.cmd spring-boot:run
   ```

4. **Access the application**
   - Open your browser and navigate to: `http://localhost:8081/chat`

### Quick Start

1. When the page loads, you'll see a modal prompting for your name
2. Enter your username and click "Join Chat"
3. Start typing messages in the message input box
4. Press **Enter** or click **Send** to send a message
5. Open additional browser tabs or windows to test with multiple users
6. Messages appear in real-time across all connected clients

## 📱 UI Components

### Chat Modal
- Appears on page load asking for username
- Validates that a name is provided before joining

### Chat Interface
- **Header**: Displays "Real Time Chat" title with green background
- **Message Area**: 
  - Shows all messages in conversation
  - Auto-scrolls to latest message
  - Green bubbles for your messages (right-aligned)
  - White bubbles for others' messages (left-aligned)
  - Timestamps shown for each message
- **Input Area**: Message composition field with Send button

### Styling
- **Primary Colors**: Green (#25d366 - WhatsApp green) and white
- **Background**: Light gray for conversation area (#e5ddd5)
- **Font**: Segoe UI, Tahoma, Geneva (modern sans-serif)
- **Max Message Width**: 70% of container
- **Rounded Corners**: 18px for message bubbles, 20px for send button

## 🔄 How It Works

### WebSocket Flow

1. **Connection Establishment**
   - Client connects to `/chat` endpoint via SockJS
   - STOMP protocol initializes the connection
   - Client subscribes to `/topic/messages` for incoming messages

2. **Message Sending**
   - User sends message from input field
   - Message sent to `/app/sendMessage` endpoint
   - Spring processes the message through ChatController
   - Message is broadcast to all subscribers at `/topic/messages`

3. **Message Reception**
   - All connected clients receive the message
   - JavaScript displays message with appropriate styling
   - Message includes sender name, content, and timestamp

### Data Model

```java
ChatMessage {
    Long id;           // Message identifier
    String sender;     // Username of sender
    String content;    // Message text
}
```

## 🐛 Error Handling

- **Port Conflict**: If port 8081 is already in use, change it in `application.properties`
- **Connection Issues**: Ensure WebSocket is enabled and not blocked by firewall
- **Origin Issues**: CORS is configured for localhost; adjust in `WebSocketConfig.java` for other domains

## 🔐 Security Considerations

This is a **demonstration application** for educational purposes. For production use:

- Implement user authentication (JWT, OAuth2)
- Add message persistence (Database)
- Implement rate limiting and input validation
- Use HTTPS and WSS (Secure WebSocket)
- Add authorization checks
- Sanitize user inputs to prevent XSS attacks
- Configure proper CORS policies
- Add logging and monitoring

## 📈 Future Enhancements

- User authentication and registration
- Persistent message storage with database
- User online/offline status
- Typing indicators
- Message reactions and emojis
- File/Image sharing
- Group chat support
- User profiles and avatars
- Message search and filtering
- Push notifications
- Mobile app version

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

**Subham** - [GitHub Profile](https://github.com/Shubh-033)

## 📞 Support

For issues, questions, or suggestions, please open an issue on the GitHub repository.

## 🙏 Acknowledgments

- Spring Boot documentation and community
- WebSocket technology pioneers
- UI/UX inspiration from WhatsApp and Instagram

---

**Happy Chatting!** 💬
