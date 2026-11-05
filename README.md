# DocuMind AI

DocuMind AI is a document question-answering application built with LangChain and Gradio. Upload a document, and the app retrieves relevant sections and uses Google Gemini to generate an answer based only on the uploaded content.

## Features

- Upload a document through a simple Gradio interface
- Convert supported documents to text with MarkItDown
- Split documents into searchable chunks
- Generate embeddings with Sentence Transformers
- Store and retrieve document chunks using ChromaDB
- Generate grounded answers with Google Gemini
- Display the source chunks used for each response

## Tech Stack

- Python
- LangChain
- Hugging Face Sentence Transformers
- ChromaDB
- Google Gemini
- Gradio
- MarkItDown

## Project Structure

```text
RAG_PROJECT-1/
├── DocuMindAi (1).ipynb  # Application notebook
├── requirements.txt       # Python dependencies
└── README.md
```

## Supported Documents

MarkItDown can process several document formats, depending on the installed optional converters. Common examples include PDF, Word (`.docx`), PowerPoint (`.pptx`), Excel (`.xlsx`), and plain text files.

## Prerequisites

- Python 3.10 or later
- A Google AI API key with Gemini API access
- Internet access for downloading the embedding model and calling the Gemini API

## Installation

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows:

```powershell
.venv\Scripts\activate
```

macOS/Linux:

```bash
source .venv/bin/activate
```

3. Install the dependencies:

```bash
python -m pip install -U pip
pip install -r requirements.txt
```

4. Create a `.env` file in the project root:

```env
GOOGLE_API_KEY=your_google_api_key_here
```

Keep this file private. Never commit API keys to GitHub.

## Running the Application

Open the notebook in Jupyter, VS Code, Google Colab, or another notebook environment and run the cells in order:

```bash
jupyter notebook "DocuMindAi (1).ipynb"
```

Running the final UI cell starts a local Gradio app and prints an address such as `http://127.0.0.1:7860`.

## Usage

1. Start the application.
2. Upload a document.
3. Enter a question in the question textbox.
4. Submit the question.
5. Review the answer and retrieved source chunks.

## How It Works

1. MarkItDown converts the uploaded document into text.
2. LangChain splits the text into overlapping chunks.
3. Hugging Face creates vector embeddings for those chunks.
4. ChromaDB stores the vectors locally in `chroma-db/`.
5. The application searches for chunks similar to the user's question.
6. Gemini answers the question using the retrieved context and returns the relevant sources.

## GitHub Setup

Before committing, add a `.gitignore` containing at least:

```gitignore
.env
.venv/
__pycache__/
.ipynb_checkpoints/
chroma-db/
```

Then initialize or update the repository:

```bash
git init
git add .
git commit -m "Initial commit: DocuMind AI"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repository>.git
git push -u origin main
```

## Limitations

- Answers depend on the quality and relevance of retrieved document chunks.
- The notebook keeps the vector store in memory and persists it under `chroma-db/`.
- Model availability and API quotas depend on your Google AI account.
- The embedding model is downloaded on first use and requires sufficient disk space and memory.

## Troubleshooting

- `GOOGLE_API_KEY not found`: confirm that `.env` exists in the project root and contains a valid key.
- `ModuleNotFoundError`: install dependencies with `pip install -r requirements.txt` inside the active virtual environment.
- Gemini model access errors: verify that the selected model is available to your API account.
- Slow first run: the Sentence Transformers embedding model may still be downloading.

## Security

Do not expose API keys in notebook output, source code, or screenshots. Use environment variables or a local `.env` file, and add `.env` to `.gitignore`.

## License

Add a license for this project before publishing it publicly (for example, the MIT License).
