# RAG
* Used Llama3 Langchain and ChromaDB to create a Retrieval Augmented Generation (RAG) system. This will allow us to ask questions about our documents (that were not included in the training data), without fine-tunning the Large Language Model (LLM).
* When using RAG, if you are given a question, you first do a retrieval step to fetch any relevant documents from a special database, a vector database where these documents were indexed.

# What is a Retrieval Augmented Generation (RAG) system?

* Large Language Models (LLMs) has proven their ability to understand context and provide accurate answers to various NLP tasks, including summarization, Q&A, when prompted. While being able to provide very good answers to questions about information that they were trained with, they tend to hallucinate when the topic is about information that they do "not know", i.e. was not included in their training data. Retrieval Augmented Generation combines external resources with LLMs. The main two components of a RAG are therefore a retriever and a generator.

* The retriever part can be described as a system that is able to encode our data so that can be easily retrieved the relevant parts of it upon queriying it. The encoding is done using text embeddings, i.e. a model trained to create a vector representation of the information. The best option for implementing a retriever is a vector database. As vector database, there are multiple options, both open source or commercial products. Few examples are ChromaDB, Mevius, FAISS, Pinecone, Weaviate. Our option in this Notebook will be a local instance of ChromaDB (persistent).

* For the generator part, the obvious option is a LLM. In this Notebook we will use a quantized Llama3 model, from the Kaggle Models collection.

* The orchestration of the retriever and generator will be done using Langchain. A specialized function from Langchain allows us to create the receiver-generator in one line of code.
