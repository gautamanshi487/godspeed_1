# Usage

To use this sample repository with the RAG (Retrieval-Augmented Generation) application, follow these steps:

## 1. Process a GitHub Repository

Send a POST request to the `/process-repo/` endpoint with the URL of the GitHub repository you want to process. You can optionally include a branch name.

Example:
```bash
POST /process-repo/?repo_url=https://github.com/your-org/your-repo&branch=main
```

This will:
- Clone the repository
- Extract and embed textual data
- Store the embeddings in the vector database

## 2. Query the Embedded Documents

Once the documents are processed and indexed, send a POST request to the `/query/` endpoint with your search query.

Example:
```bash
POST /query/
{
  "query": "How does the login system work?"
}
```

This will:
- Search the embedded content for semantically relevant results
- Return matching documents and snippets

---

This enables quick and intelligent access to large codebases or documentation using natural language queries.
