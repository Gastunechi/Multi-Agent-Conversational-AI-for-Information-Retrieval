# Multi-Agent-Conversational-AI-for-Information-Retrieval
This project implements a multi-agent conversational system that retrieves information from documents and generates intelligent responses using OpenAI’s GPT-3.5-turbo. It uses ChromaDB to store and search embeddings generated from pre-defined documents. The system is optimized through caching mechanisms and autonomous agents for efficient question-answering tasks.
The documents used for the retrieval process were sourced from the following GitHub repository:
https://github.com/Azure-Samples/azure-search-sample-data/tree/main/nasa-e-book/earth-txt-10

# Table of Contents
-  Project Overview
-  How it works?
-  Technologies Used
-  Features
-  Installation
-  Usage
-  How It Works
-  Future Improvements
-  Contributing
-  License

# Project Overview
This project demonstrates how to build a question-answering system using multiple agents. The system retrieves information from documents (in this case, text files related to NASA publications) and responds to questions posed by the user. It utilizes pre-trained language models to encode and search the documents in a vector database, leveraging ChromaDB for efficient retrieval.

The project is built with a focus on scalability, agent-based architecture, and performance optimization using disk-based caching.

# How it works?
The following diagram illustrates the workflow of the multi-agent system:

![Workflow Diagram](https://github.com/Gastunechi/Multi-Agent-Conversational-AI-for-Information-Retrieval/blob/main/workflow.jpg)

- **Data Sources**: The system retrieves data from various documents.
- **Chunking**: The data is divided into smaller pieces for efficient processing.
- **Embedding Model**: These chunks are converted into vector embeddings using a pre-trained model.
- **Vector Database**: The embeddings are stored in a vector database for fast similarity searches.
- **User Prompt**: The user's query is processed and compared to the embeddings in the vector database.
- **Similarity Search**: The most relevant document chunks are retrieved based on similarity to the user’s query.
- **LLM**: The retrieved information, combined with the user’s query, is passed to a large language model to generate a relevant answer.
Astuce :



# Technologies Used
-  Python: Primary programming language.
-  OpenAI GPT-3.5-turbo: For generating intelligent, context-based answers.
-  ChromaDB: Vector database used to store and search embeddings.
-  Sentence Transformers: Pre-trained models to encode sentences into embeddings (all-mpnet-base-v2).
-  Autogen: To manage and create the conversational agents.
-  Google Colab: For running the notebook and accessing API keys.
-  pypdf: For extracting text from PDF documents.
-  Markdownify: For converting content to markdown format.
-  Cache-based optimization: To improve performance and prevent re-running repetitive tasks.

# Features
-  Multi-Agent Architecture: Agents communicate to retrieve information and answer user queries autonomously.
-  Persistent Vector Database: Stores embeddings for efficient document search using ChromaDB.
-  Question-Answer System: Generates answers to user questions by searching embedded documents.
-  Autonomous Operation: Once initialized, agents work independently to complete tasks.
-  Caching: Disk-based caching optimizes repeated operations by storing results.

# Installation
Clone the repository:

```bash
Copy code
git clone https://github.com/yourusername/multi-agent-qa-retrieval.git
cd multi-agent-qa-retrieval
```

Install required dependencies: You can install the necessary Python packages with the following command:
```bash
Copy code
pip install pyautogen sentence_transformers markdownify pypdf chromadb==0.5.0
```

Configure OpenAI API Key: You will need an OpenAI API key to use GPT-3.5-turbo. In the project, the API key is retrieved from Google Colab’s userdata:

```python
Copy code
"api_key": userdata.get('OPENAI_API_KEY')
```

You can replace this line with your own key or configure Colab to use your key.

# Usage
-  Open the notebook: Load the project notebook in Google Colab or any Jupyter environment.

-  Run the code: Execute the cells in the notebook to set up the environment and the agents.

-  Ask a question: The agents are ready to retrieve information and respond to your query. For example:

```python
query = "What is the impact of volcanic eruptions on cloud formation?"
```

-  Inspect the results: The agents will search the documents and return the most relevant responses, optimized by caching.

# How It Works
-  Agent System: The project uses two main agents:

  - RetrieveUserProxyAgent: Represents the user and retrieves data from the document set.
  -  RetrieveAssistantAgent: Acts as the assistant that interacts with the documents and the vector database.
-  Document Embedding: The documents are embedded into vectors using all-mpnet-base-v2. These embeddings are stored in ChromaDB for efficient retrieval.

-  Query Execution: The user’s query is transformed into embeddings and matched against the document embeddings stored in the vector database to find relevant information.

-  Response Generation: Once the most relevant document segments are retrieved, GPT-3.5-turbo generates a well-formatted response based on the content.


# Future Improvements
Add a user interface to make the system more interactive and user-friendly.
Extend document support to include other file formats such as .pdf or .docx.
Improve the variety and complexity of questions the agents can handle.
Implement a real-time chat interface for continuous conversation.

# Contributing
If you want to contribute to this project, feel free to fork the repository and submit a pull request. You can also open issues for any bugs or feature requests.

# License
This project is licensed under the MIT License. See the LICENSE file for more information.
