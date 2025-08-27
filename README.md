# 🤖 AI Search Agent

A sophisticated multi-source research agent that combines Google, Bing, and Reddit search results to provide comprehensive answers using advanced AI analysis and synthesis.

## 🚀 Features

### 🔍 **Multi-Source Search Engine**
- **Google Search Integration**: Leverages Bright Data's SERP API for comprehensive web search results
- **Bing Search Integration**: Captures Microsoft ecosystem and enterprise perspectives
- **Reddit Search & Analysis**: Deep-dives into community discussions and user experiences

### 🧠 **Advanced AI Analysis Pipeline**
- **Parallel Processing**: Simultaneously searches all sources for maximum efficiency
- **Intelligent Content Selection**: AI-powered filtering of relevant Reddit posts and comments
- **Multi-Perspective Analysis**: Specialized prompts for each data source type
- **Comprehensive Synthesis**: Combines insights from all sources into coherent answers

### 🏗️ **Modern Architecture**
- **LangGraph Workflow**: State-driven graph execution for complex research tasks
- **Modular Design**: Clean separation of concerns with dedicated modules
- **Type Safety**: Full TypeScript-style type hints and Pydantic models
- **Error Handling**: Robust error handling with graceful fallbacks

### 📊 **Data Processing Capabilities**
- **Structured Data Extraction**: Parses search results into organized formats
- **Comment Retrieval**: Fetches detailed Reddit discussions and user comments
- **Snapshot Management**: Efficient handling of Bright Data API snapshots
- **Real-time Polling**: Monitors data processing status with progress indicators

## 🛠️ Technology Stack

- **Python 3.12+**: Modern Python with type hints
- **LangChain**: AI/LLM orchestration framework
- **LangGraph**: Workflow and state management
- **Ollama**: Local LLM integration (Qwen2.5:7B)
- **Bright Data**: Web scraping and data collection APIs
- **Pydantic**: Data validation and serialization
- **uv**: Fast Python package management

## 📁 Project Structure

```
AI Search Agent/
├── main.py                 # Main application and workflow orchestration
├── web_operations.py      # Search API integrations and data retrieval
├── prompts.py             # AI prompt templates and message management
├── snapshot_oprations.py  # Bright Data snapshot handling utilities
├── pyproject.toml         # Project dependencies and configuration
├── uv.lock               # Locked dependency versions
└── .env                  # Environment variables (API keys)
```

## 🚀 Quick Start

### Prerequisites

1. **Python 3.12+** installed
2. **Ollama** with Qwen2.5:7B model
3. **Bright Data API** account and API key

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd AI-Search-Agent
   ```

2. **Install dependencies using uv**
   ```bash
   uv sync
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your Bright Data API key
   ```

4. **Install Ollama and download the model**
   ```bash
   # Install Ollama (https://ollama.ai)
   ollama pull qwen2.5:7b-instruct
   ```

### Usage

Run the interactive chatbot:
```bash
python main.py
```

Example interaction:
```
Ask me anything: What are the best practices for implementing authentication in React applications?

Starting parallel research process...
Launching Google, Bing, and Reddit searches...

Final Answer:
Based on comprehensive research across multiple sources:

**Google Analysis:**
- Official React documentation recommends using Auth0, Firebase Auth, or custom JWT implementations
- Key security considerations include token storage, CSRF protection, and secure redirects

**Bing Analysis:**
- Microsoft's Azure AD integration provides enterprise-grade authentication
- Recent updates include improved OAuth 2.0 flows and PKCE support

**Reddit Community Insights:**
- "Use httpOnly cookies for JWT storage instead of localStorage" - r/reactjs user
- "Consider using NextAuth.js for Next.js projects" - r/webdev community consensus
- "Implement refresh token rotation for better security" - r/security expert advice

**Best Practices Summary:**
1. Use httpOnly cookies for token storage
2. Implement proper CORS and CSRF protection
3. Consider established libraries like NextAuth.js or Auth0
4. Implement refresh token rotation
5. Use PKCE for OAuth flows
```

## 🔧 Configuration

### Environment Variables

Create a `.env` file with:
```env
BRIGHTDATA_API_KEY=your_bright_data_api_key_here
```

### Model Configuration

The agent uses Qwen2.5:7B by default. To change models, modify the `llm` variable in `main.py`:

```python
# For different Ollama models
llm = ChatOllama(model="llama3.1:8b")

# For OpenAI (requires API key)
from langchain_openai import ChatOpenAI
llm = ChatOpenAI(model="gpt-4")
```

## 🏗️ Architecture Deep Dive

### Workflow Graph

The agent uses a sophisticated state-driven workflow:

```
START
├── Parallel Search Nodes
│   ├── google_search
│   ├── bing_search
│   └── reddit_search
├── Content Analysis
│   ├── analyze_reddit_posts (URL selection)
│   ├── retrieve_reddit_posts (comment fetching)
│   ├── analyze_google_results
│   ├── analyze_bing_results
│   └── analyze_reddit_results
└── synthesize_analyses → END
```

### State Management

The `State` class manages data flow between nodes:
- Search results from each source
- AI analysis outputs
- Selected Reddit URLs and post data
- Final synthesized answer

### Prompt Engineering

Specialized prompts for each analysis type:
- **Google Analysis**: Focus on factual, authoritative information
- **Bing Analysis**: Emphasize complementary perspectives and technical details
- **Reddit Analysis**: Extract community insights and user experiences
- **Synthesis**: Combine all analyses into coherent answers

## 📈 Performance Features

- **Parallel Execution**: All search operations run simultaneously
- **Intelligent Caching**: Reddit post selection reduces unnecessary API calls
- **Progress Monitoring**: Real-time status updates for long-running operations
- **Error Resilience**: Graceful handling of API failures and timeouts

## 🔒 Security & Best Practices

- **API Key Management**: Secure environment variable handling
- **Input Validation**: Structured data validation with Pydantic
- **Rate Limiting**: Built-in delays and retry logic
- **Error Logging**: Comprehensive error tracking without exposing sensitive data

## 🚧 Limitations & Considerations

- **API Dependencies**: Requires active Bright Data subscription
- **Local LLM**: Ollama must be running locally for AI processing
- **Search Quotas**: Subject to Bright Data API rate limits
- **Model Quality**: Local model performance depends on hardware capabilities

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Bright Data** for web scraping and data collection APIs
- **LangChain** for AI orchestration framework
- **Ollama** for local LLM capabilities
- **OpenAI** for inspiration in prompt engineering

## 📞 Support

For questions, issues, or contributions:
- Open an issue on GitHub
- Check the project documentation
- Review the code examples in the repository

---

**Built with ❤️ for comprehensive research and AI-powered insights** 