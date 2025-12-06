# 🧠 Shared Memory Prompt Template

**Use this template when giving tasks to any AI assistant to ensure they have access to the shared knowledge base.**

---

## Standard Prompt Template

Copy and paste this at the beginning of every prompt you send to ChatGPT, Monday, Perplexity, Monica, or any other AI:

```
**📚 SHARED MEMORY & CONTEXT:**

This project uses a GitHub repository as a shared knowledge base. All AI assistants working on this project should review the existing work to avoid duplication and build upon previous findings.

**Main Repositories:**
- Production Code: https://github.com/KoMMb0t/Computer-Voice-Assi
- Shared Memory Hub: https://github.com/KoMMb0t/voice-assi-nexus
- Wake-Word Infrastructure: https://github.com/KoMMb0t/hey-jarvis

**Key Documents to Review:**
- Architecture: https://github.com/KoMMb0t/voice-assi-nexus/blob/main/docs/architecture/CHIMERA_ARCHITECTURE.md
- Master Plan: https://github.com/KoMMb0t/voice-assi-nexus/blob/main/docs/MASTER_ACTION_PLAN_7_DAYS.md
- Final Report: https://github.com/KoMMb0t/voice-assi-nexus/blob/main/OPERATION_NEXUS_FINAL_REPORT.md

**Previous AI Contributions:**
- ChatGPT: OOP architecture, LLM integration, unit tests
- Monday: Event-Bus architecture, Personality Core, creative features
- Perplexity: Wake-word training research, best practices
- Monica: Icons, tutorials, documentation examples
- Manus: Chimera architecture synthesis, deployment infrastructure

---

**🎯 YOUR TASK:**
[Insert your specific task here]

---

**📦 DELIVERY FORMAT:**
Please provide your results as:
1. Complete, standalone files (code, documentation, etc.)
2. Clear file names indicating their purpose
3. A brief summary of what you created and where it fits in the project

Your work will be added to the shared memory repository so other AIs can build upon it.
```

---

## How to Use This Template

1. **Copy the template above**
2. **Replace `[Insert your specific task here]`** with your actual task
3. **Send to the AI**
4. **When the AI responds**, save its output as files
5. **Commit and push** those files to the appropriate repository

---

## Example Usage

### Example 1: Asking ChatGPT to implement a feature

```
**📚 SHARED MEMORY & CONTEXT:**
[...standard template...]

**🎯 YOUR TASK:**
Implement the AudioService class for the Chimera architecture. This service should:
- Capture audio from the microphone using sounddevice
- Publish AudioChunkReceived events to the Event Bus
- Handle start/stop functionality
- Include proper error handling

Please review the Chimera architecture document first to understand how services should be structured.

**📦 DELIVERY FORMAT:**
Provide the complete `services/audio_service.py` file with full implementation.
```

### Example 2: Asking Perplexity for research

```
**📚 SHARED MEMORY & CONTEXT:**
[...standard template...]

**🎯 YOUR TASK:**
Research the latest developments in wake-word detection for 2024-2025. Focus on:
- New training methods that require fewer samples
- Improvements in false-positive reduction
- Cross-platform compatibility (Windows/Linux/Android)

**📦 DELIVERY FORMAT:**
Provide a research report in Markdown format with sources cited.
```

---

## Benefits of Using This Template

- ✅ **Consistency:** All AIs start with the same context
- ✅ **No Duplication:** AIs can see what others have already done
- ✅ **Better Quality:** AIs can build upon previous work instead of starting from scratch
- ✅ **Coordination:** Creates a sense of "team" among the AIs

---

**This template is your key to effective multi-AI collaboration!** 🚀
