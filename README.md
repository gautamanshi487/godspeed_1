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

### Running the Application

Start the FastAPI server:

```bash
uvicorn app.main:app --reload
```

The API will be available at `http://localhost:8000`.

## Usage

### Endpoints

* `POST /process-repo/`
  Parameters:

  * `repo_url`: URL of the GitHub repository to clone
  * `branch`: Branch to clone (default: main)

* `POST /query/`
  Parameters:

  * `query`: Text query to search embeddings

### Example

```bash
curl -X POST "http://localhost:8000/process-repo/?repo_url=https://github.com/username/repo&branch=main"
```

## Troubleshooting

* **PermissionError on Windows during repo cleanup**:
  The app uses `shutil.rmtree` with an error handler to delete the cloned repo directory safely. Ensure no files are open or locked by other programs. Run the app with appropriate permissions.

* **Pinecone API Value Error - Invalid `id` length**:
  The vector `id` must be 512 characters or fewer. Check that document IDs generated for embeddings comply with this constraint.

## Contributing

Feel free to open issues or pull requests to improve the project.

## License

MIT License

```

If you want me to save this as a file for you, just say the word!
```
