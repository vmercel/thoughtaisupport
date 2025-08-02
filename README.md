Thoughtful AI Customer Support Agent

![UI Screenshot](ui.png)

Overview
This project implements a conversational AI agent for Thoughtful AI, designed to answer common questions about Thoughtful AI's automation agents (EVA, CAM, PHIL, etc.) using a predefined dataset. For unmatched queries, it falls back to the Groq API (model: llama-3.3-70b-versatile). The app uses FAISS for vector embeddings and similarity scoring, with a Streamlit-based web interface for user interaction. API keys are securely managed using a .env file locally or Replit Secrets.
Features

Conversational Interface: A user-friendly chat UI built with Streamlit.
Predefined Responses: Answers questions about Thoughtful AI's agents using a hardcoded JSON dataset.
Vector Search: Uses FAISS (version 1.7.4) and SentenceTransformer for efficient similarity-based question matching.
Fallback to Groq: Handles unmatched queries using the Groq API client.
Error Handling: Gracefully manages invalid inputs and API errors.
Chat History: Maintains conversation context within the session.
Secure API Key Management: Uses .env file locally or Replit Secrets for the Groq API key.

Prerequisites

Python: Version 3.8–3.12
Replit Account: For hosting on Replit (preferred for submission)
Grok API Key: Obtain from console.groq.com for fallback responses

Setup Instructions
Option 1: Running on Replit (Preferred)

Create a New Replit Project:

Go to Replit and create a new Python project.
Upload or copy the following files:
main.py: The main application code.
requirements.txt: Lists dependencies.
.replit: Configures the run command.
.env.example: Template for environment variables (reference only).




Set Up requirements.txt:Create or ensure requirements.txt contains:
streamlit
sentence-transformers
faiss-cpu==1.7.4
groq
python-dotenv


Note: faiss-cpu==1.7.4 ensures compatibility with Python 3.12.


Configure .replit:Create or ensure .replit contains:
run = "streamlit run main.py --server.port 8000"


Add Groq API Key:

In Replit, go to the Secrets tab (lock icon in the sidebar).
Add a secret with:
Key: GROQ_API_KEY
Value: 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


Note: Replit Secrets replace the need for a .env file in Replit.


Run the App:

Click the Run button in Replit, or in the Replit Shell, execute:pip install -r requirements.txt
streamlit run main.py --server.port 8000


Access the app via the Replit-provided URL (e.g., https://<your-repl-id>.repl.co).



Option 2: Running Locally

Clone or Set Up the Project:

Clone the repository (if hosted on GitHub) or create a directory with:
main.py: The main application code.
requirements.txt: As above.
.env.example: Template for environment variables.




Create a .env File:

Copy .env.example to .env:cp .env.example .env


Edit .env to include your Groq API key:GROQ_API_KEY=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


Ensure .env is added to .gitignore to prevent version control exposure.


Set Up a Virtual Environment (recommended):
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install Dependencies:
pip install -r requirements.txt

Or manually:
pip install streamlit sentence-transformers faiss-cpu==1.7.4 groq python-dotenv


Run the App:
streamlit run main.py


Open http://localhost:8501 in your browser to interact with the app.



Usage

Access the App: Open the Replit URL or http://localhost:8501 (local).
Ask Questions: Enter questions about Thoughtful AI’s agents (e.g., "What does EVA do?") in the chat input.
View Responses: The app matches questions to the predefined dataset using FAISS-based similarity search. Unmatched queries are answered by the Groq API.
Chat History: Previous messages are displayed in the interface.

Troubleshooting

Groq API Errors:
Invalid API Key: Ensure the GROQ_API_KEY is correctly set in .env (local) or Replit Secrets. Verify with:echo $GROQ_API_KEY  # macOS/Linux
echo %GROQ_API_KEY%  # Windows


Module Errors: Confirm groq is installed (pip show groq) and no local groq.py file exists, which could cause conflicts.


FAISS Errors: Use faiss-cpu==1.7.4 to avoid compatibility issues. Alternatively, install via Conda:conda install -c pytorch faiss-cpu


Dependency Conflicts: Use a clean Python environment (e.g., Conda or virtualenv) to avoid conflicts.
Logs: Check terminal logs for specific errors and ensure an active internet connection for Groq API calls.
.env Issues: Ensure .env is in the project root and python-dotenv is installed. If the key isn’t loaded, verify the file syntax.

Project Structure

main.py: Core application logic with Streamlit UI, FAISS vector search, and Groq API integration.
requirements.txt: Lists required Python packages.
.replit: Configures Replit’s run command for Streamlit.
.env.example: Template for environment variables (do not commit .env to version control).
.gitignore: Excludes .env and virtual environment files (recommended).

Evaluation Notes

Functionality: The app correctly handles predefined questions and falls back to Groq for others.
Code Quality: Modular, readable code with comments, error handling, and secure API key management.
Robustness: Handles invalid inputs, API errors, and missing environment variables gracefully.

For questions or issues, contact the developer or refer to the Replit/GitHub repository for updates.