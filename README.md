# rag-multi-agent-langgraph
RAG mediated Multi Agent Orchestration for regulatory compliance reporting using LangGraph

PDF Loading:
The script uses the PyPDFLoader from LangChain to load all PDFs from the ./fatca_regulations/ directory. The texts extracted from these PDFs become the corpus for your compliance data.

Vector Store Setup:
The extracted documents are embedded using an OpenAI model and stored in a ChromaDB collection named "fatca_collection". This allows fast similarity search via the RetrievalQA chain.

Agent Pipeline:

Compliance Agent: Retrieves relevant FATCA information from the vector store.
Collaborative Synthesis Agent: Simulates two synthesis sub-agents that exchange messages (using the retrieved compliance data) and produce a refined synthesis.
Supervisor Agent: Aggregates the outputs from the Compliance and Synthesis agents, merging and selecting the final output.
Report Agent: Formats the aggregated output into a detailed analyst report.
Graph Orchestration:
LangGraph defines the data flow (edges) between nodes, ensuring that the outputs are passed along in the correct sequence.
