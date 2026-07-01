# LangChain Chat Models Project

A Python project demonstrating the integration and usage of various AI chat models through LangChain, including Groq and Hugging Face models.

## 📋 Overview

This project provides examples of how to use different language models for chat applications using the LangChain framework. Currently supports:

- **Groq Models**: Fast inference with Llama models
- **Hugging Face Models**: Access to open-source models via Hugging Face Hub

## 🚀 Features

- Multiple chat model implementations
- Environment-based configuration for API keys
- Easy-to-use examples for each model type
- Modular structure for adding new model integrations

## 📁 Project Structure

```
├── ChatModels/
│   ├── chatgroq.py          # Groq chat model implementation
│   └── Chatmodel_hf.py      # Hugging Face chat model implementation
├── EmbeddingModels/         # Directory for embedding model implementations
├── .env                     # Environment variables (API keys)
├── .gitignore              # Git ignore rules
├── requirements.txt        # Python dependencies
└── README.md              # Project documentation
```

## 🛠️ Installation

1. **Clone the repository** (or download the files)

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**:
   Create a `.env` file in the root directory with your API keys:
   ```env
   GROQ_API_KEY="your_groq_api_key_here"
   HUGGINGFACEHUB_ACCESS_TOKEN="your_huggingface_token_here"
   ```

## 🔑 API Keys Setup

### Groq API Key
1. Visit [Groq Console](https://console.groq.com/)
2. Sign up or log in
3. Navigate to API Keys section
4. Generate a new API key
5. Add it to your `.env` file

### Hugging Face Access Token
1. Visit [Hugging Face](https://huggingface.co/)
2. Sign up or log in
3. Go to Settings > Access Tokens
4. Create a new token with appropriate permissions
5. Add it to your `.env` file

## 💻 Usage

### Groq Chat Model

```python
from langchain_groq import ChatGroq
from dotenv import load_dotenv

load_dotenv()

llm = ChatGroq(
    model="llama-3.1-8b-instant",
    temperature=0.7
)

result = llm.invoke("Your question here")
print(result.content)
```

Run the example:
```bash
python ChatModels/chatgroq.py
```

### Hugging Face Chat Model

```python
from langchain_huggingface import ChatHuggingFace, HuggingFaceEndpoint
from dotenv import load_dotenv

load_dotenv()

llm = HuggingFaceEndpoint(
    repo_id="TinyLlama/TinyLlama-1.1B-Chat-v1.0",
    task="text-generation",
    max_new_tokens=512,
    temperature=0.7,
)

model = ChatHuggingFace(llm=llm)
result = model.invoke("Your question here")
print(result.content)
```

Run the example:
```bash
python ChatModels/Chatmodel_hf.py
```

## 📦 Dependencies

- `langchain-core`: Core LangChain functionality
- `langchain`: Main LangChain package
- `langchain-groq`: Groq integration for LangChain
- `langchain-openai`: OpenAI integration (if needed)
- `langchain-anthropic`: Anthropic integration (if needed)
- `langchain-google-genai`: Google Generative AI integration (if needed)
- `langchain-huggingface`: Hugging Face integration
- `python-dotenv`: Environment variable management
- `numpy`: Numerical computations
- `scikit-learn`: Machine learning utilities

## 🔒 Security Notes

- **Never commit API keys** to version control
- The `.env` file is included in `.gitignore` to prevent accidental commits
- Keep your API keys secure and rotate them regularly
- Use environment variables for all sensitive configuration

## 🚧 Future Enhancements

- [ ] Add more model providers (OpenAI, Anthropic, Google)
- [ ] Implement embedding models in the `EmbeddingModels/` directory
- [ ] Add conversation memory management
- [ ] Create a unified interface for all models
- [ ] Add streaming support for real-time responses
- [ ] Implement model comparison utilities

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-model`)
3. Commit your changes (`git commit -am 'Add new model integration'`)
4. Push to the branch (`git push origin feature/new-model`)
5. Create a Pull Request

## 📄 License

This project is open source. Please check individual model provider terms of service for usage restrictions.

## 🆘 Troubleshooting

### Common Issues

1. **API Key Errors**: Ensure your `.env` file is properly configured and API keys are valid
2. **Import Errors**: Make sure all dependencies are installed (`pip install -r requirements.txt`)
3. **Model Loading Issues**: Some Hugging Face models may require authentication or have specific requirements

### Getting Help

- Check the [LangChain Documentation](https://python.langchain.com/)
- Review model provider documentation (Groq, Hugging Face)
- Open an issue in the repository for project-specific problems

## 🏷️ Version

Current Version: 1.0.0

---

**Happy Coding!** 🎉