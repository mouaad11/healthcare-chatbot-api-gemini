# Healthcare Assistant API

A Flask-based REST API that integrates with Google's Gemini Pro model to provide an intelligent healthcare assistant service. The assistant helps patients assess their symptoms and guides them towards appropriate medical care while maintaining conversation context through session management.

## Features

- 🤖 Powered by Google's Gemini Pro AI model
- 💬 Stateful conversation management with session tracking
- 🏥 Specialized healthcare-focused responses
- 🔒 Secure session handling
- 🚀 RESTful API architecture
- 🔍 Health check endpoint for monitoring

## Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.8 or higher
- pip (Python package manager)
- A Google Cloud account with access to the Gemini API

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/healthcare-assistant-api.git
cd healthcare-assistant-api
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

3. Install the required dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the project root and add your Gemini API key:
```
GEMINI_API_KEY=your_api_key_here
```

## Running the Application

To start the server in development mode:
```bash
python app.py
```

The API will be available at `http://localhost:5000`

## API Endpoints

### 1. Start Session
Creates a new conversation session.

```
POST /start_session
Response:
{
    "status": "success",
    "session_id": "uuid",
    "message": "Hello, I'm your professional healthcare assistant"
}
```

### 2. Generate Response
Sends a message to the healthcare assistant and receives a response.

```
POST /generate
Request Body:
{
    "prompt": "your message here",
    "session_id": "your_session_id"
}

Response:
{
    "response": "AI assistant's response",
    "session_id": "session_id",
    "status": "success"
}
```

### 3. End Session
Terminates a conversation session and clears its history.

```
POST /end_session
Request Body:
{
    "session_id": "your_session_id"
}

Response:
{
    "status": "success",
    "message": "Session ended and conversation history cleared"
}
```

### 4. Health Check
Verify if the API is running.

```
GET /health
Response:
{
    "status": "healthy",
    "message": "Healthcare Assistant API is up and running"
}
```

## Error Handling

The API includes comprehensive error handling for common scenarios:
- Invalid session IDs
- Missing required parameters
- Model generation errors
- Unexpected server errors

All errors return appropriate HTTP status codes and detailed error messages in the response.

## Security Considerations

- The application uses environment variables for sensitive data
- Each session has a unique UUID
- Session data is stored in memory (consider using a persistent storage solution for production)
- The application generates a random secret key on startup for session management

## Production Deployment Notes

Before deploying to production, consider:
1. Using a production-grade WSGI server (e.g., Gunicorn)
2. Implementing rate limiting
3. Adding authentication/authorization
4. Using a persistent storage solution for session management
5. Setting up proper logging
6. Configuring CORS if needed
7. Setting `debug=False` in production

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Google Generative AI team for the Gemini Pro model
- Flask framework contributors
- All contributors to this project
