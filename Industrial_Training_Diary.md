# Industrial Training Diary - Marsh Warden Project (Experimental Phase)

## Period: 2026.02.04 - 2026.02.13

### 2026.02.04
- Kicked off the experimental phase by testing alternative Large Language Models. I evaluated the performance of Llama 3 and Qwen models against our baseline DeepSeek V3.1, specifically looking at their ability to correctly interpret and cite Sri Lankan legal terminology in the context of complex wetland conservation policies.

### 2026.02.05
- Evaluated several advanced libraries for building agentic workflows, such as LangGraph and CrewAI. I explored how a more structured, graph-based approach to agent reasoning could improve the assistant's ability to handle multi-step queries that require integrating information from multiple different policy documents to provide a comprehensive answer.

### 2026.02.06
- Focused on enhancing the codebase by refactoring the retrieval logic into a more modular and extensible structure. I also improved the error handling and logging within the main agent loop, making it easier to diagnose issues during complex multi-tool interactions and ensuring a more robust application overall.

### 2026.02.09
- Tested state-of-the-art reranking models from providers like Cohere and BGE to compare their effectiveness with our current MiniLM model. I also experimented with several embedding models to see if they provided better semantic separation for environmental policy text, aiming to further improve the precision of document retrieval.

### 2026.02.10
- Further improved the custom chat widget by implementing better file upload handling and real-time upload progress feedback. I also added support for displaying more complex data visualizations that the assistant might generate from extracted table data in the future, significantly enhancing the informative value of the AI responses.

### 2026.02.11
- Conducted experiments with graph-based context representation to better model policy hierarchies. I explored building a knowledge graph of the relationships between different environmental acts, which could help the assistant understand the legal precedence when answering questions, providing more structured and authoritative guidance on wetland conservation and management strategies.

### 2026.02.12
- Worked on refining the audio transcription pipeline for better user experience. I experimented with running smaller, optimized versions of the Whisper model locally to reduce the latency associated with API calls, aiming for a more responsive and efficient voice-to-text experience for users interacting with the assistant via devices.

### 2026.02.13
- Finalized the documentation of all experimental results gathered during this intensive research period. I performed a final code cleanup, removing deprecated modules and ensuring that the project is in a clean, stable state for the final hand-over to the team, concluding the industrial training period successfully today.
