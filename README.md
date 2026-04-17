# Project LENS (Linked Encoding of Narrative Styles)

## Overview
LENS is a modular framework for persona persistence and linguistic alignment. It leverages the **Unified Gemini-NotebookLM Sync (April 2026)** to turn your local GitHub-hosted manifests into a persistent, bidirectional knowledge base. 

## Repository Architecture
- **`global/`**: Universal negative constraints (Slop filters, rhythm rules).
- **`personas/`**: Context-specific identity manifests (e.g., `technical.md`, `storyteller.md`).
- **`template-persona.md`**: Standardized blueprint for new identity generation.

---

## Implementation

### 1. The GitHub-to-Google Sync Bridge
Because Gemini and NotebookLM now share a unified data layer, your local repository serves as the upstream source:
1. **Local Sync:** Manage `lens-core` in a folder synced via **Google Drive for Desktop**.
2. **Notebook Initialization:** Create a new **Notebook** in either Gemini or NotebookLM and add your synced `global/` and `personas/` files from Drive as notebook sources.
3. **Live Syncing:** When you commit changes to your manifests locally, update the source in your Notebook to reflect the new constraints instantly across both Gemini and NotebookLM. At the time of this writing, NotebookLM has a feature within the Notebook to "Refresh sources" which will pull in the latest changes from your synced . This is not automatic and must be done manually. You might find browser extension to assist with automated syncs but that falls outside the scope of this project. 

### 2. Execution (Gemini App)
- **Notebook Context:** In the Gemini side panel, activate the `LENS` Notebook. Gemini now "remembers" your identity, background, and constraints across all chats in that project.
- **Custom Gems:** Create a Reusable Gem linked to your LENS Notebook for specific roles (e.g., "The Technical Operator"). This combines your persistent sources with Gemini’s web-search and coding capabilities.

### 3. Execution (NotebookLM)
- **Source-Locked Analysis:** Open the same Notebook in NotebookLM for "grounded-only" work, such as auditing long-form drafts against your `constraints.md` without outside hallucinations.
- **Studio Tools:** Use the synced sources to generate **Video Overviews**, **Infographics**, or **Audio Overviews** that perfectly mirror your technical persona.

---

## Model-Agnostic Support
LENS remains portable to other frontier models via manual context injection or dedicated project features:
- **Claude Projects:** Set `global/constraints.md` as permanent Project Instructions.
- **ChatGPT Projects:** Use the GitHub repo as a "Project Knowledge Base" for consistent tonal alignment.

---

## Usage Protocol
1. **Define:** Update your persona or constraints locally.
2. **Sync:** GitHub Push -> Google Drive Auto-Sync -> Notebook Refresh.
3. **Prompt:** "Referencing my LENS notebook, adopt the [Persona] to draft [Content]."
