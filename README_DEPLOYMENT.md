# Cassava Support Orchestrator

An AI-native customer support automation platform developed by Team MultiAgent, leveraging Large Language Models (LLMs) to streamline customer service operations.

## Overview

The Cassava Support Orchestrator is a comprehensive customer support application that integrates specialized AI agents to handle various aspects of customer service, including:

- **Automated ticket generation** from multiple channels (WhatsApp, Email)
- **SLA tracking and management**
- **Intelligent response generation** using RAG (Retrieval Augmented Generation)
- **Audio transcription** for voice-based support
- **Real-time support triaging** via Slack and WhatsApp integration
- **Automated service recovery** with apology and reward dispatch

## Architecture

The solution is built on a modular, multi-agent architecture:

- **DM2TicketAgent**: Converts WhatsApp voice messages to support tickets
- **EmailAgent**: Parses and processes email inquiries
- **ApologyAgent & RewardTool**: Handles automated service recovery
- **InsightTool**: Generates weekly performance reports
- **RAG Responder**: Provides context-aware responses using knowledge bases

## Technology Stack

- **Framework**: Streamlit (Python web application)
- **LLM Integration**: OpenAI GPT models
- **Vector Database**: ChromaDB for knowledge base storage
- **Audio Processing**: OpenAI Whisper for speech-to-text
- **Embeddings**: Sentence Transformers for semantic search
- **Orchestration**: LangChain for multi-agent workflows

## Repository Structure

```
.
├── agents/               # AI agent implementations
├── assets/              # Knowledge base documents and audio files
│   ├── audio/          # Sample audio files
│   ├── free/           # Free tier knowledge base
│   └── paid/           # Premium tier knowledge base
├── chroma_db/          # Vector database storage
├── data/               # Data handling and validation modules
├── graph/              # Graph-based workflow structures
├── tools/              # Utility tools (audio transcription, RAG, user DB)
├── ui/                 # User interface components
├── llm_app.py          # Main Streamlit application
├── customer_support.py # Core customer support pipeline
├── requirements.txt    # Python dependencies
└── Procfile           # Deployment configuration
```

## Local Development

### Prerequisites

- Python 3.10 or higher
- OpenAI API key

### Installation

1. Clone the repository:
```bash
git clone https://github.com/erictcarter/CassavaSupportOrchestrator.git
cd CassavaSupportOrchestrator
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
```bash
export OPENAI_API_KEY='your-api-key-here'
```

4. Run the application:
```bash
streamlit run llm_app.py
```

The application will be available at `http://localhost:8501`

## Deployment

### Deploy to Render

Render is the recommended platform for deploying this Streamlit application.

#### Quick Deploy Steps:

1. **Create a Render account** at https://render.com

2. **Connect your GitHub repository**:
   - Click "New +" → "Web Service"
   - Select this repository

3. **Configure the service**:
   - **Name**: `cassava-support-orchestrator`
   - **Runtime**: Python 3
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `streamlit run llm_app.py --server.port=$PORT --server.address=0.0.0.0`

4. **Set environment variables**:
   - Add `OPENAI_API_KEY` with your OpenAI API key

5. **Deploy**: Click "Create Web Service"

Your application will be live at `https://your-service-name.onrender.com`

### Alternative Deployment Options

- **Streamlit Community Cloud**: Free hosting for Streamlit apps
  - Visit: https://streamlit.io/cloud
  - Connect GitHub and deploy

- **Railway**: Similar to Render with automatic deployments
  - Visit: https://railway.app

- **Google Cloud Run**: For enterprise-scale deployments
  - Requires Docker containerization

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `OPENAI_API_KEY` | OpenAI API key for LLM functionality | Yes |

## Features

### 1. Multi-Channel Support
- WhatsApp voice message processing
- Email inquiry handling
- Real-time chat interface

### 2. Intelligent Response Generation
- Context-aware responses using RAG
- Subscription-based knowledge base selection
- Multi-retrieval chains for accurate information

### 3. Audio Processing
- Speech-to-text transcription using Whisper
- Automatic call summarization
- Integration with ticket generation

### 4. User Management
- Email/phone authentication
- Subscription tier management
- User information database

### 5. Workflow Visualization
- Interactive graph view of conversation flow
- Real-time node state tracking
- Visual representation of agent orchestration

## Cost Estimation

- **Hosting (Render)**: $0-$7/month
- **OpenAI API**: ~$0.01-$0.10 per conversation
- **Total**: Under $10/month for low to moderate traffic

## Security Best Practices

1. Never commit API keys to the repository
2. Use environment variables for all sensitive data
3. Enable HTTPS (provided automatically by Render)
4. Implement rate limiting for production use
5. Regularly update dependencies

## Troubleshooting

### Common Issues

**Build Failures**:
- Check dependency compatibility in `requirements.txt`
- Review build logs for specific errors

**API Key Errors**:
- Verify `OPENAI_API_KEY` is set correctly
- Ensure the API key has sufficient credits

**Memory Issues**:
- The application uses ML models that require significant memory
- Consider upgrading to a paid tier with more resources

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is developed by Team MultiAgent for the Cassava AI Infrastructure initiative.

## Support

For issues and questions:
- Open an issue on GitHub
- Refer to the [Deployment Guide](DEPLOYMENT_GUIDE.md)
- Check the [Solution Documentation](Solution%20Methodology.pdf)

## Acknowledgments

- Built with [Streamlit](https://streamlit.io)
- Powered by [OpenAI](https://openai.com)
- Vector search by [ChromaDB](https://www.trychroma.com)
- Orchestration by [LangChain](https://langchain.com)

---

**Note**: This is a proof-of-concept application demonstrating AI-native customer support automation. For production use, additional security, monitoring, and scalability considerations should be implemented.
