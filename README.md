# CST8921 – Cloud Industry Trends

## Lab 11 – Set Up Azure AI Search Index and Deploy Embedding & LLM Models

**St: Olga Durham**

**St#: 040687883**

---

### Introduction

This lab demonstrates how to build a Retrieval-Augmented Generation (RAG) solution using Azure AI Search and Azure OpenAI. The system ingests HR policy documents, generates vector embeddings, and enables both keyword and AI-powered semantic search.

---

## Architecture Overview

The solution consists of:

- **Azure Blob Storage** → stores HR documents
- **Azure AI Search** → indexes and retrieves data
- **Azure OpenAI** → generates embeddings and AI responses

This pipeline enables intelligent search and question answering over unstructured data.

---

### Step 1 - Create the Azure resources

- Resource Group: `rg-ai-search-lab`, `Canada Central`
- Azure AI Search service: `srch-rag-lab-shap0011`, `Basic`
- Azure OpenAI resource: `aoai-rag-lab-shap0011`
- Storage Account: `stsearchlabfilesshap0011`, blob container `documents`

#### Configuration Details

- Search service name: `srch-rag-lab-shap0011`
- Search endpoint: `https://srch-rag-lab-shap0011.search.windows.net`
- Search admin key: stored securely in `/keys.txt`
- OpenAI endpoint: `https://aoai-rag-lab-shap0011.openai.azure.com/`
- OpenAI key: stored securely in `/keys.txt`

---

### Step 2 - Deploy Models

- Embedding deployment: `text-embedding-3-small`
- Chat deployment: `gpt-4o`

```
AZURE_OPENAI_ENDPOINT=https://aoai-rag-lab-shap0011.openai.azure.com/
AZURE_OPENAI_API_KEY=your-key-here
EMBEDDING_MODEL_DEPLOYMENT=text-embedding-3-small
CHAT_MODEL_DEPLOYMENT=gpt-4o
```

---

### Step 3: Upload HR Documents

Storage account: `stsearchlabfilesshap0011`
Container: `documents`

Uploaded files:

- `vacation-policy.txt`
- `remote-work-policy.txt`
- `benefits-overview.txt`

---

### Step 4: Connect Blob Storage to Azure AI Search

#### Results

![Azure AI Search index successfully populated with HR documents](./screenshots/1-indexed-hr-documents.png)

Figure 1: Azure AI Search index successfully populated with HR documents

![Successful execution of the indexer pipeline](./screenshots/2-successful-indexer-execution.png)

Figure 2: Successful execution of the indexer pipeline

![Keyword-based search results for the query "vacation"](./screenshots/3-keyword-search-baseline.png)

Figure 3: Keyword-based search results for the query "vacation"

![Semantic search with extractive answer for a natural language query](./screenshots/4-semantic-search-ai-understanding.png)

Figure 4: Semantic search with extractive answer for a natural language query

![Hybrid search combining keyword, vector, and semantic ranking](./screenshots/5-hybrid-keyword-semantic-vector.png)

Figure 5: Hybrid search combining keyword, vector, and semantic ranking

![Semantic search result answering a natural language question about the remote work policy](./screenshots/6-work-from-home-policy.png)

Figure 6: Semantic search result answering a natural language question about the remote work policy

---

### Analysis: Keyword vs Semantic vs Hybrid Search

**Keyword search** retrieves results based on exact term matching. While effective for simple queries, it returns raw document content and requires manual interpretation.

**Semantic search** improves retrieval by understanding the intent of natural language queries. It provides extractive answers directly from the documents, improving usability and accuracy.

**Hybrid search** combines keyword matching, vector embeddings, and semantic ranking. This approach delivers the most relevant and context-aware results, making it the most effective method for information retrieval in this solution.

---

### Conclusion

This lab successfully demonstrated how to build a RAG-based search solution using Azure services. By integrating Azure AI Search with Azure OpenAI, it is possible to transform static documents into an intelligent system capable of answering user questions with high accuracy and relevance.

---
