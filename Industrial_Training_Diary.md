# Industrial Training Diary - Marsh Warden Project

## Period: 2025.12.08 - 2026.02.13

### 2025.12.08
- Project kickoff for the 'Marsh Warden' AI assistant. Held meetings with IWMI stakeholders to define the primary goals of the project, focusing on supporting wetland conservation policy in Sri Lanka. We discussed the challenges faced by policymakers and researchers in accessing and interpreting complex environmental regulations.

### 2025.12.09
- Intensive requirement gathering and initial data collection. I identified and gathered key wetland-related policy documents, national strategies, and legal acts from various governmental sources like the Central Environmental Authority (CEA). This involved cataloging the documents and assessing their digital format quality for extraction.

### 2025.12.10
- Set up the local development environment, including Python environments and necessary libraries for PDF processing. I spent time exploring the internal structure of the collected PDFs, noting that many contain complex tables and varying layouts that would require sophisticated extraction techniques later on.

### 2025.12.11
- Started implementing the core PDF text extraction module using the PyMuPDF (fitz) library. I focused on extracting clean text while attempting to maintain basic structural elements like paragraphs. I also explored initial chunking strategies, considering fixed-length versus paragraph-based splitting.

### 2025.12.12
- Conducted deep-dive research into RAG (Retrieval-Augmented Generation) architectures, specifically looking for those optimized for legal and policy documents. I evaluated different embedding models from the Hugging Face Leaderboard, prioritizing those with strong performance on technical and formal English text.

### 2025.12.15
- Integrated FAISS as the primary vector database for storing document embeddings. I implemented the first version of the retrieval pipeline, which involved encoding document chunks and performing similarity searches to find relevant context for a given user query. This laid the foundation for the search capabilities.

### 2025.12.16
- Developed a basic but functional Streamlit user interface to provide a front-end for the retrieval system. This allowed for real-time interaction with the document index, enabling us to quickly verify if the retrieved chunks were actually relevant to sample wetland conservation questions.

### 2025.12.17
- Integrated the DeepSeek V3.1 model via the Hugging Face Inference API as the main Large Language Model for the chatbot. I focused on setting up the API connections and handling basic prompt engineering to generate coherent answers based on the retrieved document context.

### 2025.12.18
- Began implementing an agentic loop using tool-calling capabilities. I defined a 'retrieve_documents' tool that the LLM can decide to use when it needs more information to answer a question. This approach allows the assistant to be more proactive in its information-gathering process during a conversation.

### 2025.12.19
- Focused on refining the system prompt to enforce a strict professional persona. I established a mandatory response structure that includes a legal hierarchy, comprehensive guidance, and required citations. This ensures that the AI's advice is always grounded in official policy and easy for users to verify.

### 2025.12.22
- Significantly enhanced the PDF extraction module to better handle complex document layouts. I implemented logic to detect and skip headers/footers based on page margins and used font size thresholds to identify headings, which helps in preserving the hierarchical structure of the policies during chunking.

### 2025.12.23
- Worked on the table extraction feature using PyMuPDF's 'find_tables' method. I developed logic to convert extracted tables into a text-based format (Markdown or String representations) so that the RAG pipeline can effectively process and retrieve data stored within structured tables in the policy documents.

### 2025.12.24
- Performed a comprehensive round of end-to-end testing of the current prototype. I used a set of 20 diverse queries related to wetland protection acts and management guidelines to evaluate the accuracy of both the retrieval and the generation components, identifying areas for further optimization.

### 2025.12.29
- Developed a custom RelevanceChecker class to add a verification layer to the retrieval process. This class uses a similarity threshold to filter out chunks that might be mathematically similar but contextually irrelevant, ensuring that the LLM only receives the most high-quality information.

### 2025.12.30
- Implemented a reranking step using a Cross-Encoder model (MiniLM-L-6-v2). This model evaluates the relationship between the query and each retrieved chunk more deeply than simple vector similarity, significantly improving the precision of the context provided to the assistant.

### 2026.01.02
- Experimented with hybrid retrieval techniques by combining semantic search (via FAISS) with traditional keyword search (via BM25). I implemented an EnsembleRetriever to weight the results from both methods, which helps in finding specific legal terms that might be missed by purely semantic embeddings.

### 2026.01.05
- Designed and implemented a 'SemanticChunker' to replace the older recursive splitting method. This new chunker first breaks text into mini-chunks and then merges them based on embedding similarity, ensuring that each final chunk contains a cohesive and contextually complete idea.

### 2026.01.06
- Integrated Google Authentication using the 'google_auth.py' module to provide secure access control. I focused on setting up the OAuth flow and managing session states to ensure that only authorized IWMI personnel and partners can access the 'Marsh Warden' assistant.

### 2026.01.07
- Built a robust chat history persistence layer. I implemented logic to save conversations as JSON files, enabling users to maintain continuity across multiple sessions. This involved creating a secure directory structure for history storage and handling unique user identifiers based on their email.

### 2026.01.08
- Added advanced management features for chat history, including the ability for users to archive old conversations and rename them for easier retrieval. This involved developing UI elements in the Streamlit sidebar to allow for these management actions without interrupting the main chat flow.

### 2026.01.09
- Extensively refactored the session state management logic to support multiple concurrent users and a seamless 'guest mode'. I ensured that session data is correctly isolated and that the application remains stable even when multiple authentication states are being handled.

### 2026.01.12
- Started the development of a custom React-based chat input widget. This widget was designed to replace the standard Streamlit input, providing a more modern and interactive experience, including better support for various media types and fixed positioning at the bottom of the screen.

### 2026.01.13
- Integrated audio transcription capabilities into the application. I utilized the OpenAI Whisper model (version 3) via the Hugging Face Inference API, allowing users to speak their questions instead of typing them. I focused on handling the audio data transmission and parsing the API responses.

### 2026.01.14
- Implemented real-time audio recording directly within the custom React chat widget. I worked on the JavaScript MediaRecorder API to capture audio from the user's microphone and send it to the backend Streamlit application for transcription and processing.

### 2026.01.16
- Developed a token rotation system for the Hugging Face API. I created a 'token_manager.py' module that can cycle through a list of backup tokens if the primary token hits rate limits or encounters errors, ensuring high availability of the LLM and transcription services.

### 2026.01.19
- Implemented a PDF export feature using the FPDF library. This allows users to download a professionally formatted transcript of their conversation, including citations and source references, which is highly useful for documentation and reporting purposes in policy work.

### 2026.01.20
- Revamped the entire UI/UX design. I applied a professional color palette inspired by nature and wetland environments (teals and greens) and implemented a robust dark mode toggle that adjusts both the Streamlit theme and the custom React components.

### 2026.01.21
- Focused on optimizing the retrieval pipeline for speed. I implemented caching for model initializations and document indices, and refined the hybrid search parameters to balance retrieval depth with the response time requirements of a real-time chat application.

### 2026.01.22
- Implemented contextual compression at the sentence level. Within each retrieved chunk, the system now identifies and keeps only the most relevant sentences related to the user's query, which reduces the amount of noise sent to the LLM and improves the clarity of its answers.

### 2026.01.23
- Conducted a thorough security audit and bug-fixing session. I focused on hardening the authentication modules, ensuring that guest sessions are properly isolated, and fixing edge cases in the chat history management system that could lead to data loss.

### 2026.01.26
- Refined the agentic loop's decision-making process. I improved the tool descriptions and updated the system prompt to help the LLM decide more accurately when it needs to call the 'retrieve_documents' tool versus answering from its internal knowledge for general greetings.

### 2026.01.27
- Added specialized handling for document-specific queries. I implemented logic that allows the assistant to prioritize certain policy documents if the user mentions them by name (e.g., 'What does the National Wetland Policy say about...') during the retrieval and generation stages.

### 2026.01.28
- Enhanced the custom chat widget with dynamic suggestion chips. These chips provide users with quick-reply options or sample questions based on the context of the current conversation, helping to guide them through the complex information available in the knowledge base.

### 2026.01.29
- Implemented an auto-archiving feature for older conversations to keep the user's dashboard clean. I also improved the sidebar navigation, making it easier to switch between the control panel, past conversations, and the 'About' section for the assistant.

### 2026.01.30
- Finalized all core features for the Marsh Warden prototype. I conducted a final walkthrough of the system, verifying that all modules (RAG, UI, Auth, History, Audio) are working harmoniously and preparing the code for the upcoming experimental phase.

### 2026.02.02
- Conducted an intensive system review and performance benchmarking session. I analyzed the latency of various components (embedding, retrieval, LLM generation, transcription) and identified remaining bottlenecks in the pipeline for future optimization.

### 2026.02.03
- Completed the comprehensive technical documentation for the prototype phase. I updated the README and Deployment guides, ensuring that the installation and setup processes are clearly defined for other developers and system administrators.

### 2026.02.04
- Kicked off the experimental phase by testing alternative Large Language Models. I evaluated the performance of Llama 3 (8B and 70B) and Qwen models against our baseline DeepSeek V3.1, specifically looking at their ability to correctly interpret and cite Sri Lankan legal terminology.

### 2026.02.05
- Evaluated several advanced libraries for building agentic workflows, such as LangGraph. I explored how a more structured, graph-based approach to agent reasoning could improve the assistant's ability to handle multi-step queries that require information from multiple different policy documents.

### 2026.02.06
- Focused on enhancing the codebase by refactoring the retrieval logic into a more modular and extensible structure. I also improved the error handling and logging within the main agent loop, making it easier to diagnose issues during complex multi-tool interactions.

### 2026.02.09
- Tested state-of-the-art reranking models from different providers (Cohere, BGE) to compare their effectiveness with our current MiniLM model. I also experimented with several embedding models (like GTE-large) to see if they provided better semantic separation for environmental policy text.

### 2026.02.10
- Further improved the custom chat widget by implementing better file upload handling and real-time upload progress feedback. I also added support for displaying more complex data visualizations that the assistant might generate from extracted table data in the future.

### 2026.02.11
- Conducted experiments with graph-based context representation. I explored building a small knowledge graph of the relationships between different environmental acts and policies, which could help the assistant better understand the legal hierarchy when answering questions.

### 2026.02.12
- Worked on refining the audio transcription pipeline. I experimented with running smaller, optimized versions of the Whisper model locally to reduce the latency associated with API calls, aiming for a more responsive voice-to-text experience for mobile users.

### 2026.02.13
- Finalized the documentation of all experimental results gathered during the training period. I performed a final code cleanup, removing deprecated modules and ensuring that the project is in a clean, stable state for the final hand-over to the IWMI team.
