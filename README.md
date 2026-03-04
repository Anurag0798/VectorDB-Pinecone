# VectorDB-Pinecone

This repository demonstrates how to build a vector search system using **Pinecone**, a fully managed vector database service. The project covers embedding generation, vector indexing, and similarity search using Pinecone's Python SDK.

## Setup and Installation

To get started, install the Pinecone client library:

```bash
pip install pinecone
```

## Usage Overview

You can use Pinecone to create and manage vector indexes for similarity search applications. Here's a brief overview of key components:

```python
from pinecone import Pinecone, ServerlessSpec
```

- **Pinecone**: Main client class to interact with the Pinecone vector database.
- **ServerlessSpec**: Configuration class to define serverless index specifications such as dimension, scale, and metadata.

## Key Features

- **Vector Index Creation**: Define and create vector indexes with desired specifications.
- **Embedding Storage**: Store vector embeddings in Pinecone indexes for efficient retrieval.
- **Similarity Search**: Perform fast nearest neighbor searches using query embeddings.
- **Scalable & Managed**: Pinecone handles index scaling and infrastructure.

## Getting Started

1. **Create a Pinecone account** and obtain your API key.

2. **Initialize the Pinecone client** in your Python code:

   ```python
   import pinecone
   from pinecone import Pinecone, ServerlessSpec

   pc = Pinecone(api_key="Your_Pinecone_API_Key")
   ```

3. **Create an index** with desired configuration:

   ```python
   pc.create_index(
      name = INDEX_NAME,
      dimension = EMBEDDING_MODEL_DIMENSION,
      metric = "cosine",
      spec = ServerlessSpec(
        cloud = "aws",
        region = "us-east-1"
      )
   )
   ```
4. **Connecting to an existing index** already created:
   ```python
   index = pc.Index(INDEX_NAME)
   ```

5. **Upsert embeddings** into the index:

   ```python
   index.upsert(vectors=[("id1", embedding_vector1), ("id2", embedding_vector2)])
   ```

6. **Query the index** for similar vectors:

   ```python
   results = index.query(
      vector=query_embedding.tolist(),
      top_k=3,
      include_metadata=True
    )
   ```

## Additional Resources

- [Pinecone Documentation](https://docs.pinecone.io/)

## License

This project is open-source. See the `LICENSE` file for details.