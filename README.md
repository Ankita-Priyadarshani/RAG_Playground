# RAG Playground

An intelligent Retrieval-Augmented Generation (RAG) application that enables document-based conversational AI. Part of the SEMOSS PMO Portal suite, this application allows users to upload documents and engage in context-aware conversations with an AI assistant that can reference and retrieve information from uploaded content.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [Documentation](#documentation)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Overview

The RAG Playground revolutionizes how users interact with documents by combining the power of vector databases, embeddings, and Large Language Models (LLMs). Users can upload policy documents, PDFs, presentations, or text files, and then ask questions that are answered using the specific content from those documents.

Built on the SEMOSS platform, this application leverages state-of-the-art embedding models and multiple vector database options (FAISS, Weaviate, Pinecone, pgvector) to provide accurate, citation-backed responses. The system implements advanced retrieval techniques including semantic similarity search, intelligent chunking strategies, and context-aware prompting to ensure high-quality, hallucination-free responses.

---

## Key Features

- **Multiple Vector Database Support**: FAISS, Weaviate, Pinecone, or pgvector
- **Document Upload & Processing**: PDF, DOCX, PPT, and TXT file support
- **Conversational AI Interface**: Chat-based natural language queries
- **Context-Aware Responses**: AI retrieves relevant document sections with citations
- **Knowledge Base Management**: Create, manage, and delete vector databases
- **Configurable AI Parameters**: Adjust temperature, context limit, and model selection
- **Semantic Search**: Similarity-based retrieval using embeddings

---

## Technology Stack

### Frontend
- **React 17** - UI framework
- **TypeScript** - Type-safe JavaScript
- **Material UI v5** - Modern component library
- **React Router v6** - Client-side routing
- **Styled Components** (v5.3.11) - Component styling
- **React Markdown** (v8.0.7) - Markdown rendering with syntax highlighting
- **React Dropzone** (v14.2.3) - Drag-and-drop file upload
- **React Icons** (v4.10.1) - Icon components
- **Axios** (v0.24.0) - HTTP client
- **Webpack 5** - Module bundler

### Backend / AI Integration
- **Python** - Backend processing
- **OpenAI API** - GPT-4, GPT-3.5-turbo for text generation
- **OpenAI Embeddings** - text-embedding-ada-002 for vector embeddings
- **SEMOSS SDK** (v1.0.0-beta.14) - Core AI and database functionality
- **SEMOSS SDK React** (v1.0.0-beta.15) - React integration layer
- **NumPy** - Vector operations and similarity calculations
- **Pandas** - Data processing and CSV handling
- **tiktoken** - Token counting for context management

### Vector Databases
- **FAISS** - Facebook AI Similarity Search (default)
- **Weaviate** - Cloud-native vector database
- **Pinecone** - Managed vector database service
- **pgvector** - PostgreSQL extension for vector similarity

### Document Processing
- **PDF Text Extraction** - Extract text from PDF documents
- **Document Parsing** - Support for DOCX, PPT, and TXT formats
- **Chunking Strategies** - Configurable content splitting (512 token chunks with 20 token overlap)

---

## Installation

### Frontend Setup
```bash
# Navigate to client directory
cd assets/client

# Install dependencies using pnpm
pnpm install
```

### Python Dependencies
```bash
# Install required Python packages
pip install numpy pandas openai tiktoken
```

---

## Configuration

### Environment Variables
Create a `.env` file in the `assets/client` directory:
```env
# SEMOSS Configuration
MODULE=your-module-name
ACCESS_KEY=your-access-key
SECRET_KEY=your-secret-key
APP=your-app-id

# Vector Database Configuration
EMBEDDER_ENGINE=your-embedding-engine-id

# Optional: Development settings
NODE_ENV=development
PORT=3000
```

### Python Backend Configuration
Update `policy_bot.py` with your configuration:
```python
EMBEDDING_MODEL = "text-embedding-ada-002"
model = "gpt-4-32k"  # or "gpt-4", "gpt-3.5-turbo"
temp = 0.2
max_token = 1024
context_length = 3000
```

---

## Usage

### Starting Development Server
```bash
# In assets/client directory
pnpm install
pnpm dev

# Application will be available at http://localhost:3000
```

### Workflow

1. **Select AI Model** - Choose from available LLM models
2. **Create or Select Knowledge Base** - Create new or use existing vector database
3. **Upload Documents** - Upload files via sidebar or chat interface (PDF, DOCX, PPT, TXT)
4. **Ask Questions** - Chat interface retrieves relevant context and generates responses
5. **Review Responses** - View answers with citations and source attribution
6. **Manage Knowledge Bases** - View, delete documents, or switch between knowledge bases

### Building for Production
```bash
# Build frontend
cd assets/client
pnpm build

# Output will be in the build directory
```

---

## Deployment

### Build the Application
```bash
# Build frontend
cd assets/client
pnpm build
```

### Deploy to SEMOSS Platform (GovConnect.ai)

1. **Compress Portal**: Navigate to `assets` directory and compress the `portals` folder to zip
2. **Create App**: Log in to GovConnect.ai, create new app, select "Code" panel
3. **Upload**: Upload `portals.zip` to version/assets/ (check "Unzip?" option)
4. **Publish**: Go to Settings → Data Apps → Publish Portal → Show

---

## Contributing

We welcome contributions to the RAG Playground! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) file for detailed guidelines on:

- Code of Conduct
- How to submit issues
- How to propose new features
- Pull request process
- Coding standards and style guide
- Testing requirements

---

## Documentation

### Additional Resources
- [SEMOSS SDK Documentation](https://semoss.org/documentation)
- [OpenAI API Reference](https://platform.openai.com/docs)
- [FAISS Documentation](https://github.com/facebookresearch/faiss)
- [React Documentation](https://react.dev)
- [Material UI Documentation](https://mui.com)

---

## License

This project is proprietary software developed for the Defense Health Agency (DHA) as part of the SEMOSS PMO Portal suite. All rights reserved.

For licensing inquiries, please contact the project maintainers.

---

## Acknowledgments

This project is built using the following technologies:

- **[OpenAI](https://openai.com)** - GPT models and embedding APIs
- **[FAISS](https://github.com/facebookresearch/faiss)** - Vector similarity search
- **[SEMOSS](https://semoss.org)** - AI platform and SDK
- **[React](https://react.dev)** - UI framework
- **[Material UI](https://mui.com)** - Component library
- **[TypeScript](https://www.typescriptlang.org)** - Type-safe JavaScript
- **[NumPy & Pandas](https://numpy.org)** - Python data processing
- **[Webpack](https://webpack.js.org)** - Module bundler
- **[pnpm](https://pnpm.io)** - Package manager

---
