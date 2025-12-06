# Master Action Plan: The Next 7 Days

**A prioritized roadmap for human development, based on the synthesized results of the AI-driven overnight session.**

This document consolidates the key deliverables from all AI agents and translates them into a concrete, actionable plan for the next week.

## 1. Guiding Principles

- **Foundation First:** Implement the core architecture before adding new features.
- **Test Everything:** Integrate testing from day one.
- **Iterate Quickly:** Focus on small, incremental improvements.

## 2. The 7-Day Roadmap

### **Day 1: Architecture & Setup**

**Goal:** Implement the foundational "Chimera" architecture.

- **[ ] Task 1.1: Project Scaffolding:** Create the new project structure based on the Chimera architecture (`core/`, `services/`, `commands/`, `plugins/`).
- **[ ] Task 1.2: Implement Core Infrastructure:** Port the code for `EventBus`, `ServiceLocator`, and `ConfigManager` into the new project.
- **[ ] Task 1.3: Migrate Services:** Create the new service classes (`AudioService`, `WakeWordService`, etc.) and migrate the relevant logic from the old `voice_assistant_edge_ultimate.py` script.
- **[ ] Task 1.4: Initial `main.py`:** Write the main application entry point that initializes and starts the services.

### **Day 2: Wake-Word & STT Integration**

**Goal:** Get the basic voice interaction working in the new architecture.

- **[ ] Task 2.1: Wake-Word Data Collection:** Use the `record_wake_word.py` script from the `hey-jarvis` repo to record at least 100 positive samples of "Computer".
- **[ ] Task 2.2: Data Preparation:** Use the `prepare_datasets.py` and `augment_data.py` scripts to build a training dataset.
- **[ ] Task 2.3: (Parallel) Model Training:** Start the training process for the custom "Computer" wake-word model (this may take several hours).
- **[ ] Task 2.4: STT Service Integration:** Ensure the `STTService` correctly transcribes speech after the wake-word is detected.

### **Day 3: Command Handling & Basic TTS**

**Goal:** Execute local commands and get voice feedback.

- **[ ] Task 3.1: Command Handler:** Implement the `CommandHandler` service and migrate the local command logic (open calculator, etc.).
- **[ ] Task 3.2: TTS Service Integration:** Ensure the `TTSService` provides voice feedback for executed commands.
- **[ ] Task 3.3: Testing:** Write unit tests for the `CommandHandler` to verify that commands are correctly identified.

### **Day 4: LLM Integration**

**Goal:** Enable the assistant to answer general knowledge questions.

- **[ ] Task 4.1: Secure Config:** Set up your `.env` file with your OpenAI API key using the `secure_config.py` module.
- **[ ] Task 4.2: LLM Service:** Implement the `LLMService` to query the ChatGPT API.
- **[ ] Task 4.3: Intent Detection:** Implement the logic to differentiate between local commands and questions for the LLM.
- **[ ] Task 4.4: Testing:** Write unit tests for the `LLMService` (using mocks) to test the intent detection and API calls.

### **Day 5: UI & Visuals**

**Goal:** Improve the user interface and branding.

- **[ ] Task 5.1: Select Icons:** Review the icons collected by **Monica** and choose the best ones for the application, GitHub repo, and documentation.
- **[ ] Task 5.2: GUI Prototype:** Implement the simple `Tkinter` or `PyQt` GUI concept to show the assistant's status (Idle, Listening, etc.).
- **[ ] Task 5.3: README Update:** Update the main project `README.md` with the new logo and visuals.

### **Day 6: Advanced Features & Robustness**

**Goal:** Implement advanced features and make the system more robust.

- **[ ] Task 6.1: Personality Core:** Implement the `PersonalityCore` concept from **Monday** to allow for different response styles.
- **[ ] Task 6.2: Plugin System:** Implement the basic plugin manager and create a simple example plugin.
- **[ ] Task 6.3: Benchmarking:** Use the `benchmarking_script.py` to measure the performance of the new architecture.

### **Day 7: Documentation & Deployment**

**Goal:** Prepare the project for others to use and contribute.

- **[ ] Task 7.1: Finalize Documentation:** Update the `README.md` and create a `CONTRIBUTING.md` file.
- **[ ] Task 7.2: Build Executable:** Use the `build.bat` script from the `hey-jarvis` repo to create a standalone Windows executable.
- **[ ] Task 7.3: GitHub Release:** Create a new release on GitHub with the compiled executable and updated documentation.

## 3. Asset & Research Integration

- **Icons (from Monica):** Use the selected icons in Day 5.
- **Tutorials (from Monica):** Refer to the collected tutorials when implementing specific features (e.g., wake-word training, audio processing).
- **Research (from Perplexity):** Apply the best practices for wake-word training and audio processing throughout the development process.

This action plan provides a clear path forward, leveraging the incredible amount of work done by the AI team in a single night. By following this plan, the Computer-Voice-Assi project can rapidly evolve into a mature and powerful application.

---

**Authored by Manus AI (Operation Nexus)**
