# Industrial Training Diary: Wetland Chatbot Development (Marsh Warden)
**Organization:** International Water Management Institute (IWMI)
**Project:** Marsh Warden - Wetland Information & Conservation Policy Support Assistant
**Duration:** 2025.12.08 – 2026.02.04

---

### Week 1: Foundation and Environment Setup (Dec 08 – Dec 12)

**2025.12.08**
* Attended the orientation program at the International Water Management Institute (IWMI).
* Met with the project supervisor to define the objectives of the "Marsh Warden" AI assistant.
* Discussed the importance of wetland conservation and the need for a policy-aware chatbot.

**2025.12.09**
* Conducted extensive research on Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG).
* Evaluated different framework options including LangChain and Streamlit for rapid prototyping.
* Explored existing AI solutions in the environmental conservation domain.

**2025.12.10**
* Finalized the project scope, focusing on a specialized assistant for Sri Lankan wetland policies.
* Identified the key target users: policymakers, researchers, and conservation officers.
* Documented the high-level technical requirements for the chatbot's retrieval engine.

**2025.12.11**
* Evaluated various PDF processing libraries to handle complex government policy documents.
* Selected PyMuPDF (fitz) due to its superior performance in layout analysis and text extraction.
* Researched techniques for handling non-standard characters and multi-column layouts in PDFs.

**2025.12.12**
* Initialized the development environment and configured the Python virtual environment.
* Set up the project repository on GitHub with an appropriate directory structure.
* Established version control workflows and initial project documentation.

---

### Week 2: Data Acquisition and PDF Extraction (Dec 15 – Dec 19)

**2025.12.15**
* Commenced the implementation of the `PDFExtractor` class to automate document ingestion.
* Developed the core logic for reading PDF files and iterating through pages efficiently.
* Integrated basic text cleaning routines to remove unnecessary whitespace and artifacts.

**2025.12.16**
* Implemented layout-aware extraction to identify and exclude headers, footers, and page numbers.
* Refined the margin detection algorithm to prevent noise from interfering with the core content.
* Enhanced the extractor to preserve the reading order of text blocks in multi-column documents.

**2025.12.17**
* Developed specialized logic for table extraction using the `page.find_tables()` method in PyMuPDF.
* Implemented a conversion routine to transform extracted tables into Markdown and Pandas DataFrames.
* Tested table extraction on complex regulatory schedules and environmental data tables.

**2025.12.18**
* Enhanced the content categorization logic to distinguish between headings, paragraphs, and tables.
* Implemented font size analysis to automatically detect hierarchical headings within the text.
* Added support for merging fragmented text blocks that belong to the same logical paragraph.

**2025.12.19**
* Conducted comprehensive testing of the extraction pipeline on a diverse set of wetland policy documents.
* Resolved issues related to character encoding and special symbols common in legal texts.
* Optimized the extraction speed by implementing batch processing for large document sets.

---

### Week 3: Core RAG - Processing and Semantic Chunking (Dec 22 – Dec 26)

**2025.12.22**
* Researched advanced chunking strategies to maintain context in long legal and policy documents.
* Evaluated the limitations of fixed-size chunking and explored semantic alternatives.
* Studied the impact of chunk overlap on retrieval accuracy and context window utilization.

**2025.12.23**
* Implemented the `SemanticChunker` class using SentenceTransformers for intelligent text splitting.
* Developed logic to merge adjacent text blocks based on their embedding similarity.
* Configured the chunker to respect logical boundaries such as headings and table endings.

**2025.12.24**
* Refined the text normalization pipeline to handle inconsistencies in punctuation and formatting.
* Implemented a cleaning layer to remove OCR errors and non-printable characters.
* Developed a routine to normalize technical terms and acronyms common in wetland conservation.

**2025.12.25**
* Defined a robust metadata schema for each document chunk to ensure accurate source attribution.
* Included fields for source filename, page number, content type, and hierarchical context.
* Integrated the metadata generation logic into the main processing pipeline.

**2025.12.26**
* Conducted benchmarking of different semantic similarity thresholds for the chunking process.
* Optimized the base chunk size and overlap parameters for the "BAAI/bge-base-en-v1.5" embedding model.
* Verified the quality of the generated chunks through manual review of sample outputs.

---

### Week 4: Core RAG - Indexing and Hybrid Retrieval (Dec 29 – Jan 02)

**2025.12.29**
* Integrated the FAISS (Facebook AI Similarity Search) library for high-performance vector storage.
* Developed the indexing pipeline to convert document chunks into embeddings and store them in FAISS.
* Implemented persistence logic to save and load the vector index from disk.

**2025.12.30**
* Implemented a BM25-based retriever to provide keyword-centric search capabilities.
* Configured the BM25 algorithm to handle the specific vocabulary used in environmental legislation.
* Tested the keyword retriever's effectiveness in finding specific acts and regulatory sections.

**2025.12.31**
* Developed the `EnsembleRetriever` to combine vector search and BM25 results.
* Implemented a weighted ranking system to balance semantic relevance and keyword matches.
* Conducted initial tests on the hybrid retrieval engine using a set of common policy questions.

**2026.01.01**
* Designed the unified `RAGPipeline` class to manage the entire flow from query to retrieval.
* Integrated the indexing, storage, and retrieval components into a cohesive API.
* Added logging and error-handling mechanisms to the pipeline for better observability.

**2026.01.02**
* Evaluated the performance of hybrid retrieval against pure vector and pure keyword search.
* Optimized the ensemble weights (0.85 for FAISS, 0.15 for BM25) based on retrieval precision.
* Refined the top-k selection logic to ensure a balanced set of context chunks.

---

### Week 5: Advanced Retrieval and Relevance Reranking (Jan 05 – Jan 09)

**2026.01.05**
* Researched reranking models to improve the precision of the retrieval results.
* Evaluated various CrossEncoder models and their computational trade-offs for a prototype.
* Selected the `ms-marco-MiniLM-L-6-v2` model for its balance of speed and accuracy.

**2026.01.06**
* Implemented the `RelevanceChecker` class to perform secondary scoring of retrieved documents.
* Integrated the CrossEncoder model into the retrieval pipeline to re-rank the initial results.
* Developed logic to filter out chunks that fall below a specific relevance threshold.

**2026.01.07**
* Enhanced the `RelevanceChecker` with a min/max normalization routine for scores.
* Implemented a fallback mechanism to use cosine similarity if the CrossEncoder fails.
* Optimized the reranking process by implementing batch scoring for retrieved chunks.

**2026.01.08**
* Developed a contextual compression mechanism to prune irrelevant sentences within a chunk.
* Implemented a sentence-level similarity check to keep only the most relevant parts of the text.
* Reduced the total token count of the context without losing critical information.

**2026.01.09**
* Conducted end-to-end testing of the advanced retrieval pipeline with complex queries.
* Verified that the reranker successfully prioritized the most relevant legal clauses.
* Fine-tuned the threshold parameters to achieve the optimal balance between recall and precision.

---

### Week 6: LLM Integration and Agent Logic (Jan 12 – Jan 16)

**2026.01.12**
* Evaluated the DeepSeek V3.1 model for its reasoning capabilities and support for long contexts.
* Researched the Hugging Face Inference API for cost-effective model deployment.
* Defined the system prompt to guide the LLM in providing professional and citation-backed answers.

**2026.01.13**
* Implemented the LLM integration layer using the OpenAI-compatible API on Hugging Face.
* Developed robust error-handling and retry logic for API requests.
* Configured the model parameters (temperature, max tokens) for consistent policy analysis.

**2026.01.14**
* Developed the agentic loop with tool-calling capabilities using the DeepSeek model.
* Defined the `retrieve_documents` tool to allow the agent to fetch context when needed.
* Implemented logic to handle multi-step reasoning where the agent may perform multiple retrievals.

**2026.01.15**
* Created the `token_manager.py` module to handle automatic rotation of Hugging Face API tokens.
* Implemented a round-robin rotation strategy to circumvent rate limits and ensure high availability.
* Added monitoring for token health and remaining quota.

**2026.01.16**
* Conducted extensive prompt engineering to enforce a strict response structure (Hierarchy, Guidance, Citations).
* Implemented logic to handle cases where the required information is not found in the documents.
* Verified the agent's ability to cite specific document sections and pages accurately.

---

### Week 7: Frontend Development - Part 1 (Jan 19 – Jan 23)

**2026.01.19**
* Designed the layout of the Streamlit application, focusing on a dashboard-like experience.
* Established the color palette (Teal and Cyan) and typography for the "Marsh Warden" brand.
* Created the sidebar structure for model selection, session info, and chat management.

**2026.01.20**
* Implemented extensive custom CSS to enhance the default Streamlit UI.
* Developed a responsive header section with a custom image slideshow.
* Styled the chat message bubbles to distinguish between user and assistant responses clearly.

**2026.01.21**
* Integrated Google OAuth authentication to ensure secure access to the chatbot.
* Implemented user profile cards in the sidebar to display logged-in user information.
* Developed a guest mode accessible via specific URL parameters for easy demonstration.

**2026.01.22**
* Implemented session state management to preserve chat history during the session.
* Developed logic to automatically save and load chat history from JSON files.
* Added a theme toggle feature to allow users to switch between light and dark modes.

**2026.01.23**
* Built the core chat interface components and integrated the agentic RAG pipeline.
* Implemented a "View Sources" expander to display the exact document chunks used for each answer.
* Added a "New Chat" and "Clear History" functionality to the management panel.

---

### Week 8: Frontend Development - Part 2 (Jan 26 – Jan 30)

**2026.01.26**
* Set up a dedicated React development environment for building custom Streamlit components.
* Initialized the `Chat_input_widget` project using a TypeScript and Tailwind CSS stack.
* Configured the build pipeline to generate artifacts compatible with the Streamlit frontend.

**2026.01.27**
* Developed the custom `chat_input_widget` with a focus on modern UX and accessibility.
* Implemented an audio recording feature using the MediaRecorder API.
* Added support for dynamic suggestions that appear above the input field.

**2026.01.28**
* Integrated the custom React widget into the main Streamlit application.
* Implemented the communication bridge between the React component and the Python backend.
* Resolved styling conflicts between the custom widget and the Streamlit global styles.

**2026.01.29**
* Enhanced the chat history management system with archiving and renaming capabilities.
* Implemented a persistent storage mechanism for past conversations using a structured directory.
* Added a feature to restore past conversations with full context and citations.

**2026.01.30**
* Integrated the Whisper-large-v3 model for high-accuracy audio transcription.
* Developed a seamless workflow for processing voice queries from the custom input widget.
* Added visual feedback and status indicators for the transcription process.

---

### Week 9: Finalization and Deployment (Feb 02 – Feb 04)

**2026.02.02**
* Implemented a PDF export feature using the FPDF library for conversation logging.
* Developed logic to clean and format chat content for professional-looking PDF reports.
* Integrated the download button into the custom chat input widget.

**2026.02.03**
* Performed comprehensive system testing and resolved minor UI inconsistencies.
* Optimized the application's startup time by caching the RAG pipeline and indices.
* Conducted a final review of the assistant's accuracy against a suite of benchmark questions.

**2026.02.04**
* Completed the documentation for the "Marsh Warden" prototype, including setup and usage guides.
* Prepared the final presentation and demonstration for the IWMI research team.
* Delivered the completed prototype and transitioned the repository for further internal evaluation.
