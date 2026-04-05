# CST8921 – Cloud Industry Trends

## Lab 11 – Set Up Azure AI Search Index and Deploy Embedding & LLM Models

**St: Olga Durham**

**St#: 040687883**

---

### Step 1 - Create the Azure resources

- Resource Group: `rg-ai-search-lab`, `Canada Central`
- Azure AI Search service: `srch-rag-lab-shap0011`, `Basic`
- Azure OpenAI resource: `aoai-rag-lab-shap0011`
- Storage Account: `stsearchlabfilesshap0011`, blob container `documents`

- Search service name: `srch-rag-lab-shap0011`
- Search endpoint: `https://srch-rag-lab-shap0011.search.windows.net`
- Search admin key: `[SearchAdminKey](/keys.txt)`
- OpenAI endpoint: `https://aoai-rag-lab-shap0011.openai.azure.com/`
- OpenAI key: `[OpenAIKey](/keys.txt)`
- Storage account name: `stsearchlabfilesshap0011`

### Step 2 - Deploy the embedding and chat models

- Embedding deployment: `text-embedding-3-small`
- Chat deployment: `gpt-4o`

AZURE_OPENAI_ENDPOINT=https://aoai-rag-lab-shap0011.openai.azure.com/
AZURE_OPENAI_API_KEY=your-key-here
EMBEDDING_MODEL_DEPLOYMENT=text-embedding-3-small
CHAT_MODEL_DEPLOYMENT=gpt-4o

### Step 3 (Part 1): Upload HR files to Blob Storage

Storage account: `stsearchlabfilesshap0011`
Container: `documents`

Upload all 3 files from the local repo:

`vacation-policy.txt`
`remote-work-policy.txt`
`benefits-overview.txt`

### Step 3 (Part 2): Connect Blob Storage to Azure AI Search

![Indexed HR documents](./screenshots/1-indexed-hr-documents.png)

Figure 1: Indexed HR documents

![Successful indexer execution](./screenshots/2-successful-indexer-execution.png)

Figure 2: Successful indexer execution

![Keyword search results](./screenshots/3-keyword-search-baseline.png)

Figure 3: Keyword search results

![Semantic search AI understanding](./screenshots/4-semantic-search-ai-understanding.png)

Figure 4: Semantic search AI understanding

![Hybrid keyword semantic vector](./screenshots/5-hybrid-keyword-semantic-vector.png)

Figure 5: Hybrid keyword semantic vector
