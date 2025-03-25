# RAG-Driven Transaction Analysis (LlamaIndex + OpenAI)

This project focuses on creating a custom RAG using llama index.


## 1. Core Components
### RAG-Driven:
Refers to the Retrieval-Augmented Generation architecture, which combines: 
- Retrieval: Efficiently fetching relevant context from your transaction documents.
- Generation: Using OpenAI’s LLM (e.g., GPT-3.5/4) to synthesize answers from retrieved data.
- Why It Matters: Ensures responses are grounded in your specific dataset, improving accuracy and reducing hallucinations.

### Transaction Analysis:
Focuses on banking/financial transactions (e.g., identifying trends in transaction types, channels, or banks).

- Example Queries Supported:
    - “Which is the most popular bank?”
    - “What’s the most frequent transaction type?”
    - "Which transaction channel has the highest volume?"

### LlamaIndex:
The framework used to:

- Create a vector index from unstructured transaction documents (PDFs, CSVs, etc.).
- Manage persistent storage of the index (via StorageContext) to avoid re-indexing.
- Enable semantic search over transaction data.

### OpenAI:
Provides the LLM (GPT) for:
- Generating human-like answers to user queries.
- Powering embeddings (text-embedding-ada-002) to convert documents/query text into vectors.

## 2. Workflow Summary
My code implements the following RAG pipeline:

#### 1. Data Ingestion:

- Load transaction documents (e.g., bank statements, CSV logs) from the data/ folder.
#### 2. Indexing & Persistence:

- Use LlamaIndex to create a vector store index.
- Save the index to ./storage for reuse (avoids reprocessing).
#### 3. Query Execution:

- For a query like “Most popular banks?”, LlamaIndex retrieves relevant document snippets.
- OpenAI’s LLM synthesizes the final answer from retrieved context.

## 3. Key Benefits Highlighted
### Efficiency:
- Persistent storage (StorageContext) reduces computational overhead by reusing pre-built indexes.
### Accuracy:
- RAG ensures answers are based on your specific transaction data, not generic LLM knowledge.
### Scalability:
- Handles large volumes of transaction documents (e.g., years of bank records).
### Domain-Specific Insights:
- Tailored for banking/finance use cases (e.g., channel popularity, transaction ratios).

## 4. Example Use Cases
### Customer Support Automation:
- Answer FAQs like “What’s the status of my wire transfer?” using transaction logs.

### Compliance Monitoring:
- Identify high-risk transaction patterns (e.g., frequent cross-border transfers).

### Business Intelligence:
- Analyze transaction channel adoption (e.g., mobile vs. in-branch).

## 5. Technical Features
### Persistent Vector Index:
- Avoids re-indexing documents on every run (critical for production-grade systems).
### Semantic Search:
- Understands queries like “transaction source” even if documents use terms like “payment origin”.
### Context-Aware Answers:
- OpenAI’s LLM generates natural-language responses with references to source data.

## 6. Extensions (Future Work)
- Add real-time transaction analysis (e.g., streaming data from APIs).
- Integrate multi-modal data (e.g., scanned PDFs + spreadsheets).
- Build a UI/API layer for business users to interact with the system.
