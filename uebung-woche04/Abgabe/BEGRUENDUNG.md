Für das Taskboard-Image wurde bewusst ein schlankes und sicheres Docker-Setup verwendet. Als Basis dient `python:3.12-slim`, wodurch im Vergleich zu einem vollständigen Python-Image weniger zusätzliche Pakete und damit weniger Speicherbedarf und potenzielle Angriffsfläche vorhanden sind.

Das Dockerfile verwendet einen Multi-Stage-Build. In der Builder-Stufe werden die benötigten Abhängigkeiten installiert, während im finalen Image nur die für den Betrieb notwendigen Dateien übernommen werden. Dadurch bleiben Build-Werkzeuge und temporäre Dateien ausserhalb des produktiven Images.

Zusätzlich werden die Requirements vor dem Anwendungscode kopiert. Dadurch kann Docker den Layer-Cache besser verwenden und muss die Abhängigkeiten nicht bei jeder Änderung am Python-Code erneut installieren.

Die `.dockerignore` verhindert, dass unnötige Dateien wie `.git`, `.env`, `tests` oder `__pycache__` in den Build-Kontext und später in das Image gelangen.

Aus Sicherheitsgründen läuft die Anwendung ausserdem unter einem unprivilegierten Benutzer und nicht als `root`. Dadurch werden die Auswirkungen eines möglichen Angriffs innerhalb des Containers reduziert.

Der Grössenvergleich zeigt den Effekt der Optimierungen: Das optimierte Image `taskboard:local` ist **[X MB]** gross, während `taskboard:naiv` **[Y MB]** benötigt.