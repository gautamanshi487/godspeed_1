# godspeed_1

This repository provides a FastAPI-based service that clones a GitHub repository, extracts and processes its files, generates embeddings using BERT, and upserts them to Pinecone for vector search.

## Features

- Clone and extract all files from a specified GitHub repository and branch.
- Generate document embeddings using a BERT model.
- Store and search embeddings efficiently using Pinecone vector database.
- FastAPI backend with endpoints for processing repositories and querying.

## Setup and Installation

### Prerequisites

- Python 3.8 or higher
- Git installed and accessible in your PATH
- Pinecone account and API key
- Install required Python packages:

```bash
pip install -r requirements.txt
````

### Environment Variables

Create a `.env` file or set the following environment variables:

* `PINECONE_API_KEY` - Your Pinecone API key
* `PINECONE_ENV` - Pinecone environment (e.g., `us-west1-gcp`)
* `PINECONE_INDEX_NAME` - Name of your Pinecone index

## Technologies Used
- FastAPI
- Pinecone
- BERT Embeddings (SentenceTransformers)
- GitPython

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/yourrepo.git
   cd yourrepo
   ```

2. Create and activate a virtual environment:
   ```powershell
   Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned

   .\venv\Scripts\Activate.ps1
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the FastAPI app:
   ```bash
   python -m app.main
   ```

5. Visit the interactive API docs:
   - Open: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

## Usage

### Endpoints

* `POST /process-repo/`
  Parameters:

  * `repo_url`: URL of the GitHub repository to clone
  * `branch`: Branch to clone (default: main)

* `POST /query/`
  Parameters:

  * `query`: Query the vector store
### Example

```bash
curl -X POST "http://localhost:8000/process-repo/?repo_url=https://github.com/username/repo&branch=main"
```

## Contributing

Feel free to open issues or pull requests to improve the project.

## License
This project is licensed under the MIT License.

