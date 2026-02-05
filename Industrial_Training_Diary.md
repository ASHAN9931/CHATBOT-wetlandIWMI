# Industrial Training Diary: Wetland Chatbot Development (Marsh Warden)
**Organization:** International Water Management Institute (IWMI)
**Project:** Marsh Warden - Wetland Information & Conservation Policy Support Assistant
**Duration:** 2025.12.08 – 2026.02.04

---

### Week 1: Foundation and Environment Setup (Dec 08 – Dec 12)

**2025.12.08**
* Attended the orientation program at the International Water Management Institute (IWMI).
* Met with the project supervisor to define the objectives of the "Marsh Warden" AI assistant.
* Discussed the critical role of wetlands and the necessity for an AI-driven policy support tool.

**2025.12.09**
* Conducted comprehensive research on Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG).
* Evaluated development frameworks, comparing LangChain and Streamlit for rapid prototyping.
* Analyzed existing digital solutions in the environmental and conservation sectors.

**2025.12.10**
* Finalized the project scope, prioritizing the analysis of Sri Lankan wetland conservation policies.
* Identified the primary stakeholder groups: policymakers, researchers, and field conservation officers.
* Defined the high-level technical architecture for the chatbot’s retrieval engine.

**2025.12.11**
* Evaluated PDF processing libraries for handling complex, multi-column government documents.
* Selected PyMuPDF (fitz) due to its efficient layout analysis and robust text extraction capabilities.
* Studied techniques for extracting text from legacy PDF formats and handling non-standard encodings.

**2025.12.12**
* Initialized the development environment and configured the Python virtual environment.
* Established the project repository on GitHub with a structured directory for source code and documentation.
* Configured initial project settings and version control workflows.

---

### Week 2: Data Acquisition and PDF Extraction (Dec 15 – Dec 19)

**2025.12.15**
* Commenced implementation of the `PDFExtractor` class to automate document processing.
* Developed core logic for reading PDF files and efficiently iterating through page content.
* Integrated text cleaning routines to eliminate unnecessary whitespace and formatting artifacts.

**2025.12.16**
* Implemented layout-aware extraction to filter out headers, footers, and page numbers automatically.
* Refined margin detection algorithms to ensure only the core policy content is extracted.
* Enhanced the extractor to maintain the logical reading order in multi-column document layouts.

**2025.12.17**
* Developed specialized logic for table extraction using the PyMuPDF `find_tables()` method.
* Implemented routines to convert extracted tables into structured Markdown and Pandas DataFrames.
* Tested the extraction performance on complex regulatory schedules and data tables.

**2025.12.18**
* Improved content categorization to distinguish between headings, paragraphs, and tables.
* Implemented font size analysis to detect document hierarchy and heading levels automatically.
* Added logic to merge fragmented text blocks into cohesive logical paragraphs.

**2025.12.19**
* Performed end-to-end testing of the extraction pipeline on various wetland policy documents.
* Resolved character encoding issues and handled special symbols common in legal texts.
* Optimized extraction performance by implementing batch processing for large document sets.

---

### Week 3: Core RAG - Processing and Semantic Chunking (Dec 22 – Dec 24)
*(Note: Dec 25 and Dec 26 were Public Holidays)*

**2025.12.22**
* Researched advanced chunking strategies to preserve context in long legal and policy documents.
* Studied the impact of chunk overlap on retrieval accuracy and context window efficiency.
* Defined a robust metadata schema to track source filenames, page numbers, and content types for each chunk.

**2025.12.23**
* Implemented the `SemanticChunker` class using SentenceTransformers for intelligent document splitting.
* Developed merging logic based on embedding similarity to keep semantically related text together.
* Configured the chunker to respect logical document boundaries, such as headings and table ends.

**2025.12.24**
* Refined the text normalization pipeline to resolve inconsistencies in punctuation and formatting.
* Implemented a cleaning layer to remove OCR-related errors and non-printable characters.
* Benchmarked semantic similarity thresholds and verified chunk quality through manual verification.

---

### Week 4: Core RAG - Indexing and Hybrid Retrieval (Dec 29 – Jan 02)
*(Note: Dec 31 and Jan 01 were Public Holidays)*

**2025.12.29**
* Integrated the FAISS (Facebook AI Similarity Search) library for high-performance vector storage.
* Developed an indexing pipeline to transform document chunks into embeddings and store them in FAISS.
* Implemented persistence mechanisms to save and load the vector index from disk storage.

**2025.12.30**
* Implemented a BM25-based retriever to provide robust keyword-centric search capabilities.
* Developed an `EnsembleRetriever` to combine vector search and BM25 results using a weighted system.
* Conducted initial retrieval tests to balance semantic relevance and keyword matching precision.

**2026.01.02**
* Designed the unified `RAGPipeline` class to manage the complete flow from query to retrieval.
* Evaluated the performance of the hybrid retrieval system against pure vector and keyword search models.
* Integrated comprehensive logging and error-handling into the pipeline for improved system observability.

---

### Week 5: Advanced Retrieval and Relevance Reranking (Jan 05 – Jan 09)

**2026.01.05**
* Researched reranking models to enhance the precision of the retrieved document sets.
* Evaluated CrossEncoder models, focusing on the trade-off between computational cost and accuracy.
* Selected the `ms-marco-MiniLM-L-6-v2` model for the reranking stage of the prototype.

**2026.01.06**
* Implemented the `RelevanceChecker` class to perform secondary scoring of retrieved chunks.
* Integrated the CrossEncoder into the pipeline to re-rank the initial search results dynamically.
* Developed filtering logic to exclude chunks that fall below a defined relevance threshold.

**2026.01.07**
* Enhanced the `RelevanceChecker` with a min/max normalization routine for consistent scoring.
* Implemented a fallback mechanism to cosine similarity to ensure reliability if the CrossEncoder fails.
* Optimized the reranking process by implementing batch scoring for multiple chunks.

**2026.01.08**
* Developed a contextual compression mechanism to prune irrelevant sentences within a retrieved chunk.
* Implemented sentence-level similarity checks to retain only the most relevant content for the LLM.
* Successfully reduced the total token count of the context without sacrificing critical information.

**2026.01.09**
* Conducted extensive end-to-end testing of the advanced retrieval pipeline with complex policy queries.
* Verified that the reranker correctly prioritizes the most relevant legal and regulatory clauses.
* Fine-tuned threshold parameters to achieve an optimal balance between retrieval recall and precision.

---

### Week 6: LLM Integration and Agent Logic (Jan 12 – Jan 16)
*(Note: Jan 15 was a Public Holiday)*

**2026.01.12**
* Evaluated the DeepSeek V3.1 model for its superior reasoning capabilities and long context support.
* Researched the Hugging Face Inference API for reliable and cost-effective model hosting.
* Authored the system prompt to enforce a professional tone and mandate citation-backed responses.

**2026.01.13**
* Implemented the LLM integration layer using the OpenAI-compatible API on the Hugging Face platform.
* Developed robust error-handling, timeout management, and retry logic for API requests.
* Configured model hyperparameters, such as temperature and max tokens, for stable and predictable output.

**2026.01.14**
* Developed the agentic loop with tool-calling capabilities to enable dynamic context retrieval.
* Defined the `retrieve_documents` tool, allowing the agent to fetch relevant policy data on demand.
* Implemented multi-step reasoning logic to handle complex queries requiring multiple retrieval steps.

**2026.01.16**
* Created the `token_manager.py` module to automate Hugging Face API token rotation for high availability.
* Performed intensive prompt engineering to ensure a strict response structure (Hierarchy, Guidance, Citations).
* Verified the agent’s ability to provide precise citations and handle scenarios where information is unavailable.

---

### Week 7: Frontend Development - Part 1 (Jan 19 – Jan 23)

**2026.01.19**
* Designed the layout of the Streamlit application, emphasizing a clean and professional dashboard UX.
* Defined the "Marsh Warden" visual identity, including the primary teal and cyan color palette.
* Developed the sidebar structure for model selection, session metrics, and chat management tools.

**2026.01.20**
* Implemented custom CSS overrides to enhance the aesthetics and responsiveness of the Streamlit UI.
* Developed a dynamic header section featuring a custom image slideshow and branding.
* Styled chat message bubbles to provide a clear visual distinction between user and assistant roles.

**2026.01.21**
* Integrated Google OAuth 2.0 to provide secure and personalized access to the application.
* Developed user profile cards for the sidebar to display authentication details and user initials.
* Implemented a guest access mode via URL parameters to facilitate quick demonstrations.

**2026.01.22**
* Implemented advanced session state management to ensure chat persistence during user interactions.
* Developed automated logic to save and load conversation histories from JSON-based storage.
* Added a theme toggle feature, allowing users to switch between light and dark visual modes seamlessly.

**2026.01.23**
* Built the core chat interface components and linked them to the agentic RAG backend.
* Implemented a "View Sources" expander to show the exact document chunks and metadata for each response.
* Added functionality for starting new conversations and clearing history through the management panel.

---

### Week 8: Frontend Development - Part 2 (Jan 26 – Jan 30)

**2026.01.26**
* Configured a React development environment to build custom, high-performance Streamlit components.
* Initialized the `Chat_input_widget` project utilizing TypeScript and the Tailwind CSS framework.
* Set up the build pipeline to generate Streamlit-compatible frontend artifacts.

**2026.01.27**
* Developed the custom `chat_input_widget` with a focus on modern UX and input accessibility.
* Implemented an integrated audio recording feature using the browser's MediaRecorder API.
* Added support for dynamic query suggestions that appear contextually above the input field.

**2026.01.28**
* Integrated the custom React widget into the main Streamlit application framework.
* Established a reliable communication bridge between the React frontend and the Python backend.
* Resolved complex styling and layout conflicts between the custom widget and Streamlit's default styles.

**2026.01.29**
* Enhanced the conversation management system with archiving, renaming, and organization features.
* Implemented a persistent storage directory for categorized past conversations.
* Added the capability to restore archived conversations with full context, history, and source citations.

**2026.01.30**
* Integrated the Whisper-large-v3 model via Hugging Face to provide high-accuracy voice transcription.
* Developed a seamless backend workflow for processing audio data received from the custom input widget.
* Added visual status indicators to provide real-time feedback during the transcription and processing phases.

---

### Week 9: Finalization and Project Delivery (Feb 02 – Feb 03)
*(Note: Feb 04 was a Public Holiday)*

**2026.02.02**
* Implemented a PDF export feature using the FPDF library to allow users to save conversation logs.
* Developed formatting logic to ensure exported PDFs are professional, readable, and properly cited.
* Integrated the export functionality directly into the user interface for easy accessibility.

**2026.02.03**
* Performed comprehensive system-wide testing and addressed final UI/UX inconsistencies.
* Optimized application startup and response times by implementing intelligent caching for the RAG indices.
* Finalized the project documentation, including setup guides, and conducted a successful demonstration for the IWMI research team.
