# 🎥 Compliance QA Pipeline

An AI-powered compliance auditing system that automatically analyzes YouTube videos and checks them against company policies and regulatory guidelines using Azure AI services, Retrieval-Augmented Generation (RAG), and LangGraph.

---

## 📌 Overview

Manual compliance auditing of advertisements and marketing videos is time-consuming and prone to human error. This project automates the process by extracting video insights, retrieving relevant compliance policies, and generating an AI-powered compliance report.

The system integrates Azure Video Indexer, Azure AI Search, Azure OpenAI, and LangGraph to create an intelligent compliance pipeline.

---

## 🚀 Features

- Analyze YouTube videos using a video URL
- Automatically extract:
  - Speech transcript
  - OCR text
  - Video insights
- Retrieve relevant compliance documents using Azure AI Search
- Perform Retrieval-Augmented Generation (RAG)
- Detect policy violations using Azure OpenAI
- Generate structured compliance reports
- Modular LangGraph workflow
- FastAPI REST API
- Azure Monitor / OpenTelemetry integration

---

## 🏗️ Architecture

```
                User
                  │
                  ▼
            FastAPI API
                  │
                  ▼
          LangGraph Workflow
                  │
      ┌───────────┴───────────┐
      ▼                       ▼
 Video Indexer Node     Compliance Audit Node
      │                       │
      ▼                       ▼
Azure Video Indexer     Azure OpenAI
      │                       ▲
      ▼                       │
Transcript + OCR      Azure AI Search
                  │
                  ▼
          Compliance Report
```

---

## 🛠️ Tech Stack

### Backend

- Python
- FastAPI

### AI Frameworks

- LangGraph
- LangChain

### Azure Services

- Azure OpenAI
- Azure AI Search
- Azure Video Indexer
- Azure Blob Storage
- Azure Monitor

### Other Tools

- yt-dlp
- Docker
- OpenTelemetry

---

## 📂 Project Structure

```
ComplianceQAPipeline/
│
├── backend/
│   ├── api/
│   ├── graph/
│   ├── services/
│   ├── data/
│   ├── scripts/
│   └── tests/
│
├── azure_functions/
│
├── main.py
├── pyproject.toml
├── Dockerfile
├── README.md
└── .env
```

---

## ⚙️ Workflow

1. User submits a YouTube video URL.
2. Video is downloaded.
3. Azure Video Indexer extracts:
   - Transcript
   - OCR text
   - Video insights
4. Compliance documents are retrieved from Azure AI Search.
5. Azure OpenAI analyzes the video against retrieved policies.
6. A structured compliance report is generated.

---

## 🧠 Retrieval-Augmented Generation (RAG)

The project uses RAG to improve answer accuracy.

Workflow:

```
Compliance PDFs
        │
        ▼
Document Chunking
        │
        ▼
Embeddings
        │
        ▼
Azure AI Search
        │
        ▼
Relevant Policy Sections
        │
        ▼
Azure OpenAI
        │
        ▼
Compliance Report
```

---

## 📄 Compliance Report Includes

- Compliance status
- Detected violations
- Severity level
- Explanation
- Recommendations
- Supporting policy references

---

## 📦 Installation

Clone the repository

```bash
git clone https://github.com/Pranayrebeyro/ComplianceQAPipeline.git
```

Navigate to the project

```bash
cd ComplianceQAPipeline
```

Create virtual environment

```bash
python -m venv .venv
```

Activate environment

Linux / macOS

```bash
source .venv/bin/activate
```

Windows

```bash
.venv\Scripts\activate
```

Install dependencies

```bash
pip install -r requirements.txt
```

or

```bash
uv sync
```

---

## 🔑 Environment Variables

Create a `.env` file and configure:

```env
AZURE_STORAGE_CONNECTION_STRING=

AZURE_OPENAI_API_KEY=
AZURE_OPENAI_ENDPOINT=
AZURE_OPENAI_API_VERSION=
AZURE_OPENAI_CHAT_DEPLOYMENT=
AZURE_OPENAI_EMBEDDING_DEPLOYMENT=

AZURE_SEARCH_ENDPOINT=
AZURE_SEARCH_API_KEY=
AZURE_SEARCH_INDEX_NAME=

AZURE_VI_NAME=
AZURE_VI_LOCATION=
AZURE_VI_ACCOUNT_ID=
AZURE_SUBSCRIPTION_ID=
AZURE_RESOURCE_GROUP=

APPLICATIONINSIGHTS_CONNECTION_STRING=
```

---

## ▶️ Run the Application

```bash
python main.py
```

or

```bash
uvicorn backend.api.server:app --reload
```

---

## 📡 API Endpoint

### Audit a Video

```
POST /audit
```

Example Request

```json
{
  "video_url": "https://www.youtube.com/watch?v=xxxxxxxx"
}
```

Example Response

```json
{
  "status": "Compliant",
  "violations": [],
  "recommendation": "No issues detected."
}
```

---

## 📈 Future Enhancements

- Human approval workflow
- Multi-language compliance checking
- Brand logo detection
- Face recognition
- Real-time video auditing
- Dashboard for compliance analytics
- Batch video processing
- Confidence score visualization

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to your branch
5. Open a Pull Request

---

## 📜 License

This project is intended for educational and research purposes.

---

## 👨‍💻 Author

**Pranay Rebeyro**

GitHub: https://github.com/Pranayrebeyro

---
