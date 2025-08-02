# Thoughtful AI Customer Support Agent

![UI Screenshot](ui.png)

## Overview

The Thoughtful AI Customer Support Agent is a conversational AI application that answers questions about Thoughtful AI's automation agents (EVA, CAM, PHIL, etc.) using a predefined dataset. It leverages FAISS for vector-based similarity search and falls back to the Groq API (model: llama-3.3-70b-versatile) for unmatched queries. The app features a modern Streamlit-based web interface with secure API key management via .env or Replit Secrets, and robust error handling.

## Features

- **Conversational Interface**: A user-friendly chat UI built with Streamlit
- **Predefined Responses**: Answers questions from a hardcoded JSON dataset about Thoughtful AI's agents
- **Vector Search**: Uses FAISS and SentenceTransformer for efficient question matching
- **Groq Fallback**: Handles unmatched queries with the Groq API
- **Chat History**: Displays conversation history with session persistence
- **Secure Configuration**: Manages the Groq API key via .env (local) or Replit Secrets
- **Error Handling**: Gracefully manages invalid inputs and API errors

## Prerequisites

- **Python**: 3.8–3.12
- **Replit account**: For hosting on Replit (preferred for submission)
- **Groq API key**: From [console.groq.com](https://console.groq.com)
- **Conda**: Recommended for local FAISS installation on Anaconda

## Setup

### Option 1: Replit (Preferred)

#### 1. Create a Python Project

1. Go to [Replit](https://replit.com) and create a new Python project
2. Add the following files:
   - `main.py`: Core application code
   - `requirements.txt`:
     ```
     streamlit
     sentence-transformers
     faiss-cpu==1.7.4
     groq
     python-dotenv
     ```
   - `.replit`:
     ```
     run = "streamlit run main.py --server.port 8000"
     ```
   - `.env.example` (for reference)

#### 2. Configure API Key

1. In Replit's Secrets tab (lock icon), add:
   - **Key**: `GROQ_API_KEY`
   - **Value**: `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`

#### 3. Run the App

1. Click **Run** or use the Replit Shell:
   ```bash
   pip install -r requirements.txt
   streamlit run main.py --server.port 8000
   ```
2. Access the app via the Replit URL (e.g., `https://<your-repl-id>.repl.co`)

### Option 2: Local Setup

#### 1. Set Up Project

1. Create a directory (e.g., `/Users/mercelvubangsi/Documents/GitHub/thoughtaisupport/`)
2. Add `main.py`, `requirements.txt`, and `.env.example` from this project

#### 2. Configure Environment

1. Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   ```
2. Edit `.env`:
   ```
   GROQ_API_KEY=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
   ```
3. Add `.env` to `.gitignore`:
   ```
   .env
   __pycache__/
   *.pyc
   ```

#### 3. Set Up Conda Environment (Recommended for Anaconda)

```bash
conda create -n thoughtai python=3.10
conda activate thoughtai
```

#### 4. Install Dependencies

1. Install FAISS via Conda (preferred for Anaconda):
   ```bash
   conda install -c pytorch faiss-cpu
   ```
2. Install remaining dependencies:
   ```bash
   pip install streamlit sentence-transformers groq python-dotenv
   ```

#### 5. Run the App

```bash
streamlit run main.py
```

Open [http://localhost:8501](http://localhost:8501) in your browser.

## Usage

1. **Access**: Use the Replit URL or `http://localhost:8501` (local)
2. **Ask Questions**: Enter queries about Thoughtful AI's agents (e.g., "What does EVA do?") in the chat input
3. **View Responses**: The app matches questions to the dataset using FAISS. Unmatched queries use the Groq API
4. **Chat History**: Previous messages are displayed in the interface

## Troubleshooting

### FAISS Errors

If you encounter `AttributeError: module 'faiss' has no attribute 'IndexFlatL2'`:

1. **Use Conda for FAISS**:
   ```bash
   conda install -c pytorch faiss-cpu
   ```

2. **Alternative pip installation**:
   ```bash
   pip install faiss-cpu==1.8.0
   ```

3. **Clear conflicting installations**:
   ```bash
   pip uninstall faiss-cpu faiss-gpu -y
   conda remove faiss faiss-cpu faiss-gpu --force
   ```

### Groq API Errors

1. **Invalid Key**: Verify `GROQ_API_KEY` in `.env` or Replit Secrets:
   ```bash
   echo $GROQ_API_KEY  # macOS/Linux
   echo %GROQ_API_KEY%  # Windows
   ```

2. **Module Errors**: Ensure no `groq.py` file exists and groq is installed:
   ```bash
   pip show groq
   pip install --upgrade groq
   ```

### Other Issues

- **.env Issues**: Confirm `.env` is in the project root and `python-dotenv` is installed
- **Dependencies**: Use a clean Conda environment to avoid conflicts:
  ```bash
  conda create -n thoughtai python=3.10
  conda activate thoughtai
  ```
- **Logs**: Check terminal for errors. Ensure an active internet connection for Groq API

## Project Structure

```
thoughtaisupport/
├── main.py              # Core logic with Streamlit UI, FAISS search, and Groq integration
├── requirements.txt     # Python package dependencies
├── .replit             # Replit run configuration
├── .env.example        # Environment variable template (do not commit .env)
├── .gitignore          # Excludes .env, Conda/virtualenv, and cache files
└── README.md           # This file
```

## Evaluation Criteria

- **Functionality**: Accurately handles predefined and fallback queries
- **Code Quality**: Clean, modular code with comments and secure API key management
- **Robustness**: Manages errors and compatibility issues effectively
- **UI**: Professional, user-friendly interface with modern styling and usability features

## Contact

For issues or questions, refer to the Replit/GitHub repository or contact the developer.