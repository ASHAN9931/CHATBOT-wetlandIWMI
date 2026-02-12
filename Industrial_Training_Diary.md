# Industrial Training Diary - Marsh Warden Project

## Period: 2025.12.08 - 2026.02.13

### 2025.12.08
- Project kickoff for 'Marsh Warden' AI assistant. Defined the scope for wetland conservation policy support in Sri Lanka.

### 2025.12.09
- Requirement gathering and initial data collection of wetland-related policy documents and research papers.

### 2025.12.10
- Setting up the development environment and exploring the structure of the collected PDF documents.

### 2025.12.11
- Implementing basic PDF text extraction using PyMuPDF and exploring initial chunking strategies.

### 2025.12.12
- Researching RAG (Retrieval-Augmented Generation) architectures suitable for legal and policy documents.

### 2025.12.15
- Integrating FAISS for vector storage and implementing the first version of the retrieval pipeline.

### 2025.12.16
- Developing a basic Streamlit UI to interact with the retrieval system.

### 2025.12.17
- Integrating DeepSeek V3.1 via Hugging Face Inference API as the primary LLM.

### 2025.12.18
- Implementing an agentic loop to allow the LLM to use tools for document retrieval.

### 2025.12.19
- Refining the system prompt to ensure hierarchical and citation-backed responses.

### 2025.12.22
- Enhancing PDF extraction to handle complex layouts and preserve document structure.

### 2025.12.23
- Implementing table extraction and merging table data into the RAG context.

### 2025.12.24
- Initial testing of the end-to-end prototype with sample wetland conservation queries.

### 2025.12.29
- Developing the RelevanceChecker class to filter retrieved documents based on similarity thresholds.

### 2025.12.30
- Implementing a Cross-Encoder (MiniLM-L-6-v2) for reranking retrieved chunks to improve precision.

### 2026.01.02
- Experimenting with hybrid retrieval: combining semantic search (FAISS) with keyword search (BM25).

### 2026.01.05
- Improving the chunking strategy by implementing a SemanticChunker that merges adjacent chunks based on embedding similarity.

### 2026.01.06
- Integrating Google Authentication for secure user access to the application.

### 2026.01.07
- Developing chat history persistence, allowing users to save and load previous conversations.

### 2026.01.08
- Implementing chat history archiving and renaming functionality for better management.

### 2026.01.09
- Refactoring the session state management to handle multi-user scenarios and guest mode.

### 2026.01.12
- Developing a custom React-based chat input widget to enhance the user experience.

### 2026.01.13
- Integrating audio transcription capabilities using OpenAI Whisper via Hugging Face API.

### 2026.01.14
- Adding support for audio recording directly within the custom chat widget.

### 2026.01.16
- Implementing token rotation for Hugging Face API to handle rate limits and improve reliability.

### 2026.01.19
- Adding PDF export functionality for users to download their conversation history.

### 2026.01.20
- Enhancing the UI/UX with professional color palettes and dark mode support.

### 2026.01.21
- Optimizing the retrieval pipeline for faster response times and better context relevance.

### 2026.01.22
- Implementing contextual compression at the sentence level within retrieved chunks.

### 2026.01.23
- Conducting comprehensive testing and bug fixing for the authentication and history modules.

### 2026.01.26
- Refining the agent's tool-calling logic to handle ambiguous queries more effectively.

### 2026.01.27
- Adding document-specific query handling to prioritize certain policies when mentioned by the user.

### 2026.01.28
- Enhancing the custom chat widget with dynamic suggestion chips for better user engagement.

### 2026.01.29
- Implementing auto-archiving of conversations and improving the sidebar navigation.

### 2026.01.30
- Finalizing the core features of the Marsh Warden prototype and preparing for the experimental phase.

### 2026.02.02
- Conducting a full system review and performance benchmarking of the current RAG pipeline.

### 2026.02.03
- Finalizing documentation and completing the prototype phase of the industrial training.

### 2026.02.04
- Experimenting with alternative LLMs: Testing Llama 3 and Qwen models to compare their reasoning capabilities for environmental policy.

### 2026.02.05
- Evaluating different libraries for agentic workflows and exploring multi-step reasoning improvements.

### 2026.02.06
- Enhancing the codebase by refactoring the retrieval logic and improving error handling in the agent loop.

### 2026.02.09
- Testing advanced reranking models and experimenting with different embedding models for better semantic capture.

### 2026.02.10
- Improving the custom chat widget with better file upload handling and real-time feedback.

### 2026.02.11
- Conducting experiments with graph-based context representation to better model policy hierarchies.

### 2026.02.12
- Refining the audio transcription pipeline and exploring local Whisper models for reduced latency.

### 2026.02.13
- Final documentation of experimental results and code cleanup for the end of the training period.
