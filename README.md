# Report Analyzer

<p align="center">
  <em>An AI-powered personal health insights agent.</em>
</p>

## Overview
**Report Analyzer** allows users to upload medical blood reports in PDF format, performs a detailed AI analysis of the results, and provides a RAG-based (Retrieval-Augmented Generation) chat interface for follow-up questions. It uses a tiered AI model approach to provide insights securely and efficiently.

## Key Features
- **Secure Authentication**: Integration with Supabase Auth for safe user logins and session management.
- **Automated PDF Extraction**: Seamlessly extracts text from medical PDFs using `pdfplumber`.
- **Intelligent AI Analysis**: Contextual, tiered model hierarchy (Groq/Llama) for robust health insights.
- **Interactive RAG Chat**: Chatbot that understands the context of the analyzed report using HuggingFace Embeddings and FAISS.
- **Rate Limiting**: Daily analysis limits to manage resource consumption effectively.

## Tech Stack
- **Frontend**: [Streamlit](https://streamlit.io/)
- **Backend & Database**: [Supabase](https://supabase.com/) (Auth, PostgreSQL, Storage)
- **AI Inference Engine**: [Groq](https://groq.com/) (Fast LLM inference)
- **RAG / Embeddings**: FAISS & HuggingFace (`all-MiniLM-L6-v2`) via LangChain
- **Document Processing**: `pdfplumber`

## Getting Started

### Prerequisites
Make sure you have following installed:
- Python 3.9+
- Pip
- A Supabase Project (with Auth and standard setup)
- A Groq API Key

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository_url>
   cd "Report Analyzer"
   ```

2. **Set up a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Environment Variables:**
   Create a `.streamlit/secrets.toml` file in the root directory and add your keys:
   ```toml
   SUPABASE_URL = "your_supabase_url"
   SUPABASE_KEY = "your_supabase_anon_key"
   GROQ_API_KEY = "your_groq_api_key"
   ```

5. **Run the application:**
   ```bash
   streamlit run src/main.py
   ```

## Architecture & Flow

For a deeper dive into the technical implementation, system architecture, component breakdown, and detailed data flow diagrams, please refer to our [Technical Documentation](TECHNICAL_DOCS.md).

## License
This project is licensed under the MIT License.
