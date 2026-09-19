# 🩺 Medical Chatbot — AI-Powered Healthcare Assistant

An **AI-powered Medical Chatbot** built using **Retrieval-Augmented Generation (RAG)** to provide informative responses to healthcare-related questions. The system combines **semantic search, vector embeddings, FAISS, LangChain, and a Large Language Model (Mistral)** to retrieve relevant medical information and generate contextual responses.

> ⚠️ **Disclaimer:** This project is intended for educational and informational purposes only. It is **not a substitute for professional medical advice, diagnosis, or treatment.**

---

## 📌 Overview

Traditional chatbots often generate responses solely from the knowledge stored inside an LLM. This can lead to irrelevant or unsupported answers, especially in specialized domains such as healthcare.

This project addresses that problem using a **Retrieval-Augmented Generation (RAG) pipeline**.

The chatbot first searches a medical knowledge base for relevant information using **Hugging Face embeddings and FAISS**, then provides the retrieved context to the language model to generate a more relevant response.

### 🔄 How It Works

```text
                 User Question
                       │
                       ▼
              ┌─────────────────┐
              │    Streamlit    │
              │   Chat Interface│
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Query Processing│
              └────────┬────────┘
                       │
                       ▼
            ┌──────────────────────┐
            │ Hugging Face         │
            │ Embedding Model      │
            └──────────┬───────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  FAISS Vector   │
              │     Search      │
              └────────┬────────┘
                       │
                 Relevant Context
                       │
                       ▼
              ┌─────────────────┐
              │      Mistral    │
              │       LLM       │
              └────────┬────────┘
                       │
                       ▼
                Generated Answer
```

---

## ✨ Key Features

* 🤖 **AI-powered medical conversational assistant**
* 🔎 **Semantic search** over a medical knowledge base
* 🧠 **Retrieval-Augmented Generation (RAG)**
* 📚 Medical document-based knowledge retrieval
* 🔢 **Hugging Face embeddings** for semantic representation
* ⚡ **FAISS** for efficient vector similarity search
* 🔗 **LangChain** for retrieval and LLM orchestration
* 💬 Interactive **Streamlit chat interface**
* 🧩 Context-aware response generation
* 🐍 Built completely with Python
* 📦 Reproducible environment using **Pipenv**

---

## 🛠️ Tech Stack

| Technology       | Purpose                               |
| ---------------- | ------------------------------------- |
| **Python**       | Core programming language             |
| **LangChain**    | RAG and LLM orchestration             |
| **Hugging Face** | Text embeddings                       |
| **FAISS**        | Vector database / similarity search   |
| **Mistral**      | Large Language Model                  |
| **Streamlit**    | Web-based chatbot interface           |
| **PyPDF**        | PDF document processing               |
| **Pipenv**       | Dependency and environment management |

---

## 🧠 RAG Architecture

The project follows a Retrieval-Augmented Generation architecture:

### 1. 📄 Knowledge Base

Medical information is collected from the available medical documents.

### 2. ✂️ Document Processing

Documents are processed and divided into smaller chunks that can be efficiently searched.

### 3. 🔢 Embedding Generation

Each document chunk is converted into a numerical vector using a **Hugging Face embedding model**.

### 4. 🗄️ Vector Storage

The generated embeddings are stored in a **FAISS vector database**.

### 5. 🔍 Retrieval

When the user asks a question, the question is converted into an embedding and FAISS retrieves the most semantically relevant information.

### 6. 🤖 Response Generation

The retrieved context is provided to the **Mistral language model**, which generates the final response.

---

## 📁 Project Structure

```text
medical-chatbot/
│
├── data/
│   └── Medical_book.pdf
│
├── vectorstore/
│   └── db_faiss/
│       └── FAISS vector database
│
├── create_memory_for_llm.py
│   └── Creates embeddings and vector database
│
├── connect_memory_with_llm.py
│   └── Connects retrieved context with the LLM
│
├── medibot.py
│   └── Main Streamlit chatbot application
│
├── requirements.txt
├── Pipfile
├── Pipfile.lock
├── medical-chatbot-ppt.pdf
└── README.md
```

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/AIwithhassan/medical-chatbot.git

cd medical-chatbot
```

---

## 2. Create a Virtual Environment

Using Pipenv:

```bash
pip install pipenv

pipenv install
```

Activate the environment:

```bash
pipenv shell
```

Alternatively, install the required packages using:

```bash
pip install -r requirements.txt
```

---

## 3. Configure Hugging Face

Create a Hugging Face account and generate an API token.

Then configure your token as an environment variable.

### Windows

```bash
set HF_TOKEN=your_huggingface_token
```

### Linux / macOS

```bash
export HF_TOKEN=your_huggingface_token
```

> Never commit API keys or tokens directly to GitHub.

---

## 4. Create the Vector Database

Run the embedding/vector-store generation script:

```bash
python create_memory_for_llm.py
```

This processes the medical documents, generates embeddings, and creates the FAISS vector store.

---

## 5. Start the Chatbot

Run the Streamlit application:

```bash
streamlit run medibot.py
```

The application will open in your browser.

---

# 💬 Example Questions

You can ask questions such as:

```text
What are the symptoms of diabetes?

What are common causes of headaches?

What are the symptoms of hypertension?

What precautions can be taken for common illnesses?

What are the common symptoms of a particular disease?
```

The chatbot retrieves relevant information from the medical knowledge base before generating its response.

---

# 🔬 Why RAG?

A standard LLM generates answers from its pretrained knowledge.

With **RAG**, the system follows:

```text
Question
   ↓
Semantic Search
   ↓
Relevant Medical Information
   ↓
LLM + Retrieved Context
   ↓
Contextual Response
```

This allows the chatbot to ground its responses in the project's medical knowledge base rather than relying entirely on the model's internal knowledge.

---

# 📊 Project Highlights

### Retrieval-Augmented Generation

Implemented a complete RAG pipeline combining:

* Document processing
* Text embeddings
* Vector similarity search
* Context retrieval
* LLM-based response generation

### Semantic Search

Instead of matching only exact keywords, the system searches for information based on **semantic similarity** between the user's question and medical documents.

### Vector Database

FAISS enables efficient similarity search over the generated document embeddings.

### Conversational Interface

Streamlit provides a simple interactive interface for users to communicate with the medical assistant.

---

# 🔮 Future Improvements

The project can be extended with:

* 🎙️ Voice-based medical conversations
* 🗣️ Speech-to-text and text-to-speech
* 🌐 Multilingual support
* 👤 User authentication
* 💾 Conversation history
* 🏥 Integration with medical APIs
* 📑 Citation of retrieved medical sources
* 📊 Response confidence and relevance scoring
* 🧠 Improved medical-domain LLM
* 🔐 Privacy-preserving healthcare architecture
* 🚨 Emergency symptom detection and appropriate escalation
* 📱 Mobile-friendly interface

---

# ⚠️ Medical Disclaimer

This chatbot is an **educational AI project** and should not be used as a replacement for a qualified doctor or healthcare professional.

The generated responses may contain inaccuracies. Users should consult a licensed medical professional for diagnosis, treatment decisions, medication recommendations, or emergency situations.

---

# 🎯 Learning Outcomes

Through this project, the following concepts can be explored:

* Retrieval-Augmented Generation
* Large Language Models
* Natural Language Processing
* Semantic Search
* Text Embeddings
* Vector Databases
* FAISS
* LangChain
* Hugging Face
* Prompt Engineering
* Document Processing
* Streamlit Application Development

---

# 👩‍💻 Author

**Sayantika Chowdhury**

B.Tech — Computer Science & Engineering

### Areas of Interest

* 🤖 Artificial Intelligence
* 🧠 Machine Learning
* 🧬 Deep Learning
* 💬 Generative AI
* 🔎 Retrieval-Augmented Generation
* 🏥 AI in Healthcare

---

## ⭐ If you find this project useful

Consider giving the repository a ⭐ star and exploring the implementation to learn more about building domain-specific AI assistants with RAG.
