# Chimera Architecture: A Hybrid Approach

**The best of both worlds: Combining the clarity of OOP with the flexibility of an Event-Bus.**

This document outlines the "Chimera" architecture, a hybrid software design that synthesizes the best elements from two distinct AI-generated approaches: **ChatGPT's OOP model** and **Monday's Event-Bus model**.

## 1. Core Philosophy

The Chimera architecture is built on a simple principle: **Structure for clarity, events for flexibility.**

- **Object-Oriented Programming (OOP):** Provides a clear, hierarchical structure for core components. Each part of the system is a well-defined object with a specific responsibility.
- **Event-Bus:** Decouples components, allowing them to communicate without direct dependencies. This makes the system highly modular, extensible, and easy to test.

## 2. Architectural Diagram (ASCII Art)

```
+-----------------------------------------------------------------------+
|                                Main Application                       |
+-----------------------------------------------------------------------+
|                                                                       |
|   +-----------------+      +-----------------+      +-----------------+   |
|   | Service Locator |----->|   Event Bus     |<-----| Config Manager  |   |
|   +-----------------+      +-----------------+      +-----------------+   |
|                                      ^                                |
|                                      |                                |
|                                      v                                |
| +---------------------------------------------------------------------+ |
| |                              SERVICES                               | |
| +---------------------------------------------------------------------+ |
| |                                                                     | |
| |  +-----------------+   +-----------------+   +-----------------+    | |
| |  |  Audio Service  |-->| WakeWord Service|-->|   STT Service   |    | |
| |  | (Produces Audio)|   | (Consumes Audio,|   | (Consumes Audio,|    | |
| |  |                 |   |  Produces Wake) |   |  Produces Text) |    | |
| |  +-----------------+   +-----------------+   +-----------------+    | |
| |          ^                   ^                   ^                  | |
| |          |                   |                   |                  | |
| |          v                   v                   v                  | |
| |  +-----------------+   +-----------------+   +-----------------+    | |
| |  |   TTS Service   |-->|  Command Handler|-->|   LLM Service   |    | |
| |  | (Consumes Text, |   | (Consumes Text, |   | (Consumes Text, |    | |
| |  |  Produces Audio)|   |  Produces Action)|   |  Produces Text) |    | |
| |  +-----------------+   +-----------------+   +-----------------+    | |
| |                                                                     | |
| +---------------------------------------------------------------------+ |
|                                                                       |
+-----------------------------------------------------------------------+
```

## 3. Key Components

### Core Infrastructure

- **Main Application (`main.py`):** The entry point. Initializes the core infrastructure and starts the services.
- **Event Bus (`core/event_bus.py`):** The central nervous system. All communication between services happens through events.
- **Service Locator (`core/service_locator.py`):** A central registry for accessing shared services like the Event Bus, Config Manager, and Logger.
- **Config Manager (`core/config_manager.py`):** Loads and provides access to all configuration data.

### Services

Each service is a self-contained class that performs a specific task. Services communicate via the Event Bus.

- **Audio Service (`services/audio_service.py`):**
  - **Responsibility:** Captures audio from the microphone.
  - **Publishes:** `AudioChunkReceived` event with raw audio data.

- **WakeWord Service (`services/wake_word_service.py`):**
  - **Subscribes to:** `AudioChunkReceived` event.
  - **Responsibility:** Detects the wake-word in the audio stream.
  - **Publishes:** `WakeWordDetected` event.

- **STT Service (`services/stt_service.py`):**
  - **Subscribes to:** `AudioChunkReceived` event (after wake-word detection).
  - **Responsibility:** Transcribes speech to text.
  - **Publishes:** `SpeechRecognized` event with the transcribed text.

- **Command Handler (`services/command_handler.py`):**
  - **Subscribes to:** `SpeechRecognized` event.
  - **Responsibility:** Identifies and executes local commands (e.g., "open calculator").
  - **Publishes:** `ActionExecuted` event or forwards to LLM Service.

- **LLM Service (`services/llm_service.py`):**
  - **Subscribes to:** `SpeechRecognized` event (if not a local command).
  - **Responsibility:** Sends queries to a large language model (e.g., ChatGPT).
  - **Publishes:** `LLMResponseReceived` event with the AI's answer.

- **TTS Service (`services/tts_service.py`):**
  - **Subscribes to:** `LLMResponseReceived` and `ActionExecuted` events.
  - **Responsibility:** Converts text responses to speech.
  - **Publishes:** `SpeechStarted` and `SpeechEnded` events.

## 4. Event Flow Example: User asks a question

1. **Audio Service** continuously publishes `AudioChunkReceived` events.
2. **WakeWord Service** listens and detects "Computer". It publishes a `WakeWordDetected` event.
3. **STT Service** starts listening for speech. It transcribes "What is the capital of France?" and publishes a `SpeechRecognized` event.
4. **Command Handler** receives the text, determines it's not a local command, and forwards it.
5. **LLM Service** receives the text, sends it to the OpenAI API, and receives "Paris". It publishes an `LLMResponseReceived` event with the text "Paris".
6. **TTS Service** receives the text "Paris", converts it to audio, and plays it.

## 5. Advantages of the Chimera Architecture

- **Decoupling:** Services don't need to know about each other. You can replace the STT service without touching any other part of the system.
- **Testability:** Each service can be tested in isolation by mocking the events it subscribes to and checking the events it publishes.
- **Extensibility:** Adding new functionality is as simple as creating a new service that subscribes to existing events or publishes new ones.
- **Clarity:** The OOP structure of each service makes the code easy to understand and maintain.
- **Scalability:** Services can be run in separate threads or even on different machines in the future.

## 6. Comparison to Pure Models

- **vs. Pure OOP (ChatGPT):** A pure OOP model would require services to hold references to each other, creating tight coupling. The Chimera architecture avoids this with the Event Bus.
- **vs. Pure Event-Bus (Monday):** A pure event-driven model can sometimes obscure the overall structure. The Chimera architecture retains a clear OOP structure for each service, making it easier to reason about.

## 7. Conclusion

The Chimera architecture represents a mature, robust, and scalable design for the Computer-Voice-Assi project. It provides a solid foundation for future development, including the integration of new services, plugins, and platforms.

---

**Authored by Manus AI (Operation Nexus)**
