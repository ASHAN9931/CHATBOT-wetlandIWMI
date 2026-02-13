# World Wetland Day (WWD) Demo Guide: WCPA Assistant

This guide is prepared for the WWD event at IWMI to demonstrate the capabilities and limitations of the Wetland Conservation Policy Assistant (WCPA).

## 🚀 Demo Strategy: "The Power of Policy AI"

The goal is to show how the chatbot transforms complex legal and policy documents into immediate, actionable, and structured advice, while being honest about its boundaries as a document-based RAG system.

### 🌟 Part 1: High-Performance Capabilities (Retrieval & Synthesis)

Use these questions to show the chatbot's ability to retrieve specific facts and **structure data into tables**.

1.  **Tabular Comparison (The "Wow" Factor):**
    *   **Question:** *"Compare development conditions for different wetland zones in a table."*
    *   **Why it works:** The bot extracts data from the "Wetlands-Zoning Guidelines Western Province (2018)" and structures technical conditions (plot size, coverage, building height) into a clean table.
    *   **Value:** Instant cross-referencing of multiple guidelines.

2.  **Comprehensive Policy Summary:**
    *   **Question:** *"What are the six primary objectives of the National Wetland Policy (2006)?"*
    *   **Why it works:** It precisely identifies the "Objectives" section of the 2006 policy and lists all six points accurately.
    *   **Value:** Reliable "single source of truth" retrieval.

3.  **Specific Zoning Explanations:**
    *   **Question:** *"Explain the four basic wetland zones in the Western Province."*
    *   **Why it works:** It provides a detailed breakdown of the zones defined in the 2018 guidelines, explaining the purpose of each.
    *   **Value:** Simplifies complex spatial planning documents.

---

### ⚠️ Part 2: Understanding the Boundaries (System Limitations)

Use these to show the "RAG Reality"—the system only knows what is in its document library.

4.  **Limitation: Real-Time / Dynamic Data**
    *   **Question:** *"What is the current water level at Beddagana Wetland Park today?"*
    *   **Expected Response:** The bot will state it doesn't have real-time information.
    *   **Reasoning:** Explain that this is a **policy expert**, not a real-time sensor monitoring system.

5.  **Limitation: Scope & Private Data**
    *   **Question:** *"Who are the private landowners in the Bolgoda wetland area?"*
    *   **Expected Response:** The bot will be unable to provide specific names or private records.
    *   **Reasoning:** Explain that while it knows the *policies* for private land (e.g., from the NWP 2006), it does not have access to private land registries or PII for security and privacy reasons.

---

## 🛠️ Suggestion Chips
These five questions are pre-loaded as **Suggestion Chips** at the bottom of the chat window for easy access during your demonstration.

## 💡 Pro Tip
If a visitor asks about a specific animal, try: *"What are the legal protections for [Species Name] in Sri Lanka?"*. This demonstrates how the bot handles the Fauna and Flora Protection Ordinance (FFPO).
