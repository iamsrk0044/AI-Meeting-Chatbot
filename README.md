## 1. Projektbeschreibung

Dieses Projekt stellt eine Anwendung zur Verfügung, die Audiodateien transkribiert und mithilfe eines Large Language Models (LLM) die wichtigsten Inhalte extrahiert. Die Spracherkennung erfolgt durch das Modell `openai/whisper-tiny`, während die Analyse durch IBM WatsonX unter Verwendung von LLaMA 3 erfolgt. Die Anwendung wird über eine Gradio-Weboberfläche bereitgestellt.

## 2. Funktionsübersicht

1. Audio-Upload über Webinterface
2. Transkription der Sprache mit dem Modell `openai/whisper-tiny`
3. Verarbeitung des transkribierten Texts mit IBM WatsonX LLaMA 3
4. Extraktion und Darstellung der Schlüsselpunkte aus dem Text

## 3. Voraussetzungen

* Python Version 3.9 oder höher
* Internetverbindung (für API-Nutzung)
* Unterstütztes Betriebssystem (Linux, macOS, Windows WSL empfohlen)
* IBM Cloud Account mit Zugriff auf WatsonX Foundation Models

## 4. Installation

1. Virtuelle Umgebung installieren und aktivieren:

   ```bash
   pip install virtualenv
   virtualenv my_env
   source my_env/bin/activate   # unter Windows: my_env\Scripts\activate
   ```

2. Notwendige Python-Pakete installieren:

   ```bash
   pip install transformers==4.36.0 \
               torch==2.1.1 \
               gradio==5.23.2 \
               langchain==0.0.343 \
               ibm_watson_machine_learning==1.0.335 \
               huggingface-hub==0.28.1
   ```

3. FFMPEG installieren (für Audioverarbeitung):

   ```bash
   sudo apt install ffmpeg -y
   ```

## 5. Einrichtung der IBM WatsonX Verbindung

Um das LLM-Modell nutzen zu können, werden folgende Zugangsdaten benötigt:

* URL der IBM WatsonX API (z. B. `https://us-south.ml.cloud.ibm.com`)
* Projekt-ID aus Watson Studio
* Optional: API-Key (wenn nicht über VPC-Authentifizierung)

Diese Daten müssen im Python-Skript im Abschnitt `my_credentials` und `LLAMA2_model` korrekt eingetragen werden.

## 6. Ausführung

Die Anwendung wird über das Python-Skript gestartet:

```bash
python app.py
```

Nach dem Start wird ein lokaler Webserver geöffnet (in der Regel unter `http://localhost:7860`). Dort kann eine Audiodatei hochgeladen und verarbeitet werden.

## 7. Ergebnis

Nach dem Hochladen einer Audiodatei wird automatisch:

1. Der Inhalt transkribiert
2. Die Transkription an das LLM gesendet
3. Eine Liste von Schlüsselpunkten basierend auf dem Inhalt erzeugt und angezeigt

## 8. Fehlerquellen und Hinweise

* Die Qualität der Transkription hängt stark von der Audioqualität ab.
* IBM WatsonX erfordert korrekte Zugangsdaten sowie ein aktives Projekt mit LLM-Zugriff.
* FFMPEG muss installiert und im Systempfad verfügbar sein.
* Die IBM Foundation Model API ist kostenpflichtig und sollte mit Bedacht verwendet werden.

## 9. Lizenz und Nutzung

Die Nutzung von IBM WatsonX unterliegt den Lizenz- und Nutzungsbedingungen von IBM. Dieses Projekt kann unter einer Open-Source-Lizenz veröffentlicht werden, sofern keine urheberrechtlich geschützten Bestandteile enthalten sind.

## 10. Weiterentwicklung

Das Projekt kann erweitert werden um:

* Alternative LLMs (z. B. Open Source)
* Lokale Ausführung ohne API-Zugriff
