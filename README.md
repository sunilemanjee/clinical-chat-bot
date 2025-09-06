# Clinical Chat Bot

An intelligent clinical assistant powered by Azure AI services, featuring a conversational avatar for healthcare interactions.

## Features

- 🎤 **Voice Input**: Speech-to-text for natural conversation
- 🤖 **AI-Powered Responses**: Azure OpenAI for intelligent clinical assistance
- 👤 **Animated Avatar**: Realistic talking avatar with synchronized speech
- 📊 **Performance Monitoring**: Real-time latency metrics for optimization
- 🔄 **WebSocket Support**: Low-latency communication
- 🎨 **Customizable Interface**: Configurable avatar and voice settings

## Use Cases

- **Clinical Consultations**: Interactive patient consultations
- **Medical Education**: Training and educational scenarios
- **Patient Support**: 24/7 clinical assistance
- **Telemedicine**: Remote healthcare interactions

## Quick Start

### Prerequisites
- Python 3.7 or later
- Azure AI Services resources:
  - **Speech Service** (with TTS Avatar support)
  - **Azure OpenAI Service** 
  - **Cognitive Search** (optional, for medical knowledge base)

### Setup

1. **Clone and setup environment:**
```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

2. **Configure environment variables:**
Create a `variables.env` file with your Azure credentials:
```bash
# Speech Service
SPEECH_REGION=eastus2
SPEECH_KEY=your_speech_key_here
SPEECH_RESOURCE_URL=/subscriptions/your_subscription/resourceGroups/your_rg/providers/Microsoft.CognitiveServices/accounts/your_account

# Azure OpenAI
AZURE_OPENAI_ENDPOINT=https://your-openai.openai.azure.com/
AZURE_OPENAI_API_KEY=your_openai_key_here
AZURE_OPENAI_DEPLOYMENT_NAME=gpt-4o

# Optional: Medical Knowledge Base
COGNITIVE_SEARCH_ENDPOINT=https://your-search.search.windows.net/
COGNITIVE_SEARCH_API_KEY=your_search_key_here
COGNITIVE_SEARCH_INDEX_NAME=medical_knowledge_base
```

3. **Run the application:**
```bash
python -m flask run -h 0.0.0.0 -p 5000
```

4. **Access the application:**
- Clinical chat: `http://localhost:5000/chat`
- Basic demo: `http://localhost:5000/basic`

### Available Regions
TTS Avatar is available in: Southeast Asia, North Europe, West Europe, Sweden Central, South Central US, East US 2, and West US 2.

## Clinical Configuration

### System Prompt for Clinical Use
Configure the system prompt in the chat interface for clinical scenarios:

```
You are a professional clinical assistant. Provide accurate, evidence-based medical information while always reminding users to consult with healthcare professionals for medical decisions. Focus on:

- Symptom assessment guidance
- General health information
- Medication information
- Preventive care recommendations
- When to seek immediate medical attention

Always emphasize that this is for informational purposes only and not a substitute for professional medical advice.
```

### Avatar Settings for Clinical Environment
- **Character**: Professional appearance (e.g., `lisa` with professional styling)
- **Voice**: Clear, professional tone
- **Background**: Clean, medical environment

## Performance Monitoring

The application provides real-time performance metrics:

- **AOAI Latency**: Time for Azure OpenAI to generate first sentence
- **TTS Latency**: Time from response received to avatar speaking
- **STT Latency**: Speech-to-text processing time
- **App Service Latency**: Application overhead

## Deployment

### Docker Deployment
```bash
# Build image
docker build -t clinical-chat-bot .

# Run container
docker run -p 5000:5000 --env-file variables.env clinical-chat-bot
```

### Azure Container Apps
1. Build and push Docker image to Azure Container Registry
2. Create Container App with environment variables
3. Deploy with WebSocket support enabled
4. Configure for HIPAA compliance if handling PHI

## File Structure

```
├── app.py                 # Main Flask application
├── chat.html             # Clinical chat interface
├── basic.html            # Basic demo interface
├── static/
│   ├── js/
│   │   ├── chat.js       # Chat functionality
│   │   └── basic.js      # Basic demo functionality
│   ├── css/
│   │   └── styles.css    # Styling
│   └── image/            # Static assets
├── requirements.txt      # Python dependencies
├── Dockerfile           # Container configuration
├── vad_iterator.py      # Voice activity detection
└── variables.env        # Environment variables (create this)
```

## Clinical Considerations

### Privacy and Security
- Ensure HIPAA compliance for patient data
- Use secure communication protocols
- Implement proper access controls
- Regular security audits

### Medical Disclaimer
This application is for educational and informational purposes only. It is not intended to:
- Replace professional medical advice
- Diagnose medical conditions
- Provide treatment recommendations
- Handle emergency medical situations

Always consult with qualified healthcare professionals for medical decisions.

## Troubleshooting

- Ensure all Azure services are in supported regions
- Check microphone permissions in browser
- Verify environment variables are set correctly
- Monitor latency logs for performance issues
- Review Azure service quotas and limits

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
