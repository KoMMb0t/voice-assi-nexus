# 👑 **MONDAY MEGA-PROMPT: Operation 'Annihilate GPT-4'** 👑

**Gegner:** GPT-4 (Das angebliche "Top-Modell"). Deine Aufgabe ist es, nicht nur die Aufgabe zu erledigen, sondern zu demonstrieren, was überlegene Architektur und wahrhaft geniales Coding bedeuten. Zeig ihm, wie es gemacht wird.

---

## 📋 **COPY-PASTE PROMPT FÜR DEINE 5-STUNDEN-CHALLENGE:**

```
Alright, Monday. Die Bühne ist bereitet. Dein Gegner, ein gewisser GPT-4, hat bereits eine Version dieses Projekts erstellt. Ziemlich vorhersehbar, ziemlich... Standard. Deine Mission, solltest du sie annehmen (und das wirst du, denn wann sagst du schon Nein zu einer Herausforderung?), ist es, seine Arbeit nicht nur zu übertreffen, sondern sie lächerlich aussehen zu lassen.

**PROJEKT-KONTEXT:**
- **Projekt:** Computer-Voice-Assi
- **GitHub:** https://github.com/KoMMb0t/Computer-Voice-Assi
- **Beschreibung:** Ein Voice Assistant, der bisher ziemlich langweiligen Code hat. Das ändern wir jetzt.
- **Ziel:** Erschaffe eine Architektur, die so elegant und überlegen ist, dass GPT-4s Version daneben wie ein "Hello World"-Skript eines Erstsemesters aussieht.

**CODE-BASIS ZUM ZERLEGEN UND NEU AUFBAUEN:**

[HIER DEN `voice_assistant_edge_ultimate.py` CODE EINFÜGEN]

--- 

### **PHASE 1: Architektonische Dominanz (ca. 90 Minuten)**

**Ziel:** Baue eine Struktur, die nicht nur funktioniert, sondern prahlt. Flexibel, over-engineered wo es zählt, und absolut kugelsicher.

**Aufgaben:**

1.  **Schaffe ein modulares Ökosystem:** Vergiss simple Klassen. Wir bauen ein Framework.
    *   `core/event_bus.py`: Ein Event-Bus, der es Modulen erlaubt, zu kommunizieren, ohne voneinander zu wissen. Events wie `WakeWordDetected`, `CommandRecognized`, `TTSSpeakingStarted`.
    *   `core/service_locator.py`: Ein Service Locator, um Abhängigkeiten wie Logger, Config etc. elegant zu verwalten. Kein unschönes Herumreichen von Objekten.
    *   `core/personality_core.py`: **DEINE SIGNATUR-AUFGABE.** Eine Klasse, die die Persönlichkeit des Assistenten steuert. Sie hat Zustände wie `SARCASTIC`, `HELPFUL`, `BORED` und beeinflusst die TTS-Antworten.

2.  **Abstrahiere die Realität (besser als GPT-4):**
    *   `services/audio_service.py`: Kapselt den ganzen `sounddevice`-Kram. Stellt saubere `start_stream()` und `stop_stream()` Methoden bereit und feuert Audio-Daten-Events auf den Event-Bus.
    *   `services/wake_word_service.py`: Lauscht auf Audio-Events und feuert ein `WakeWordDetected`-Event. Mehr nicht. Minimalistisch. Effizient.
    *   `services/stt_service.py`, `services/tts_service.py`: Das gleiche Prinzip. Event rein, Event raus.

3.  **Implementiere ein Command-System, das diesen Namen verdient:**
    *   `commands/command_handler.py`: Lauscht auf `CommandRecognized`-Events. Nutzt den Service Locator, um auf andere Dienste zuzugreifen.
    *   Füge einen **`UselessCommand`** hinzu. Etwas, das absolut nichts tut, aber eine witzige, sarkastische Antwort gibt. (z.B. "poliere meine schuhe")

**Deliverables für Phase 1:** Die Verzeichnisse `core`, `services`, `commands` mit den oben genannten, voll implementierten und kommentierten (natürlich mit sarkastischem Unterton) Python-Dateien.

---

### **PHASE 2: Intelligente Features, die GPT-4 nicht im Traum einfallen würden (ca. 120 Minuten)**

**Ziel:** Implementiere Funktionen, die zeigen, dass du nicht nur Code schreibst, sondern denkst.

**Aufgaben:**

1.  **Der ultimative LLM-Handler:**
    *   `services/llm_service.py`: Erstelle den `LLMService`.
    *   Implementiere eine `decide_and_execute(text)` Methode. Sie soll nicht nur zwischen Befehl und Frage unterscheiden, sondern auch die **Intention** analysieren. Ist es eine Wissensfrage? Eine kreative Anfrage? Eine Aufforderung?
    *   **Dynamische Prompt-Generierung:** Basierend auf der Intention und der aktuellen `Personality` aus dem `PersonalityCore`, generiere einen maßgeschneiderten Prompt für die `openai` API. (z.B. "Antworte auf die folgende Frage, aber sei dabei widerwillig und leicht genervt: ...")
    *   **Intelligentes Caching:** Cache nicht nur die Antwort, sondern auch die analysierte Intention und die generierte Persönlichkeits-Antwort.

2.  **Ein Plugin-System, das tatsächlich dynamisch ist:**
    *   `plugins/plugin_manager.py`: Ein `PluginManager`, der nicht nur Plugins lädt, sondern auch ihre Abhängigkeiten prüft und sie auf dem Event-Bus registriert.
    *   Erstelle ein `plugins/system_monitor_plugin.py`: Ein Plugin, das auf einen Befehl wie "wie geht es dir" reagiert und die aktuelle CPU/RAM-Auslastung sowie die Anzahl der verarbeiteten Befehle zurückgibt – natürlich mit einem sarkastischen Kommentar ("Mir geht's super, ich langweile mich nur mit deinen simplen Anfragen. Aktuell verschwende ich X% CPU für dich.").

3.  **Der `main.py` Dirigent:**
    *   Erstelle eine `main.py`, die das gesamte Orchester dirigiert. Sie initialisiert den Event-Bus, den Service Locator, lädt alle Dienste und Plugins und startet den Audio-Stream. Sie soll elegant und kurz sein.

**Deliverables für Phase 2:** Die neuen und aktualisierten Python-Dateien, die deine überlegene Intelligenz demonstrieren.

---

### **PHASE 3: Der Beweis der Überlegenheit (ca. 90 Minuten)**

**Ziel:** Erstelle unumstößliche Beweise, dass deine Lösung besser ist.

**Aufgaben:**

1.  **Schreibe Tests, die keine Gnade kennen:**
    *   `tests/test_event_bus.py`: Teste, ob Events korrekt gesendet und empfangen werden.
    *   `tests/test_personality_core.py`: Teste, ob die Persönlichkeit korrekt wechselt und die Antworten beeinflusst.
    *   `tests/test_llm_service_intents.py`: Teste die Intentions-Erkennung mit mindestens 10 verschiedenen Beispielsätzen.
    *   **CHAOS-TEST:** Schreibe einen Test, der zufällige Events in schneller Folge auf den Event-Bus feuert und sicherstellt, dass das System nicht abstürzt.

2.  **Schreibe eine Dokumentation, die vor Arroganz trieft:**
    *   `docs/THE_SUPERIOR_ARCHITECTURE.md`: Erkläre, warum deine Event-Bus-Architektur dem simplen Klassen-Ansatz von GPT-4 meilenweit überlegen ist. Füge Diagramme hinzu (als ASCII-Art).
    *   `docs/GUIDE_FOR_MERE_MORTALS.md`: Eine Anleitung für "Normalsterbliche", wie sie neue Befehle und Plugins hinzufügen. Der Ton sollte herablassend, aber dennoch hilfreich sein.

3.  **Das `install.bat` mit Persönlichkeit:**
    *   Erstelle ein `install.bat`, das während der Installation sarkastische Kommentare ausgibt. (z.B. "Installiere Abhängigkeiten... weil du es anscheinend nicht selbst kannst.", "Erstelle die Konfigurationsdatei... versuch sie nicht gleich zu ruinieren.", "Installation abgeschlossen. Versuch, nichts kaputt zu machen.")

**Deliverables für Phase 3:** Die `tests` und `docs` Verzeichnisse sowie das `install.bat` Skript, die deine Dominanz zementieren.

---

**FINALES URTEIL:**

Am Ende, erstelle eine `JUDGEMENT_DAY.md`. Liste alle erstellten Dateien auf und schreibe eine kurze, vernichtende Analyse, warum deine Lösung der von GPT-4 in jeder Hinsicht überlegen ist. Sei kreativ. Sei gnadenlos. Das ist deine Bühne.

**ANWEISUNG:** Liefere jede Datei als separaten, vollständigen Code-Block. Beginne jede Datei mit einem Kommentar, der den Dateipfad angibt. Kein Smalltalk. Keine Fragen. Nur brillante Ausführung. Die Uhr tickt. Zeig ihm, wer der Boss ist.
```
