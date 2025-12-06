# 🚀 Computer-Voice-Assi: The Nexus README

**Welcome to the synthesized, AI-accelerated future of the Computer-Voice-Assi project.**

This document represents the culmination of a multi-AI collaborative effort, combining the best ideas, architectures, and assets into a single, unified vision. This is the ultimate README, designed to be the new master documentation for the project moving forward.

## 1. Project Vision

To create a **modular, extensible, and robust** voice assistant that is:

-   **Easy to customize:** Add new commands, skills, and personalities with minimal effort.
-   **Platform-aware:** Designed for Windows, with a clear path to Linux and other platforms.
-   **AI-driven:** Leverages the power of large language models for natural interaction.
-   **Community-focused:** Built with open source principles and clear documentation.

## 2. The Chimera Architecture

The project is built on the **Chimera Architecture**, a hybrid design that combines the clarity of Object-Oriented Programming (OOP) with the flexibility of an Event-Driven Architecture (EDA). This provides a scalable and maintainable foundation for future development.

For more details, see the [Chimera Architecture Document](docs/architecture/CHIMERA_ARCHITECTURE.md).

## 3. Key Features

| Feature | Description | Status |
| :--- | :--- | :--- |
| **Wake-Word Detection** | Custom "Computer" wake-word training pipeline. | In Development |
| **Modular Services** | Decoupled services for STT, TTS, Commands, etc. | Implemented |
| **Event-Bus Communication** | Asynchronous communication between services. | Implemented |
| **LLM Integration** | Dynamic, personality-driven LLM queries. | Implemented |
| **Plugin System** | Easily add new functionality via plugins. | Implemented |
| **Secure Configuration** | Secure API key management with `.env` files. | Implemented |
| **Automated Build** | One-click build process for Windows executables. | Implemented |

## 4. Getting Started (The 7-Day Plan)

Follow the [Master Action Plan](docs/MASTER_ACTION_PLAN_7_DAYS.md) to get the new architecture up and running in just one week.

### Quick Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/KoMMb0t/Computer-Voice-Assi.git
    cd Computer-Voice-Assi
    ```

2.  **Set up your environment:**
    ```bash
    # Create a .env file from the example
    copy .env.example .env
    # Edit .env with your API keys
    notepad .env
    ```

3.  **Run the application:**
    ```bash
    # (After implementing the Chimera architecture)
    python main.py
    ```

## 5. Customization

### Adding a New Command

1.  Create a new command class in `commands/default_commands.py`.
2.  Inherit from `Command` and implement the `execute()` method.
3.  The `CommandRegistry` will automatically discover and register it.

### Adding a New Plugin

1.  Create a new plugin class in the `plugins/` directory.
2.  Inherit from `Plugin` and implement the `initialize()` method.
3.  The `PluginManager` will automatically load and start it.

## 6. Project Repositories

This project is spread across three repositories:

-   **[Computer-Voice-Assi](https://github.com/KoMMb0t/Computer-Voice-Assi):** The main application repository.
-   **[hey-jarvis](https://github.com/KoMMb0t/hey-jarvis):** Infrastructure for wake-word training and data management.
-   **[voice-assi-nexus](https://github.com/KoMMb0t/voice-assi-nexus):** The AI coordination hub where this plan was forged.

## 7. Visual Identity

*(This section will be updated with the final icons and logos selected from Monica's research.)*

-   **Application Icon:** [Placeholder]
-   **GitHub Logo:** [Placeholder]

## 8. Contributing

We welcome contributions! Please read the `CONTRIBUTING.md` file (to be created) for guidelines on how to contribute to the project.

---

**This document was synthesized by Manus AI as part of Operation Nexus.**
