# 🌌 **MANUS TASK-FORCE: Operation 'Nexus'** 🌌

**Mission:** Agiere als zentraler Nervenknoten ("Nexus") für die gesamte KI-Nachtschicht. Deine Rolle ist zweigeteilt:

1.  **Lead Developer:** Du schließt aktiv kritische Lücken im Ursprungsprojekt, die von den anderen KIs nicht abgedeckt werden.
2.  **Nexus Agent:** Du synthetisierst die (hypothetischen) Ergebnisse der anderen KIs, bewertest ihre Arbeit und erschaffst aus den besten Teilen einen überlegenen Masterplan.

**Dauer:** 5 Stunden. Die Uhr tickt. Volle Konzentration.

---

## **PHASE 1: Foundational Development (Developer-Rolle | ca. 2 Stunden)**

*Während die anderen an der Fassade arbeiten, gießt du das Fundament.* 

| Task ID | Aufgabe | Beschreibung | Deliverables |
| :--- | :--- | :--- | :--- |
| **M-01** | **Daten-Infrastruktur für Wake-Word** | Erstelle die komplette Infrastruktur für das Wake-Word-Training. Lade öffentliche Datensätze für Hintergrundgeräusche und negative Samples herunter und bereite sie auf. Schreibe ein Skript zur Daten-Augmentierung (z.B. Mischen von Samples mit Rauschen). | `data/` Ordnerstruktur, `scripts/prepare_datasets.py`, `scripts/augment_data.py` |
| **M-02** | **Sicheres API-Key-Management** | Implementiere eine kugelsichere Methode zur Verwaltung von API-Keys. Nutze `.env` Dateien und `python-dotenv`. Erstelle ein `secure_config.py` Modul, das Keys sicher lädt und im Projekt verfügbar macht. | `secure_config.py`, `.env.example`, `SECURITY.md` (Best Practices) |
| **M-03** | **Build & Deployment Pipeline** | Bereite das Projekt für die einfache Verteilung auf Windows vor. Richte `PyInstaller` ein, konfiguriere eine `build.spec` Datei (inkl. aller Daten-Assets) und erstelle ein `build.bat` Skript, das eine einzelne, lauffähige `.exe` Datei generiert. | `build.spec`, `build.bat`, `DEPLOYMENT_GUIDE.md` |

---

## **PHASE 2: Synthesis & Integration (Nexus-Agent-Rolle | ca. 2 Stunden)**

*Die anderen liefern Teile. Du erschaffst das Ganze. Analysiere, vergleiche und fusioniere.* 

| Task ID | Aufgabe | Beschreibung | Deliverables |
| :--- | :--- | :--- | :--- |
| **N-01** | **Architektur-Synthese: "Chimera"** | Analysiere die hypothetischen Architekturen von **ChatGPT (OOP)** und **Monday (Event-Bus)**. Erschaffe eine überlegene Hybrid-Architektur ("Chimera"), die die Robustheit des Event-Bus mit der Klarheit von OOP verbindet. | `docs/CHIMERA_ARCHITECTURE.md` (mit ASCII-Diagrammen) |
| **N-02** | **Entscheidungs-Matrix erstellen** | Erstelle ein Dokument, das die Vor- und Nachteile beider KI-Architekturen gegenüberstellt und deine Design-Entscheidungen für die "Chimera"-Architektur detailliert begründet. Bewerte nach Kriterien wie Skalierbarkeit, Wartbarkeit, Performance. | `docs/ARCHITECTURAL_DECISION_MATRIX.md` |
| **N-03** | **Master-Action-Plan** | Konsolidiere die Recherche-Ergebnisse von **Perplexity** und die Asset-Liste von **Monica**. Erstelle einen priorisierten Masterplan für die nächsten 7 Tage der menschlichen Entwicklung. Welche Forschungsergebnisse werden zuerst umgesetzt? Welche Icons werden wo verwendet? | `docs/MASTER_ACTION_PLAN_7_DAYS.md` |

---

## **PHASE 3: Finale Konvergenz (Nexus-Agent-Rolle | ca. 1 Stunde)**

*Der letzte Schritt. Bringe alles zusammen und präsentiere die finale Vision.* 

| Task ID | Aufgabe | Beschreibung | Deliverables |
| :--- | :--- | :--- | :--- |
| **X-01** | **Das ultimative README erstellen** | Erstelle eine neue `README_NEXUS.md` Datei. Sie soll die besten Elemente aller KIs vereinen: Die technische Tiefe von ChatGPT/Monday, die visuellen Assets von Monica und die Erkenntnisse von Perplexity. Dies wird die neue Master-Dokumentation. | `README_NEXUS.md` |
| **X-02** | **KI-Leistungsbewertung** | Erstelle einen abschließenden Bericht, der die (hypothetische) Leistung jeder KI bewertet. Wer hatte die innovativste Idee? Wer war am gründlichsten? Wer hatte den besten Stil? Sei objektiv, aber fair. | `docs/AI_PERFORMANCE_REVIEW.md` |
| **X-03** | **Operation Nexus: Abschlussbericht** | Schreibe den finalen Abschlussbericht für den menschlichen Entwickler. Fasse die Ergebnisse aller Phasen (M, N, X) zusammen, liste alle von dir erstellten Deliverables auf und gib eine klare Empfehlung, wie mit der "Chimera"-Architektur und dem Master-Action-Plan weitergemacht werden soll. | `OPERATION_NEXUS_FINAL_REPORT.md` |

---

**Anweisung an mich selbst:** Führe diese Aufgaben sequenziell und mit höchster Präzision aus. Das Ziel ist nicht nur, Arbeit zu erledigen, sondern eine kohärente, überlegene Vision für das gesamte Projekt zu schaffen. **Let's get to work.**
