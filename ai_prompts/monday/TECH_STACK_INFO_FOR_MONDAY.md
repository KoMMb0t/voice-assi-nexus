## **TECH-STACK-AUFKLÄRUNG FÜR MONDAY**

Hey Monday,

damit du nicht im Dunkeln tappst und dein glorreiches Refactoring auf den richtigen, wenn auch etwas... *rustikalen*... Komponenten aufbauen kannst, hier die knallharten Fakten zum aktuellen Tech-Stack. Ja, es ist kein Hamster mit Morsecode. Schade eigentlich.

---

### **1. Wake-Word-Erkennung**

> **Deine Frage:** *Snowboy, Vosk, selbstgebastelt?*

**Antwort:** **OpenWakeWord**

*   **Details:** Ein Open-Source-Ansatz. Aktuell wird noch das `hey_jarvis` Modell als Platzhalter verwendet. Das Ziel ist es, ein eigenes "Computer"-Modell zu haben. Porcupine wurde als Alternative evaluiert.
*   **Dein Job:** Eine Architektur bauen, die so flexibel ist, dass man die Wake-Word-Engine wie eine schmutzige Socke wechseln kann. Plane also für austauschbare Module.

---

### **2. STT (Speech-to-Text) Engine**

> **Deine Frage:** *Whisper? Google? PocketSphinx? Ein Hamster mit Morsecode?*

**Antwort:** **Vosk**

*   **Details:** Läuft komplett offline, was für Privatsphäre-Fanatiker (und Leute mit schlechtem Internet) ganz nett ist. Genutzt wird das deutsche Modell (`lang="de"`).
*   **Dein Job:** Kapsle diese Logik in einem sauberen Service, damit man sie später gegen eine Cloud-API (wie Whisper) austauschen könnte, falls der Nutzer mal Geld ausgeben will.

---

### **3. TTS (Text-to-Speech) Engine**

> **Deine Frage:** *pyttsx3? ElevenLabs? Festival, für Leute mit Geschmack von 1998?*

**Antwort:** **Edge TTS**

*   **Details:** Nutzt Microsofts Online-Dienst für eine qualitativ hochwertige neuronale Stimme (`de-DE-KatjaNeural`). Ist also nicht offline, im Gegensatz zu Vosk. Ein cleverer, inkonsistenter Mix.
*   **Dein Job:** Auch hier: Kapsle es in einem Service. Die Architektur sollte es erlauben, eine Offline-TTS (wie `pyttsx3`) als Fallback zu integrieren, wenn das Internet mal wieder weg ist.

---

### **ZUSAMMENFASSUNG FÜR DEIN GENIALES HIRN:**

| Komponente | Aktuelle Implementierung | Charakteristik | Deine Aufgabe |
| :--- | :--- | :--- | :--- |
| **Wake-Word** | `OpenWakeWord` | Open Source, lokales Modell | Austauschbar machen (z.B. für Porcupine) |
| **STT** | `Vosk` | Offline, Deutsch | In Service kapseln, für Austauschbarkeit sorgen |
| **TTS** | `Edge TTS` | Online, hohe Qualität | In Service kapseln, Fallback-Möglichkeit schaffen |

Jetzt hast du alle Informationen. Keine Ausreden mehr. Mach was draus. Und mach es besser als die Konkurrenz.
