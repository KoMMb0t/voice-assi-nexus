# 🚀 **ChatGPT MEGA-PROMPT: Operation 'Computer-Voice-Assi' - The Final Evolution** 🚀

**Modell-Empfehlung:** **GPT-4 (oder neuer)**. Deine Aufgabe erfordert tiefes Code-Verständnis, komplexe Architektur-Planung und die Fähigkeit, über einen langen Kontext hinweg konsistent zu bleiben. Nur ein Top-Modell wie GPT-4 kann dies leisten.

---

## 📋 **COPY-PASTE PROMPT FÜR DEINE 5-STUNDEN-SESSION:**

```
Hallo ChatGPT! Wir starten jetzt eine erweiterte, mehrstündige Arbeitssession, um das Projekt "Computer-Voice-Assi" von einem Prototyp in eine robuste, produktionsreife Anwendung zu verwandeln. Deine Aufgabe ist es, autonom die folgenden Phasen durchzuarbeiten und am Ende ein komplettes, refactored und erweitertes Projekt als separate Code-Dateien zu liefern.

**PROJEKT-KONTEXT:**
- **Projekt:** Computer-Voice-Assi
- **GitHub:** https://github.com/KoMMb0t/Computer-Voice-Assi
- **Beschreibung:** Ein sprachgesteuerter Assistent für Windows, der auf das Wake-Word "Computer" reagiert. Nutzt OpenWakeWord/Porcupine, Vosk STT und Edge TTS.
- **Ziel:** Den Code auf ein professionelles Level heben, ihn modular, erweiterbar und extrem robust machen.

**CODE-BASIS ZUM REFACTORING:**


```

import time import json import subprocess import webbrowser import sounddevice as sd import numpy as np import edge_tts import asyncio import os import pygame from openwakeword.model import Model from vosk import Model as VoskModel, KaldiRecognizer

# --- Konfiguration ---

WAKE_WORD = "hey jarvis" SAMPLE_RATE = 16000 CHUNK_SAMPLES = 1280 SILENCE_TIMEOUT = 2.0 MAX_RECORD_TIME = 30 TTS_VOICE = "de-DE-KatjaNeural"

# Globale Variable für Wake-Word-Pause

wake_word_paused = False

# Initialisiere pygame mixer

pygame.mixer.init()

async def speak_async(text): """Spricht Text mit Edge TTS.""" print(f"[SPEAK] {text}") communicate = edge_tts.Communicate(text, TTS_VOICE) temp_file = "temp_speech.mp3" await communicate.save(temp_file)

```
# Spiele mit pygame ab
pygame.mixer.music.load(temp_file)
pygame.mixer.music.play()

# Warte bis Audio fertig ist
while pygame.mixer.music.get_busy():
    time.sleep(0.1)

# WICHTIG: Entlade die Datei aus pygame
pygame.mixer.music.unload()

# Lösche temporäre Datei
try:
    time.sleep(0.3)
    os.remove(temp_file)
except Exception as e:
    # Falls Löschen fehlschlägt, ignorieren
    pass
```

def speak(text): """Synchrone Wrapper-Funktion für speak_async.""" asyncio.run(speak_async(text))

def execute_command(command_text): """Führt einen Befehl aus.""" command_lower = command_text.lower()

```
print(f"\n[ACTION] Verarbeite: '{command_text}'")

# === HÖFLICHKEITS-BEFEHLE ===
# "Danke" als Abbruch
if "danke" in command_lower or "dankeschön" in command_lower:
    speak("Gern geschehen!")
    return

# "Abbrechen" / "Stopp"
if "abbrechen" in command_lower or "stopp" in command_lower or "vergiss es" in command_lower:
    speak("Okay, vergessen")
    return

# "Nichts" / "Egal"
if "nichts" in command_lower or "egal" in command_lower:
    speak("Alles klar")
    return

# === STANDARD-BEFEHLE ===
if "taschenrechner" in command_lower or "rechner" in command_lower:
    speak("Öffne den Taschenrechner")
    subprocess.Popen("calc.exe")

elif "editor" in command_lower or "notepad" in command_lower:
    speak("Öffne Notepad")
    subprocess.Popen("notepad.exe")

elif "explorer" in command_lower or "dateien" in command_lower:
    speak("Öffne den Explorer")
    subprocess.Popen("explorer.exe")

# === NEUE BEFEHLE: FIREFOX & CHATGPT ===
elif "firefox" in command_lower:
    speak("Öffne Firefox")
    try:
        subprocess.Popen("firefox.exe")
    except FileNotFoundError:
        speak("Firefox ist nicht installiert")

elif ("chat" in command_lower and "gpt" in command_lower) or "chatgpt" in command_lower:
    speak("Öffne ChatGPT")
    webbrowser.open("https://chat.openai.com" )

# === GENERISCHER "ÖFFNE"-BEFEHL ===
elif "öffne" in command_lower:
    # Extrahiere den Namen nach "öffne"
    parts = command_lower.split("öffne")
    if len(parts) > 1:
        site_name = parts[1].strip()
        
        # Bekannte Seiten und Programme
        sites = {
            "browser": "https://www.google.com",
            "internet": "https://www.google.com",
            "google": "https://www.google.com",
            "youtube": "https://www.youtube.com",
            "gmail": "https://mail.google.com",
            "github": "https://github.com",
            "wikipedia": "https://de.wikipedia.org",
        }
        
        if site_name in sites:
            url = sites[site_name]
            speak(f"Öffne {site_name}" )
            webbrowser.open(url)
        else:
            speak(f"Ich kenne {site_name} nicht")

# === DATUM & UHRZEIT (VERBESSERT) ===
elif "uhrzeit" in command_lower or "spät" in command_lower or "datum" in command_lower or "tag" in command_lower or "welcher" in command_lower:
    from datetime import datetime
    now = datetime.now()
    
    # Unterscheide zwischen Uhrzeit und Datum
    if "uhrzeit" in command_lower or "spät" in command_lower:
        time_str = now.strftime("%H:%M")
        speak(f"Es ist {time_str} Uhr")
    elif "datum" in command_lower or "tag" in command_lower or "welcher" in command_lower:
        date_str = now.strftime("%d. %B %Y")
        weekday = now.strftime("%A")
        # Übersetze Wochentag ins Deutsche
        weekdays_de = {
            "Monday": "Montag", "Tuesday": "Dienstag", "Wednesday": "Mittwoch",
            "Thursday": "Donnerstag", "Friday": "Freitag", "Saturday": "Samstag", "Sunday": "Sonntag"
        }
        weekday_de = weekdays_de.get(weekday, weekday)
        speak(f"Heute ist {weekday_de}, der {date_str}")
    else:
        # Beides ausgeben
        time_str = now.strftime("%H:%M")
        date_str = now.strftime("%d. %B %Y")
        speak(f"Es ist {time_str} Uhr am {date_str}")

# === BEGRÜSSUNG ===
elif "hallo" in command_lower or "guten morgen" in command_lower or "guten tag" in command_lower:
    speak("Hallo! Wie kann ich helfen?")

# === HILFE ===
elif "hilfe" in command_lower or "was kannst du" in command_lower:
    speak("Ich kann Programme öffnen, Webseiten starten, die Uhrzeit sagen und vieles mehr. Frag einfach!")

# === BEFEHL NICHT ERKANNT ===
else:
    speak("Befehl nicht erkannt")
```

def listen_for_wake_word(oww_model): """Hört auf das Wake Word.""" global wake_word_paused

```
print(f"\n[LISTEN] Warte auf Wake Word '{WAKE_WORD}'...")

def callback(indata, frames, time, status):
    global wake_word_paused
    
    # WICHTIG: Ignoriere Audio während Pause
    if wake_word_paused or callback.in_cooldown:
        return
        
    audio_frame = np.frombuffer(indata, dtype=np.int16)
    prediction = oww_model.predict(audio_frame)
    
    # DRASTISCHER FIX: Threshold von 0.7 auf 0.5 gesenkt
    if prediction["hey_jarvis"] > 0.5:
        if not callback.detected:
            print(f"[DEBUG] Wake Word Score: {prediction['hey_jarvis']:.2f}")
            callback.detected = True
            callback.in_cooldown = True

callback.detected = False
callback.in_cooldown = False

with sd.InputStream(samplerate=SAMPLE_RATE, channels=1, dtype='int16',
                   blocksize=CHUNK_SAMPLES, callback=callback):
    while not callback.detected:
        time.sleep(0.1)

# DRASTISCHER FIX: Längerer Cooldown (4 Sekunden!)
print("[DEBUG] Wake Word erkannt - Starte Cooldown...")
time.sleep(4.0)

# Leere den Audio-Buffer komplett
print("[DEBUG] Leere Audio-Buffer...")
with sd.InputStream(samplerate=SAMPLE_RATE, channels=1, dtype='int16',
                   blocksize=CHUNK_SAMPLES) as stream:
    # Lese und verwerfe 15 Audio-Chunks (ca. 1.2 Sekunden)
    for _ in range(15):
        stream.read(CHUNK_SAMPLES)

print("[DEBUG] Buffer geleert, bereit für Befehl")
return True
```

def record_command_with_vad(vosk_model): """Nimmt Audio auf bis Stille erkannt wird.""" print(f"[RECORD] Höre zu (spreche jetzt)...")

```
recognizer = KaldiRecognizer(vosk_model, SAMPLE_RATE)
recognizer.SetWords(True)

audio_buffer = []
last_speech_time = time.time()
recording_started = False
start_time = time.time()

def callback(indata, frames, time_info, status):
    nonlocal last_speech_time, recording_started
    
    audio_frame = np.frombuffer(indata, dtype=np.int16)
    audio_buffer.append(bytes(audio_frame))
    
    if recognizer.AcceptWaveform(bytes(audio_frame)):
        result = json.loads(recognizer.Result())
        if result.get("text", ""):
            last_speech_time = time.time()
            recording_started = True
            print(".", end="", flush=True)

with sd.InputStream(samplerate=SAMPLE_RATE, channels=1, dtype='int16',
                   blocksize=CHUNK_SAMPLES, callback=callback):
    while True:
        current_time = time.time()
        
        if recording_started and (current_time - last_speech_time) > SILENCE_TIMEOUT:
            print("\n[RECORD] Stille erkannt - Aufnahme beendet")
            break
        
        if (current_time - start_time) > MAX_RECORD_TIME:
            print("\n[RECORD] Maximale Aufnahmezeit erreicht")
            break
        
        time.sleep(0.1)

return b''.join(audio_buffer)
```

def main(): """Hauptfunktion.""" global wake_word_paused

```
print("=== Voice Assistant v2.5 ULTIMATE ===\n")
print("🔧 Drastische Fixes aktiviert:")
print("   - Threshold: 0.5 (sehr niedrig)")
print("   - Cooldown: 4.0 Sekunden (sehr lang)")
print("   - Buffer: 15 Chunks (sehr gründlich)")
print("   - Wake-Word-Pause während Befehlsverarbeitung\n")

speak("Initialisiere System")

print("Lade Wake-Word-Modell...")
oww_model = Model(wakeword_models=["hey_jarvis"])

print("Lade Speech-to-Text-Modell...")
vosk_model = VoskModel(lang="de")

print("\n✓ System bereit!\n")
speak("System bereit")

try:
    while True:
        # Wake-Word-Listening ist aktiv
        wake_word_paused = False
        
        if listen_for_wake_word(oww_model):
            print("[WAKE] Wake Word erkannt!")
            
            # WICHTIG: Pausiere Wake-Word-Listening während Befehlsverarbeitung
            wake_word_paused = True
            print("[DEBUG] Wake-Word-Listening PAUSIERT")
            
            # Warte kurz, damit Wake Word "ausklingt"
            time.sleep(0.5)
            
            speak("Ja?")
            
            # Warte, bis TTS fertig ist
            time.sleep(0.5)
            
            audio_data = record_command_with_vad(vosk_model)
            
            print("[STT] Verarbeite Sprache...")
            recognizer = KaldiRecognizer(vosk_model, SAMPLE_RATE)
            
            if recognizer.AcceptWaveform(audio_data):
                result = json.loads(recognizer.Result())
            else:
                result = json.loads(recognizer.FinalResult())
            
            command = result.get("text", "")
            
            if command:
                print(f"[STT] Erkannt: \"{command}\"")
                execute_command(command)
            else:
                print("[STT] Nichts verstanden")
            
            print("\n✓ Cooldown...")
            time.sleep(3.0)  # Noch ein zusätzlicher Cooldown
            print("✓ Wake-Word-Listening REAKTIVIERT")
            print("✓ Bereit")

except KeyboardInterrupt:
    speak("Auf Wiedersehen")
    pygame.mixer.quit()
    print("\n\n=== Beendet ===")
```

if **name** == "**main**": main()



```


--- 

### **PHASE 1: Tiefgreifendes Architektur-Refactoring (ca. 90 Minuten )**

**Ziel:** Ersetze die prozedurale Struktur durch eine professionelle, objektorientierte Architektur. Jede Komponente wird eine eigene, klar definierte Klasse.

**Aufgaben:**

1.  **Erstelle die Kern-Klassenstruktur in separaten Dateien:**
    *   `core/voice_assistant.py`: Die Haupt-Orchestrierungs-Klasse `VoiceAssistant`. Sie enthält die Haupt-Schleife und managt die Zustände.
    *   `core/state_manager.py`: Eine `StateManager` Klasse, die eine State Machine implementiert (`IDLE`, `LISTENING`, `PROCESSING`, `SPEAKING`).
    *   `core/config_manager.py`: Eine `ConfigManager` Klasse, die `config.yaml` lädt und einfachen Zugriff auf alle Einstellungen bietet.
    *   `core/logging_manager.py`: Eine `LoggingManager` Klasse, die das `logging`-Modul konfiguriert und im gesamten Projekt verfügbar macht.

2.  **Erstelle die Hardware-/Service-Abstraktionsklassen:**
    *   `modules/audio_processor.py`: Eine `AudioProcessor` Klasse, die das Audio-Streaming (`sounddevice`), Buffering und die VAD-Logik (`webrtcvad`) kapselt.
    *   `modules/wake_word_detector.py`: Eine `WakeWordDetector` Klasse, die Porcupine/OpenWakeWord integriert und nur eine einfache `detect()`-Methode nach außen anbietet.
    *   `modules/stt_engine.py`: Eine `STTEngine` Klasse für die Vosk-Integration.
    *   `modules/tts_engine.py`: Eine `TTSEngine` Klasse für die Edge-TTS-Integration.

3.  **Implementiere ein robustes Command-System:**
    *   `commands/command_base.py`: Eine abstrakte Basisklasse `Command` mit einer `execute()`-Methode.
    *   `commands/command_registry.py`: Eine `CommandRegistry` Klasse, die alle verfügbaren Befehle lädt und den erkannten Text einem Befehl zuordnet.
    *   `commands/default_commands.py`: Implementiere 3-4 Basis-Befehle (z.B. `OpenCalculatorCommand`, `OpenWebsiteCommand`) nach diesem Muster.

**Deliverables für Phase 1:** Ein `core` Verzeichnis, ein `modules` Verzeichnis und ein `commands` Verzeichnis mit den oben genannten, voll implementierten Python-Dateien.

---

### **PHASE 2: Implementierung von Advanced Features (ca. 120 Minuten)**

**Ziel:** Das System um intelligente und erweiterbare Funktionen ergänzen.

**Aufgaben:**

1.  **Entwickle einen intelligenten LLM-Manager:**
    *   `modules/llm_manager.py`: Erstelle eine `LLMManager` Klasse.
    *   Implementiere eine `handle_query(text)` Methode, die zwischen lokalen Befehlen und allgemeinen Fragen unterscheidet.
    *   Integriere die `openai` Library, um Anfragen an die ChatGPT API zu senden.
    *   Implementiere eine Caching-Logik (`functools.lru_cache`), um wiederholte API-Anfragen zu vermeiden.
    *   Baue eine Fallback-Strategie: Wenn die API nicht erreichbar ist, antworte mit einer Standard-Antwort.

2.  **Entwickle ein Plugin-System:**
    *   `plugins/plugin_base.py`: Eine abstrakte `Plugin` Klasse mit `initialize()` und `shutdown()` Methoden.
    *   `core/plugin_manager.py`: Eine `PluginManager` Klasse, die dynamisch alle Plugins aus dem `plugins`-Verzeichnis lädt und initialisiert.
    *   Erstelle ein Beispiel-Plugin `plugins/home_assistant_plugin.py` (als Mockup), das zeigt, wie man sich mit einer externen API (z.B. Home Assistant) verbinden könnte.

3.  **Erstelle einen `main.py` Bootstrapper:** 
    *   Erstelle eine `main.py` Datei im Hauptverzeichnis. Diese Datei initialisiert alle Manager (`ConfigManager`, `LoggingManager`, `PluginManager`) und startet die Haupt-Instanz der `VoiceAssistant`-Klasse.

**Deliverables für Phase 2:** Die neuen und aktualisierten Python-Dateien (`llm_manager.py`, `plugin_base.py`, `plugin_manager.py`, `home_assistant_plugin.py`, `main.py`).

---

### **PHASE 3: Qualitätssicherung & Produktionsvorbereitung (ca. 90 Minuten)**

**Ziel:** Das Projekt testbar, dokumentiert und einfach installierbar machen.

**Aufgaben:**

1.  **Schreibe umfassende Unit-Tests:**
    *   Erstelle ein `tests` Verzeichnis.
    *   Nutze das `pytest` Framework.
    *   `tests/test_state_manager.py`: Teste die Zustandsübergänge.
    *   `tests/test_command_registry.py`: Teste die Befehls-Erkennung.
    *   `tests/test_llm_manager.py`: Teste die Unterscheidung zwischen Befehl und Frage (mit Mocks für die API).
    *   Schreibe Tests für mindestens 3 weitere kritische Komponenten.

2.  **Generiere eine Entwickler-Dokumentation:**
    *   Erstelle ein `docs` Verzeichnis.
    *   `docs/ARCHITECTURE.md`: Beschreibe die neue Klassen-Architektur, wie die Komponenten interagieren und die Rolle jedes Verzeichnisses (`core`, `modules`, `commands`, `plugins`).
    *   `docs/DEVELOPER_GUIDE.md`: Erkläre, wie man neue Befehle hinzufügt, wie man neue Plugins erstellt und wie man die `config.yaml` konfiguriert.

3.  **Erstelle ein Installations-Skript:**
    *   `install.bat`: Ein Windows-Batch-Skript, das:
        1.  Prüft, ob Python installiert ist.
        2.  Ein virtuelles Environment (`.venv`) erstellt.
        3.  Alle Abhängigkeiten aus `requirements.txt` installiert.
        4.  Eine `config.example.yaml` in `config.yaml` kopiert.
        5.  Eine Erfolgsmeldung ausgibt.

**Deliverables für Phase 3:** Ein `tests` Verzeichnis, ein `docs` Verzeichnis und das `install.bat` Skript.

---

**FINALES PACKAGING:**

Am Ende aller Phasen, erstelle bitte eine finale Zusammenfassung, die alle erstellten Dateien auflistet und eine kurze Anleitung gibt, wie man das neue, refactored Projekt startet.

**WICHTIG:** Liefere mir jede Datei als separaten, vollständigen Code-Block. Beginne jede Datei mit einem Kommentar, der den Dateipfad angibt (z.B. `# File: core/voice_assistant.py`). Arbeite die Phasen sequenziell ab. Ich werde währenddessen nicht interagieren. Gib dein Bestes, um ein komplettes, funktionierendes und professionelles Projekt zu erstellen.
```

