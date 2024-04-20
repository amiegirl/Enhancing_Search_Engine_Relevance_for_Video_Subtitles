# Project Description
Develop an advanced search engine algorithm that efficiently retrieves subtitles content, and provide relevant information based on user queries.
# Objective
The primary goal is to leverage natural language processing and machine learning techniques to enhance the relevance and accuracy of search results.
# Introduction
Search engines have become critical for accessing digital information and providing valuable answers to search queries.
Search engines, such as Google, play a crucial role in the daily lives of people worldwide.<br>
This project utilizes a BERT based Sentence Transformers to generate embeddings creating a Semantic Search Engine. 
The aim is to improve video subtitles accessibility for a wider audience.
With Semantic search, our engine understands the purpose of your search and the meaning of webpages to provide more relevant results.
# Step by Step Processing
## Part 1: Ingesting Documents
* **Reading Data:** Database contains a sample of 82498 subtitle files from [opensubtitles.org](opensubtitles.org). Most of the subtitles are of movies and tv-series which were released after 1990 and before 2024. The Database contains a table called 'zipfiles' with three columns; num: Unique Subtitle ID, name: Subtitle File Name, content: Subtitle content compressed and stored as a binary using 'latin-1' encoding. The subtitle content ware decoded using 'latin-1'. Only 30% samples were taken due to limited computing resources.
* **Data preprocessing:** Appropriate cleaning steps were taken on the retrieved subtitle documents. Timestamps, IDs, HTML tags and special characters were removed from the subtitle document.
* **Document Chunking:** To address information loss, the documents were divided into smaller, more manageable chunks for embedding, as it is often not practical to embed an entire document as a single vector. Using Hugging Face Tokenizer, we used semantic-text-splitter which uses BERT to create chunks.
* **Text vectorization:** Text chunks were converted into a numerical vector representation known as embeddings that is understandable for machine to process. ```all-MiniLM-L6-v2```, a model powered by [Hugging Face Model Hub](https://huggingface.co/models?library=sentence-transformers) was used to create the embeddings. They have been extensively evaluated for their quality to Performance Sentence Embeddings and to embedded search queries & paragraphs (Performance Semantic Search). GPU was used in the embedding to accelerate the processing.
* **Storing the embeddings:** Chroma DB an open-source vector store was used for storing and retrieving vector embeddings. With the help of Chroma DB, metadata and embeddings may be stored to offer more relevant information. When retrieving the embeddings, use this metadata to filter and search across them. 
## Part 2: Retrieving Documents
* The search query is taken as input from the user.
* The query is preprocessed by removing special characters and converting to lower case.
* Query embedding i.e. numerical vector representation are created.
* Using cosine distance, the similarity score between embeddings of documents and user search query embedding is calculated.
* These cosine similarity scores help in returning the most relevant candidate documents as per user’s search query.
# Results

# Conclusion 
The approach attempts to improve video search results' relevance and accuracy, with the potential to enhance accessibility and inclusivity in the video content industry.
