## Objective:
Develop an advanced search engine algorithm that efficiently retrieves subtitles based on user queries, with a specific emphasis on subtitle content.
The primary goal is to leverage natural language processing and machine learning techniques to enhance the relevance and accuracy of search results.
Step by Step Process

## Part 1: Ingesting Documents
1. Read the given data.
    * Observe that the given data is a database file.
    * Go through the README.txt to understand what is there inside the database.
    * Take care of decoding the files inside the database.
    * If you have limited compute resources, you can take a random 30% of the data.
2. Apply appropriate cleaning steps on subtitle documents (whatever is required)
3. Experiment with the following to generate text vectors of subtitle documents:
    * BOW / TFIDF to generate sparse vector representations. Note that this will only help you to build a **Keyword Based Search Engine**.
    * BERT based “SentenceTransformers” to generate embeddings which encode semantic information. This can help us build a **Semantic Search Engine**.
4. (**Must Implement**) A very important step to improve the performance: Document Chunker.
    * Consider the challenge of embedding large documents: Information Loss.
    * It is often not practical to embed an entire document as a single vector, particularly when dealing with long documents.
    * Solution: Divide a large document into smaller, more manageable chunks for embedding.
    * Another Problem: Let’s say we set the token window to be 500, then we’d expect each chunk to be just below 500 tokens. One common concern of this method is that we might accidentally cut off some important text between chunks, splitting up the context. To mitigate this, we can set overlapping windows with a specified amount of tokens to overlap so we have tokens shared between chunks.
5. Store embeddings in a ChromaDB database. 

## Part 2: Retrieving Documents
1. Take the user's search query.
2. Preprocess the query (if required).
3. Create query embedding.
4. Using cosine distance, calculate the similarity score between embeddings of documents and user search query embedding.
5. These cosine similarity scores will help in returning the most relevant candidate documents as per user’s search query.
